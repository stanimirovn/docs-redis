# Redis for PCF Docs

## Where is the book repo?
https://github.com/pivotal-cf/docs-book-redis

The book repo uses these branches:

* **Edge** builds from the **master** content branch in this repo.
* **Master** builds from the **-live** content branches in this repo.

## Branches in this (content) repo

**Note:** We only document to the second digit of the release number, for example, 1.x, not 1.x.x. So if a doc change is needed for a new patch 1.x.x, it will be included in the docs for 1.x.

### Master - Use for next unreleased version

All documentation for the next unreleased version of Redis is in `master`. 

Always make changes you want carried forward in the master branch. This includes:

* Unreleased features
* Doc bug fixes
* Doc reorganization or enhancement

### Live Branches In Production (Public)

* **1.12**: Live docs at staging (https://docs-pcf-staging.cfapps.io/redis/1-12/) and production (https://docs.pivotal.io/redis/1-12/)
* **1.11**: Live docs at staging (https://docs-pcf-staging.cfapps.io/redis/1-11/) and production (https://docs.pivotal.io/redis/1-11/)
* **1.10**: Live docs at staging (https://docs-pcf-staging.cfapps.io/redis/1-10/) and production (https://docs.pivotal.io/redis/1-10/)
* **1.9**: This branch is no longer in use because the docs are no longer live.PDF available at https://docs.pivotal.io/archives/redis-1.9.pdf.
* **1.8**: Live docs at staging (https://docs-pcf-staging.cfapps.io/redis/1-8/) and production (https://docs.pivotal.io/redis/1-8/)
* **1.7**: This branch is no longer in use because the docs are no longer live. PDF available at https://docs.pivotal.io/archives/redis-1.7.pdf.
* **1.6**: This branch is no longer in use because the docs are no longer live. PDF available at https://docs.pivotal.io/archives/redis-1.6.pdf.
* **1.5**: This branch is no longer in use because the docs are no longer live. PDF available at https://docs.pivotal.io/archives/redis-1.5.pdf.
* **1.5**: This branch is no longer in use because the docs are no longer live. PDF available at https://docs.pivotal.io/archives/redis-1.5.pdf.
* **1.4**: This branch is no longer in use because the docs are no longer live. PDF available at https://docs.pivotal.io/archives/redis-1.4.pdf.

### Cherry picking to and from MASTER

1. Always cherry-pick any changes to live branches into **master** if you want those changes carried forward.

2. If necessary, immediately cherry-pick/copy changes from **master** that you want to push immediately to production into the appropriate live branch above.


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
