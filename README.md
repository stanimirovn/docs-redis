# Redis for PCF Docs

## Branch Management

**MASTER** - Use for the NEXT UNRELEASED VERSION.

All documentation for the next unreleased version of Redis is in `master`. 

ALWAYS make changes you want carried forward in this branch. This includes:

* Unreleased features
* Doc bug fixes
* Doc reorganization or enhancement

**Cherry picking to and from MASTER**

1. Always cherry-pick any changes to live branches into **master** if you want those changes carried forward.

2. If necessary, immediately cherry-pick/copy any changes that you want to push immediately to production into the appropriate live branch below.

**Live Branches**

* **1.6 - 1.12**: Live docs at staging (https://docs-pcf-staging.cfapps.io/redis/1-12/) and production (https://docs.pivotal.io/redis/1-12/)
* **1.5**: This branch is no longer in use because the docs no longer live. PDF available at https://docs.pivotal.io/archives/redis-1.5.pdf.
* **1.4**: This branch is no longer in use because the docs no longer live. PDF available at https://docs.pivotal.io/archives/redis-1.4.pdf.

## Pipelines

**Edge Pipeline**
The `master` branch builds to the <br> <strong>cf-services-edge > redis-edge</strong> pipeline, and does not go to production until release time: [Edge pipeline](https://concourse.run.pivotal.io/teams/cf-docs/pipelines/cf-services-edge?groups=redis-edge). <br>

**Production Pipeline**
All live branches build to the <strong>cf-services > redis</strong> pipeline, 
and are manually pushed to production as needed: [Production pipeline[(https://concourse.run.pivotal.io/teams/cf-docs/pipelines/cf-services?groups=redis).

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
