---
title: Redis for Pivotal Cloud Foundry&reg;
owner: London Services
---

This is documentation for the [Redis service for Pivotal Cloud Foundry&reg;](https://network.pivotal.io/products/p-redis).

## Product snapshot

<dl>
<dt>Current <a href="https://network.pivotal.io/products/p-redis">Redis</a> for Pivotal Cloud Foundry&reg; (PCF) Details</dt>
<dd><strong>Version</strong>: 1.5.10 </dd>
<dd><strong>Release Date</strong>: 15th March 2016</dd>
<dd><strong>Software component version</strong>: Redis OSS 3.0.7</dd>
<dd><strong>Compatible Ops Manager Version(s)</strong>: 1.6.x, 1.5.x</dd>
<dd><strong>Compatible Elastic Runtime Version(s)</strong>: 1.6.x, 1.5.x</dd>
<dd><strong>vSphere support?</strong> Yes</dd>
<dd><strong>AWS support?</strong> Yes</dd>
<dd><strong>OpenStack support?</strong> Yes</dd>
</dl>

## Upgrading to the Latest Version

Consider the following compatibility information before upgrading Redis for Pivotal Cloud Foundry&reg;.

<p class="note"><strong>Note</strong>: Before you upgrade to Ops Manager 1.4.x, you must first upgrade Redis for PCF to any 1.4.x version prior to 1.4.4. This allows Redis for PCF upgrades after you install OpsManager 1.4.x. </p>

For more information, refer to the full [Product Version Matrix](../compatibility-matrix.pdf).

<table border="1" class="nice">
<tr>
	  <th rowspan="2">Ops Manager Version</td>
	  <th colspan="2">Supported Upgrades from Imported Redis Installation</td>
</tr>

<tr>
	<th>From</th>
	<th>To</th>
</tr>

<tr>
	<th rowspan="2">1.3.x</th>
	<td>1.3.2</td>
	<td>1.4.0 - 1.4.2</td>
</tr>

<tr>
	<td>1.4.0, 1.4.1</td>
	<td>Next 1.4.x version - 1.4.3</td>
</tr>

<tr>
	<th rowspan="6">1.4.x, 1.5.x, and 1.6.x</th>
	<td rowspan="2">1.40 - 1.4.3</td>
	<td>1.4.4 - 1.4.21</td>
</tr>

<tr>
	<td>1.5.0 - 1.5.7</td>
</tr>

<tr>
	<td rowspan="2">1.4.4 - 1.4.20</td>
	<td> Next 1.4.x version - 1.4.21
</tr>

<tr>
	<td>1.5.0 - 1.5.10</td>
</tr>

<tr>
	<td>1.4.18</td>
	<td>1.5.0 - 1.5.10</td>
</tr>

<tr>
  <td>1.5.0 - 1.5.9</td>
  <td>Next 1.5.x version - 1.5.10</td>
</tr>

</table>

## Feedback

Please provide any bugs, feature requests, or questions to [the Pivotal Cloud Foundry&reg; Feedback list](mailto:pivotal-cf-feedback@pivotal.io).

## Further Reading

* [Official Redis Documentation](http://redis.io/documentation)
