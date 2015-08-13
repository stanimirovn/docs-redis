---
title: Redis for Pivotal Cloud Foundry
---

# Upgrades

This product enables a seamless upgrade experience between versions of the product that is deployed through Ops Manager.

The upgrade paths are detailed [here](http://docs.pivotal.io/redis/index.html) for each released version.

To upgrade the product:

* The Operator needs to download the latest version of the product from [Pivotal Network](https://network.pivotal.io/products/p-redis)
* Upload it to OpsManager
* Upload the stemcell (*if required*)
* Update any new mandatory configuration parameters.
* Press deploy and the rest of the process is automated.

During the upgrade deployment each Redis instance will experience a small period of downtime as each VM is updated with the new software components. This is because the Redis instances are single VMs operating in a non HA setup.

Ops Manager ensures the instances are updated with the new packages and any configuration changes are applied automatically.

Upgrading to a newer version of the product does not cause any loss of data or configuration. This is explicitly tested for during our build and test process for a new release of the product.

# Release policy

When a new version of Redis is released we aim to release a new version of the product containing this soon after.

Where there is a new version of Redis or another software component such as the stemcell released due to a critical CVE, we will release a new version of the product within 48 hours. 
