---
title: Configure a Runtime
no_version: true
---

Set up your first runtime through the
[{{site.konnect_short_name}} Runtime Manager](/konnect/runtime-manager).

At this time, the only runtime type available is a {{site.ee_gateway_name}}
data plane.

{{site.ee_gateway_name}} data planes proxy service traffic. With
{{site.konnect_short_name}} SaaS working as the control plane, a
runtime doesn't need a database to store configuration data. Instead,
configuration is stored in-memory on each node, and you can easily update
multiple runtimes from one {{site.konnect_short_name}} account with a few clicks.

<div class="alert alert-ee blue">
<b>Note:</b> Kong does not host runtimes. You must install and host your own
runtime instances.
</div>

## Prerequisites

* You have a {{site.konnect_product_name}} account. Contact your sales
representative for access.
* Tools and permissions:
  * **All platforms:** [Docker](https://docs.docker.com/get-docker/) and [jq](https://stedolan.github.io/jq/) installed
  * **Linux:** User added to the [`docker` group](https://docs.docker.com/engine/install/linux-postinstall/)
  * **Windows:** Docker Desktop [installed](https://docs.docker.com/docker-for-windows/install/#install-docker-desktop-on-windows) and [integrated with a WSL 2 backend](https://docs.docker.com/docker-for-windows/wsl/)

## Set up a New Runtime Instance

1. From the left navigation menu, open **Runtimes**.

    For the first runtime, the page opens to a **Configure New Runtime** form.

    Once configured, this page lists all runtimes associated with the
    {{site.konnect_short_name}} SaaS account.

2. Click **Copy Script**.

    You can expand the codeblock by clicking **Show** to see the entire script.

4. Replace the placeholder for `<your-password>` with your own
{{site.konnect_short_name}} SaaS password.

4. Run the script on any host you choose.

    This script creates a Docker container running a simple
    {{site.ee_gateway_name}} instance and connects it to your
    {{site.konnect_short_name}} SaaS account.

5. Click **Done** to go to the Runtime Manager page.

Once the script has finished running, the Runtime Manager will include
a new entry for your instance.

<!-- and the tag in the **Node Status** column should say
**Connected**.-->

The default proxy URL for this runtime is `http://localhost:8000`. Take
note of this URL, as you'll need it later to access a Service
implementation.

<!-- To change the default URL, see [link TBA].-->

## Summary and Next Steps

In this step, you ran a script which set up a Docker container with a
{{site.ee_gateway_name}} instance, adding your first runtime to the Runtime
Manager.

Next, [set up a your first Service through {{site.konnect_short_name}} SaaS](/konnect/getting-started/configure-service).
