# Redis for VMware Tanzu Application Service Docs

## Where is the book repository?

The book repo associated with this content repo is [**docs-book-redis**](https://github.com/pivotal-cf/docs-book-redis).

## Partials

Cross-product partials for **Redis for VMware Tanzu Application Service** are single sourced from the [Services Partials](https://github.com/pivotal-cf/docs-partials) repository.

Previously, these partials were sourced from the v018.x branch of the [On Demand Service Broker SDK](https://github.com/pivotal-cf/docs-on-demand-service-broker/tree/v0.18.x) content repository.

## Branches in this (content) repository

### Master - Use for next unreleased version

All documentation for the next unreleased version of Redis is in `master`.

Always make changes you want carried forward in the master branch. This includes:

* Unreleased features
* Doc bug fixes
* Doc reorganization or enhancement

### Live Branches In Production (Public)

* **3.1**: Live docs at staging (https://docs-pcf-staging.cfapps.io/redis/3-1/) and production (https://docs.pivotal.io/redis/3-1/)
* **3.0**: Live docs at staging (https://docs-pcf-staging.cfapps.io/redis/3-0/) and production (https://docs.pivotal.io/redis/3-0/)
* **2.4**: Live docs at staging (https://docs-pcf-staging.cfapps.io/redis/2-4/) and production (https://docs.pivotal.io/redis/2-4/)
* **2.3**: Live docs at staging (https://docs-pcf-staging.cfapps.io/redis/2-3/) and production (https://docs.pivotal.io/redis/2-3/)
* **2.2**: This branch is no longer in use because this version is EOGS. Live docs at staging (https://docs-pcf-staging.cfapps.io/redis/2-2/) and production (https://docs.pivotal.io/redis/2-2/)
* **2.1**: This branch is no longer in use because this version is EOGS. Live docs at staging (https://docs-pcf-staging.cfapps.io/redis-eogs/2-1/) and production (https://docs.pivotal.io/redis-eogs/2-1/)
* **2.0**: This branch is no longer in use because this version is EOGS. Live docs at staging (https://docs-pcf-staging.cfapps.io/redis-eogs/2-0/) and production (https://docs.pivotal.io/redis-eogs/2-0/)
* **1.14**: This branch is no longer in use because this version is EOGS. Live docs at staging (https://docs-pcf-staging.cfapps.io/redis-eogs/1-14/) and production (https://docs.pivotal.io/redis-eogs/1-14/)
* **1.13**: This branch is no longer in use because the docs are no longer live. PDF available at https://docs.pivotal.io/archives/redis-1.13.pdf.
* **1.12**: This branch is no longer in use because the docs are no longer live. PDF available at https://docs.pivotal.io/archives/redis-1.12.pdf.
* **1.11**: This branch is no longer in use because the docs are no longer live. PDF available at https://docs.pivotal.io/archives/redis-1.11.pdf.
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

Use this section to specify spelling of special words for Redis for VMware Tanzu Application Service:

+ on-demand plan
+ shared-VM plan

## Pipelines

**Edge Pipeline**<br>
The `master` branch builds to the <br> <strong>cf-services-edge > redis-edge</strong> pipeline, and does not go to production until release time: [Edge pipeline](https://concourse.run.pivotal.io/teams/cf-docs/pipelines/cf-services-edge?groups=redis-edge). <br>

**Production Pipeline**<br>
All live branches build to the <strong>cf-services > redis</strong> pipeline,
and are manually pushed to production as needed: [Production pipeline](https://concourse.run.pivotal.io/teams/cf-docs/pipelines/cf-services?groups=redis).

## How to Cherry-pick from one Branch to Another
1. Make changes in the first branch (usually `master`), commit them, and then push them to the repository.
2. Copy part of the SHA for the above commit. To find this, you can do a `git log`, or look at the list of commits in the github repository.
3. Checkout the second branch, where you want to copy the changes you made in the first branch.
4. Run this command, using the SHA snippet you copied above:
    `git cherry-pick <SHA_SNIPPET>`<br><br>
    For example: `git cherry-pick 5dc22fe00`

    Do the cherry-pick immediately to lessen the chances of conflicts.
    Otherwise, you may need to resolve conflicts in order to complete the cherry-pick.

5. Do a `git push` after the cherry-pick is complete.<br><br>
