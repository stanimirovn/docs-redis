# Redis for PCF Docs

## Where is the book repo?
https://github.com/pivotal-cf/docs-book-redis

The book repo uses these branches:

* **Edge** builds from the **master** content branch (2.0 - previously known as 1.15 - available on staging here https://docs-pcf-staging.cfapps.io/redis/1-n/). Pipeline [here](https://concourse.run.pivotal.io/teams/cf-docs/pipelines/cf-services-edge?groups=redis-edge).
* **Master** builds from the published content branches in this repo (1.12, 1.11, etc). Pipeline [here](https://concourse.run.pivotal.io/teams/cf-docs/pipelines/cf-services?groups=redis).

## Partials

Cross-product partials for **Redis for PCF** are single sourced from the [PCF Docs Partials](https://github.com/pivotal-cf/docs-partials) repository.

Previously, these partials were sourced from the v018.x branch of the [On Demand Service Broker SDK](https://github.com/pivotal-cf/docs-on-demand-service-broker/tree/v0.18.x) content repo.

## Branches in this (content) repo

### Master - Use for next unreleased version

All documentation for the next unreleased version of Redis is in `master`. 

Always make changes you want carried forward in the master branch. This includes:

* Unreleased features
* Doc bug fixes
* Doc reorganization or enhancement

### Live Branches In Production (Public)

* **1.14**: Live docs at staging (https://docs-pcf-staging.cfapps.io/redis/1-14/) and production (https://docs.pivotal.io/redis/1-14/)
* **1.13**: Live docs at staging (https://docs-pcf-staging.cfapps.io/redis/1-13/) and production (https://docs.pivotal.io/redis/1-13/)
* **1.12**: Live docs at staging (https://docs-pcf-staging.cfapps.io/redis/1-12/) and production (https://docs.pivotal.io/redis/1-12/)
* **1.11**: Live docs at staging (https://docs-pcf-staging.cfapps.io/redis/1-11/) and production (https://docs.pivotal.io/redis/1-11/)
* **1.10**: This branch is no longer in use because the docs are no longer live. PDF available at https://docs.pivotal.io/archives/redis-1.10.pdf.
* **1.9**: This branch is no longer in use because the docs are no longer live. PDF available at https://docs.pivotal.io/archives/redis-1.9.pdf.
* **1.8**: This branch is no longer in use because the docs are no longer live. PDF available at https://docs.pivotal.io/archives/redis-1.8.pdf.
* **1.7**: This branch is no longer in use because the docs are no longer live. PDF available at https://docs.pivotal.io/archives/redis-1.7.pdf.
* **1.6**: This branch is no longer in use because the docs are no longer live. PDF available at https://docs.pivotal.io/archives/redis-1.6.pdf.
* **1.5**: This branch is no longer in use because the docs are no longer live. PDF available at https://docs.pivotal.io/archives/redis-1.5.pdf.
* **1.5**: This branch is no longer in use because the docs are no longer live. PDF available at https://docs.pivotal.io/archives/redis-1.5.pdf.
* **1.4**: This branch is no longer in use because the docs are no longer live. PDF available at https://docs.pivotal.io/archives/redis-1.4.pdf.

### Cherry picking to and from MASTER

1. Always cherry-pick any changes to live branches into **master** if you want those changes carried forward.

2. If necessary, immediately cherry-pick/copy changes from **master** that you want to push immediately to production into the appropriate live branch above.

### Style Sheet

Use this section to specify spelling of special words for Redis for PCF:

+ on-demand plan
+ shared-VM plan
+ dedicated-VM plan

## Pipelines

**Edge Pipeline**<br>
The `master` branch builds to the <br> <strong>cf-services-edge > redis-edge</strong> pipeline, and does not go to production until release time: [Edge pipeline](https://concourse.run.pivotal.io/teams/cf-docs/pipelines/cf-services-edge?groups=redis-edge). <br>

**Production Pipeline**<br>
All live branches build to the <strong>cf-services > redis</strong> pipeline,
and are manually pushed to production as needed: [Production pipeline](https://concourse.run.pivotal.io/teams/cf-docs/pipelines/cf-services?groups=redis).

## How to Cherry-pick from one Branch to Another
1. Make changes in the first branch (usually `master`), commit them, and then push them to the repo.
2. Copy part of the SHA for the above commit. To find this, you can do a `git log`, or look at the list of commits in the github repo.
3. Checkout the second branch, where you want to copy the changes you made in the first branch.
4. Run this command, using the SHA snippet you copied above:
    `git cherry-pick <SHA_SNIPPET>`<br><br>
    For example: `git cherry-pick 5dc22fe00`

    Do the cherry-pick immediately to lessen the chances of conflicts.
    Otherwise, you may need to resolve conflicts in order to complete the cherry-pick.

5. Do a `git push` after the cherry-pick is complete.<br><br>
