---
title: Redis for PCF Smoke Tests
owner: London Services
---

Redis for PCF runs a set of smoke tests during installation to confirm system health. The tests run in the org 'system' and in the space 'redis-smoke-tests'. The tests run as an application instance with a restrictive ASG (Application Security Group). The tests use the cf-redis-example-app to test basic usage of Redis.  


