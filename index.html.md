---
title: Redis for Pivotal CF
---

This is documentation for the Redis service for Pivotal CF.

## Install via Pivotal Operations Manager

To install Redis for Pivotal CF, follow the procedure for installing Pivotal Ops Manager tiles:

1. Download the product file from [Pivotal Network](https://network.pivotal.io/).
1. Upload the product file to your Ops Manager installation.
1. Click **Add** next to the uploaded product description in the Available Products view to add this product to your staging area.
1. Click the newly added tile to review any configurable options.
1. Click **Apply Changes** to install the service.

## Dependencies
This product requires Pivotal CF:

* Elastic Runtime version 1.2 or greater
* Ops Manager version 1.3 or greater

## Provisioning and Binding via Cloud Foundry

Once you have installed the product, it automatically registers itself with your Elastic Runtime. At this point, the product is available to your application developers, either in the Marketplace in the web based console, or via `cf marketplace`. They can add, provision, and bind the service to their applications like any other CF service:

```
$ cf create-service p-redis shared-vm redis
$ cf bind-service my-application redis
$ cf restart my-application
```

## Available Plans

There are two available plans:

<table border="1" class="nice">
<tr>
<th><strong>Plan Name</strong></th>
<th><strong>Suitable for</strong></th>
<th><strong>Tenancy Model per Instance</strong></th>
<th><strong>Highly Available</strong></th>
<th><strong>Backup Functionality</strong></th>
</tr>

<tr>
<td><b>Shared-VM</b></td>
<td>Development and testing workloads</td>
<td>Shared VM</td>
<td>No</td>
<td>No</td>
</tr>

<tr>
<td><b>Dedicated-VM</b></td>
<td>Production workloads</td>
<td>Dedicated VM</td>
<td>No</td>
<td>No</td>
</tr>

</table>

### Shared-VM Plan

An instance of this plan, provisions a single Redis process, on a single **shared VM**, which is suitable for development workloads. 

We **do not** recommend using this in a production environment.

Data persistence is enabled through the use of `RDB` and `AOF`.

#### Operator Notes
This plan can be disabled by setting the `Max instances limit` on the `Shared-VM Plan` tab in OpsManager to be `0`.

#### Known Limitations

Limitations with the current `shared-vm` plan include:

* It cannot be scaled beyond a single virtual machine.
* It has no backup and restore capabilities.
* The following commands are disabled: `CONFIG`, `MONITOR`, `SAVE`, `BGSAVE`,
  `SHUTDOWN`, `BGREWRITEAOF`, `SLAVEOF`, `DEBUG`, and `SYNC`.
* Constraining CPU and/or disk usage is not supported.

### Dedicated-VM Plan

An instance of this plan, provisions a single Redis process, on a single **dedicated VM**, which is suitable for production workloads. 

The following commands are enabled:

* `MONITOR`
* `SAVE`
* `BGSAVE`
* `BGREWRITEAOF`

Data persistence is enabled through the use of `RDB` and `AOF`.

The `maxmemory` value for the Redis process is set to be 45% of the RAM for that instance.

#### Operator Notes

These instances are pre-provisioned during the deployment of the tile from OpsManager, into a "pool". The VMs are provisioned and configured with a Redis process ready to be used, when an instance of the `dedicated-vm` plan is requested. 

A default deployment will provision `5 instances` of the `dedicated-vm` plan into the "pool". This number can be increased on the `Resource Config` tab in OpsManager, either in the initial deployment or subsequently thereafter. The number of VMs **cannot** be decreased once deployed. 

When a user provisions an instance, it is marked as in use and taken out of the "pool".

When a user deprovisions an instance, it is cleansed of any data and configuration to restore it to a fresh state and placed back into the "pool" ready to be used again. 

This plan can be disabled by setting the number of instances of the `Dedicated node` job in OpsManager to be `0`.

#### Known Limitations
Limitations with the current `dedicated-vm` plan include:

* No ability to change the Redis configuration, the `CONFIG` command is disabled
* Cannot scale down the number of VMs on the plan, once deployed
* Not highly available, each instance is a single VM with no master / slave setup.

## Licencing

Development and testing workloads are covered under the **PCF OpsManager** entitlement. 

Production workloads are covered under the **Pivotal Services Suite** entitlement.

## Support
Support is provided for production workloads, if you have a **Pivotal Services Suite** entitlement.

[Visit the support home page](https://support.pivotal.io/hc/en-us)

## Example Application

To help your application developers get started with Redis for Pivotal CF, we have provided an example application, which can be [downloaded here](https://github.com/pivotal-cf/cf-redis-example-app/archive/master.zip).

## Feedback

Please provide any bugs, feature requests, or questions to [the Pivotal CF Feedback list](mailto:pivotal-cf-feedback@pivotal.io).

## Version

This product is based on Redis version 2.8.18. 

## Further Reading

* [Official Redis Documentation](http://redis.io/documentation)

