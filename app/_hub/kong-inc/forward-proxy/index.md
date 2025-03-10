---

name: Forward Proxy Advanced
publisher: Kong Inc.
version: 1.3-x

desc: Allows Kong to connect to intermediary transparent HTTP proxies
description: |
  The Forward Proxy plugin allows Kong to connect to intermediary transparent
   HTTP proxies, instead of directly to the upstream_url, when forwarding requests
   upstream. This is useful in environments where Kong sits in an organization's
   internal network, the upstream API is available via the public internet, and
   the organization proxies all outbound traffic through a forward proxy server.

enterprise: true
type: plugin
categories:
  - traffic-control

kong_version_compatibility:
    community_edition:
      compatible:
    enterprise_edition:
      compatible:
        - 2.3.x
        - 2.2.x
        - 2.1.x
        - 1.5.x
        - 1.3-x
        - 0.36-x


params:
  name: forward-proxy
  api_id: true
  service_id: true
  route_id: true
  consumer_id: true
  config:
    - name: proxy_host
      required: true
      default:
      value_in_examples: example.com
      datatype: string
      description: |
        The hostname or IP address of the forward proxy to which to connect.
    - name: proxy_port
      required: true
      default:
      value_in_examples: 80
      datatype: string
      description: |
        The TCP port of the forward proxy to which to connect.
    - name: proxy_scheme
      required: true
      default: http
      value_in_examples: http
      datatype: string
      description: |
        The proxy scheme to use when connecting. Currently only `http` is supported.
    - name: https_verify
      required: true
      default: false
      value_in_examples: false
      datatype: boolean
      description: |
        Whether the server certificate will be verified according to the CA certificates
        specified in
        [lua_ssl_trusted_certificate](https://www.nginx.com/resources/wiki/modules/lua/#lua-ssl-trusted-certificate).
---

### Notes

The plugin attempts to transparently replace upstream connections made by Kong
 core, sending the request instead to an intermediary forward proxy. Currently
  only transparent HTTP proxies are supported; TLS connections (via `CONNECT`)
  are not yet supported.

---
