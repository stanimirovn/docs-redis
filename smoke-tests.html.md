---
title: Redis for PCF Smoke Tests
owner: London Services
---

Redis for PCF runs a set of smoke tests during installation to confirm system health. The tests run in the org 'system' and in the space 'redis-smoke-tests'. The tests run as an application instance with a restrictive ASG (Application Security Group).

### Smoke test steps

The test does the following for each available service plan:

1. Targets the org 'system' and space 'redis-smoke-tests' (creating them if they do not exist)
1. Creates a restrictive security group ('redis-smoke-tests-sg') and bind it to the space
1. Deploys an instance of the [CF Redis Example App](https://github.com/pivotal-cf/cf-redis-example-app) to this space
1. Creates a Redis instance and bind it to the app
1. Checks the app can write to and read from the Redis instance

### Security groups

Smoke tests create a new [application security group](https://docs.pivotal.io/pivotalcf/1-7/adminguide/app-sec-groups.html) for the CF Redis Example App (`redis-smoke-tests-sg`) and delete it once the tests finish. This security group has the following rules:

```
[
    {
      "protocol": "tcp",
      "destination": "<dedicated node IP addresses>",
      "ports": "6379" // Redis dedicated node port
    },
    {
      "protocol": "tcp",
      "destination": "<broker IP address>",
      "ports": "32768-61000" // Ephemeral port range (assigned to shared-vm instances)
    }
]
```

This allows outbound traffic from the test app to the Redis shared VM and dedicated VM nodes.

### Troubleshooting

If errors occur while the smoke tests run, they will be summarised at the end of the errand log output. Detailed logs can be found where the failure occurs. Some common failures are listed below.

<table border='1' class='nice'>
<tr>
  <th width="22%">Error</th>
  <td><code>Failed to target Cloud Foundry</code>
  </td>
</tr>
<tr>
  <th>Cause</th>
  <td>Your Pivotal Cloud Foundry&reg; is unresponsive</td>
</tr>
<tr>
  <th>Solution</th>
  <td>Examine the detailed error message in the logs and check the <a href="https://docs.pivotal.io/pivotalcf/1-7/customizing/troubleshooting.html">PCF Troubleshooting Guide</a> for advice</td>
</tr>
</table>
