---
name: ACME
publisher: Kong Inc.
version: 0.2.13

source_url: https://github.com/Kong/kong-plugin-acme

desc: Let's Encrypt and ACMEv2 integration with Kong
description: |
  This plugin allows Kong to apply certificates from Let's Encrypt or any other ACMEv2 service and serve dynamically. Renewal is handled with a configurable threshold time.

type: plugin
categories:
  - security

kong_version_compatibility:
    community_edition:
      compatible:
        - 2.3.x
        - 2.2.x
        - 2.1.x
        - 2.0.x
    enterprise_edition:
      compatible:
        - 2.3.x
        - 2.2.x
        - 2.1.x

params:
  name: acme
  api_id: false
  service_id: false
  route_id: false
  consumer_id: false
  protocols: ['http', 'https', 'tcp', 'tls', 'grpc', 'grpcs']
  dbless_compatible: yes
  config:
    - name: account_email
      required: yes
      default:
      value_in_examples: example@example.com
      description: |
        The account identifier, can be reused in different plugin instance.
    - name: api_uri
      required: false
      default: "`https://acme-v02.api.letsencrypt.org`"
      description: |
        The ACMEv2 API endpoint to use. Users can specify the [Let's Encrypt staging environment](https://letsencrypt.org/docs/staging-environment/) (`https://acme-staging-v02.api.letsencrypt.org/directory`) for testing. Note that Kong doesn't automatically delete staging certificates: if you use same domain to test and use in production, you will need to delete those certificates manually after testing.
    - name: cert_type
      required: false
      default: "`rsa`"
      description: |
        The certificate type to create. The possible values are `"rsa"` for RSA certificate or `"ecc"` for EC certificate.
    - name: domains
      required: false
      default: "`[]`"
      description: |
        The list of domains to create certificate for. To match subdomains under `example.com`, use `*.example.com`. Regex pattern is not supported. Note this config is only used to match domains, not to specify the Common Name or Subject Alternative Name to create certifcates; each domain will have its own certificate.
    - name: fail_backoff_minutes
      required: false
      default: 5
      description: |
        Minutes to wait for each domain that fails to create a certificate. This applies to both new certificate and renewal.
    - name: renew_threshold_days
      required: false
      default: "`14`"
      description: |
        Days before expire to renew the certificate.
    - name: storage
      required: false
      default: "`shm`"
      description: |
        The backend storage type to use. The possible values are `"kong"`, `"shm"`, `"redis"`, `"consul"`, or `"vault"`. In DB-less mode, `"kong"` storage is unavailable. Note that `"shm"` storage does not persist during Kong restarts and does not work for Kong running on different machines, so consider using one of `"kong"`, `"redis"`, `"consul"`, or `"vault"` in production.
    - name: storage_config
      required: false
      default:
      description: |
        Storage configs for each backend storage. See below for its default value.
    - name: tos_accepted
      required: false
      default: "`false`"
      description: |
        If you are using Let's Encrypt, you must set this to true to agree the [Terms of Service](https://letsencrypt.org/repository/).
    - name: eab_kid
      required: false
      description: |
        External account binding (EAB) key id. You usually don't need to set this unless it is explicitly required by the CA.
    - name: eab_hmac_key
      required: false
      description: |
        External account binding (EAB) base64-encoded URL string of the HMAC key. You usually don't need to set this unless it is explicitly required by the CA.
  extra: |
    `config.storage_config` is a table for all possible storage types. By default, it is:
    ```json
        "storage_config": {
          "kong": {},
          "shm": {
            "shm_name": "kong"
          },
          "redis": {
            "auth": null,
            "port": 6379,
            "database": 0,
            "host": "127.0.0.1"
          },
           "consul": {
              "host": "127.0.0.1",
              "port": 8500,
              "token": null,
              "kv_path": "acme",
              "timeout": 2000,
              "https": false
          },
          "vault": {
              "host": "127.0.0.1",
              "port": 8200,
              "token": null,
              "kv_path": "acme",
              "timeout": 2000,
              "https": false,
              "tls_verify": true,
              "tls_server_name": null
          },
        }
    ```

    To configure a storage type other than `kong`, refer to [lua-resty-acme](https://github.com/fffonion/lua-resty-acme#storage-adapters).

    External account binding (EAB) is supported as long as `eab_kid` and `eab_hmac_key` are provided.

    The following CA provider's external account can be registered automatically, without specifying
    the `eab_kid` or `eab_hmac_key`:

    - [ZeroSSL](https://zerossl.com/)

---

### Using the Plugin

#### Configure Kong

- Kong needs to listen 80 port or proxied by a load balancer that listens for 80 port.
- `lua_ssl_trusted_certificate` needs to be set in `kong.conf` to ensure the plugin can properly
verify Let's Encrypt API. The CA-bundle file is usually `/etc/ssl/certs/ca-certificates.crt` for
Ubuntu/Debian and `/etc/ssl/certs/ca-bundle.crt` for CentOS/Fedora/RHEL.

#### Configure Plugin

Here's a sample declarative configuration with `redis` as storage:

```yaml
_format_version: "1.1"
# this section is not necessary if there's already a route that matches
# /.well-known/acme-challenge path with http protocol
services:
  - name: acme-dummy
    url: http://127.0.0.1:65535
    routes:
      - name: acme-dummy
        protocols:
          - http
        paths:
          - /.well-known/acme-challenge
plugins:
  - name: acme
    config:
      account_email: example@myexample.com
      domains:
        - "*.example.com"
        - "example.com"
      tos_accepted: true
      storage: redis
      storage_config:
        redis:
          host: redis.service
          port: 6379
```

#### Enable the Plugin

For each the domain that needs a certificate, make sure `DOMAIN/.well-known/acme-challenge`
is mapped to a Route in Kong. You can check this by sending
`curl KONG_IP/.well-known/acme-challenge/x -H "host:DOMAIN"` and getting the response `Not found`.
You can also [use the Admin API](#create-certificates) to verify the setup.
If not, add a Route and a dummy Service to catch this route.

```bash
# add a dummy service if needed
$ curl http://localhost:8001/services \
        -d name=acme-dummy \
        -d url=http://127.0.0.1:65535

# add a dummy route if needed
$ curl http://localhost:8001/routes \
        -d name=acme-dummy \
        -d paths[]=/.well-known/acme-challenge \
        -d service.name=acme-dummy

# add the plugin
$ curl http://localhost:8001/plugins \
        -d name=acme \
        -d config.account_email=yourname@yourdomain.com \
        -d config.tos_accepted=true \
        -d config.domains[]=my.secret.domains.com
```

Note by setting `tos_accepted` to *true* implies that you have read and accepted
[terms of service](https://letsencrypt.org/repository/).

**This plugin can only be configured as a global plugin.** The plugin terminates
`/.well-known/acme-challenge/` path for matching domains. To create certificates
and terminate challenges only for certain domains, refer to the
[Parameters](#parameters) section.

#### Trigger creation of certificate

Assume Kong proxy is accessible via http://mydomain.com and https://mydomain.com.

```bash
# Trigger asynchronous creation from proxy requests
# The following request returns immediately with Kong's default certificate
# Wait up to 1 minute for the background process to finish
$ curl https://mydomain.com -k

# OR create from Admin API synchronously
# User can also use this endpoint to force "renew" a certificate
$ curl http://localhost:8001/acme -d host=mydomain.com

# Furthermore, it's possible to run a sanity test on your Kong setup
# before creating any certificate
$ curl http://localhost:8001/acme -d host=mydomain.com -d test_http_challenge_flow=true

$ curl https://mydomain.com
# Now gives you a valid Let's Encrypt certicate
```

### Local testing and development

#### Run ngrok

[ngrok](https://ngrok.com) exposes a local URL to the internet. [Download ngrok](https://ngrok.com/download) and install.

*`ngrok` is only needed for local testing or development, it's **not** a requirement for the plugin itself.*

Run ngrok with

```bash
$ ./ngrok http localhost:8000
# Shows something like
# ...
# Forwarding                    http://e2e034a5.ngrok.io -> http://localhost:8000
# Forwarding                    https://e2e034a5.ngrok.io -> http://localhost:8000
# ...
# Substitute "e2e034a5.ngrok.io" with the host shows in your ngrok output
$ export NGROK_HOST=e2e034a5.ngrok.io
```

Leave the process running.

#### Configure Route and Service

```bash
$ curl http://localhost:8001/services -d name=acme-test -d url=http://mockbin.org
$ curl http://localhost:8001/routes -d service.name=acme-test -d hosts=$NGROK_HOST
```

#### Enable Plugin

```bash
$ curl localhost:8001/plugins -d name=acme \
                                -d config.account_email=test@test.com \
                                -d config.tos_accepted=true \
                                -d config.domains[]=$NGROK_HOST
```

#### Trigger creation of certificate

```bash
$ curl https://$NGROK_HOST:8443 --resolve $NGROK_HOST:8443:127.0.0.1 -vk
# Wait for several seconds
```

#### Check new certificate

```bash
$ echo q |openssl s_client -connect localhost -port 8443 -servername $NGROK_HOST 2>/dev/null |openssl x509 -text -noout
```

### Notes

- In database mode, the plugin creates an SNI and Certificate entity in Kong to
serve the certificate. If SNI or Certificate for the current request is already set
in the database, they will be overwritten.
- In DB-less mode, the plugin takes over certificate handling. If the SNI or
Certificate entity is already defined in Kong, they will be overridden by the
response.
- The plugin only supports http-01 challenge, meaning a user will need a public
IP and set up a resolvable DNS. Kong also needs to accept proxy traffic from port `80`.
Also, note that a wildcard or star (*) certificate is not supported. Each domain will have its
own certificate.
