---
title: Version Compatibility
---

Kong's Ingress Controller is compatible with different flavors of Kong.
The following sections detail on compatibility between versions.

## Kong

By Kong, we are here referring to the official distribution of the Open-Source
Kong Gateway.

| {{site.kic_product_name}} |          <= 0.0.4           |            0.0.5            |            0.1.x            |            0.2.x            |            0.3.x            |            0.4.x            |            0.5.x            |            0.6.x            |            0.7.x            |            0.8.x            |            0.9.x            |           0.10.x            |            1.0.x            |            1.1.x            |
|:------------------------|:---------------------------:|:---------------------------:|:---------------------------:|:---------------------------:|:---------------------------:|:---------------------------:|:---------------------------:|:---------------------------:|:---------------------------:|:---------------------------:|:---------------------------:|:---------------------------:|:---------------------------:|:---------------------------:|
| Kong 0.13.x               | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> |
| Kong 0.14.x               | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-check"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> |
| Kong 1.0.x                | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> |
| Kong 1.1.x                | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> |
| Kong 1.2.x                | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> |
| Kong 1.3.x                | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> |
| Kong 1.4.x                | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> |
| Kong 1.5.x                | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> |
| Kong 2.0.x                | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> |
| Kong 2.1.x                | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> |

## Kong-enterprise-k8s

Kong-enterprise-k8s is an official distribution by Kong, Inc. which bundles
all enterprise plugins into Open-Source Kong Gateway.

The compatibility for this distribution will largely follow that of the
Open-Source Kong Gateway compatibility (the previous section).

| {{site.kic_product_name}}   |           0.6.2+            |            0.7.x            |            0.8.x            |            0.9.x            |           0.10.x            |            1.0.x            |            1.1.x            |
|:----------------------------|:---------------------------:|:---------------------------:|:---------------------------:|:---------------------------:|:---------------------------:|:---------------------------:|:---------------------------:|
| Kong-enterprise-k8s 1.3.x.y | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> |
| Kong-enterprise-k8s 1.4.x.y | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> |
| Kong-enterprise-k8s 2.0.x.y | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> |

## Kong Enterprise

Kong Enterprise is the official enterprise distribution, which includes all
other enterprise functionality, built on top of the Open-Source Kong Gateway.

| {{site.kic_product_name}} |            0.0.5            |            0.1.x            |            0.2.x            |            0.3.x            |            0.4.x            |            0.5.x            |            0.6.x            |            0.7.x            |            0.8.x            |            0.9.x            |           0.10.x            |            1.0.x            |            1.1.x            |
|:------------------------|:---------------------------:|:---------------------------:|:---------------------------:|:---------------------------:|:---------------------------:|:---------------------------:|:---------------------------:|:---------------------------:|:---------------------------:|:---------------------------:|:---------------------------:|:---------------------------:|:---------------------------:|
| Kong Enterprise 0.32-x    | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> |
| Kong Enterprise 0.33-x    | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> |
| Kong Enterprise 0.34-x    | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> |
| Kong Enterprise 0.35-x    | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> |
| Kong Enterprise 0.36-x    | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> |
| Kong Enterprise 1.3.x     | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> |
| Kong Enterprise 1.5.x     | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> |
| Kong Enterprise 2.1.x     | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> |

## Kubernetes

| {{site.kic_product_name}} |            0.9.x            |           0.10.x            |            1.0.x            |            1.1.x            |
|:--------------------------|:---------------------------:|:---------------------------:|:---------------------------:|:---------------------------:|
| Kubernetes 1.13           | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> | <i class="fa fa-times"></i> |
| Kubernetes 1.14           | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> |
| Kubernetes 1.15           | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> |
| Kubernetes 1.16           | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> |
| Kubernetes 1.17           | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> |
| Kubernetes 1.18           | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> |
| Kubernetes 1.19           | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> |
| Kubernetes 1.20           | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> |
| Kubernetes 1.21           | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> | <i class="fa fa-check"></i> |
