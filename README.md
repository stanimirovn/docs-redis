# Redis for PCF Docs

## Branch Management

**MASTER** - Use for the (upcoming) v1.13 release.

All documentation for the next unreleased version of Redis is in `master`. This is the tree-trunk, so ALWAYS make changes you want carried forward in this branch. This includes:

* Unreleased features
* Doc bug fixes
* Doc reorganization or enhancement

Then, if necessary, immediately cherry-pick/copy any changes that you want to push immediately to production into the appropriate live branch below.

Any changes on the `master` branch will not be displayed publicly until a live `1.13` branch is cut.

* **1.12**: Live docs at staging (https://docs-pcf-staging.cfapps.io/redis/1-12/)
* **1.11**: Live docs at staging (https://docs-pcf-staging.cfapps.io/redis/1-11/) and production (https://docs.pivotal.io/redis/1-11/)
* **1.10**: Live docs at staging (https://docs-pcf-staging.cfapps.io/redis/1-10/) and production (https://docs.pivotal.io/redis/1-10/)
* **1.9**: Live docs at staging (https://docs-pcf-staging.cfapps.io/redis/1-9/) and production (https://docs.pivotal.io/redis/1-9/index.html)
* **1.8**: Live docs at staging (https://docs-pcf-staging.cfapps.io/redis/1-8) and production (https://docs.pivotal.io/redis/1-8/index.html)
* **1.7**: Live docs at staging (https://docs-pcf-staging.cfapps.io/redis/1-7/) and production (https://docs.pivotal.io/redis/1-7/index.html)
* **1.6**: Live docs at staging (https://docs-pcf-staging.cfapps.io/redis/1-6/) and production (https://docs.pivotal.io/redis/1-6/index.html)
* **1.5**: This branch is no longer in use because the docs no longer live. PDF available at https://docs.pivotal.io/archives/redis-1.5.pdf.
* **1.4**: This branch is no longer in use because the docs no longer live. PDF available at https://docs.pivotal.io/archives/redis-1.4.pdf.

## Pipelines

The `master` branch builds to the <br> <strong>cf-services-edge > redis-edge</strong> pipeline, and does not go to production until release time. <br>

Other live branches build to the <strong>cf-services > redis</strong> pipeline, 
and are manually pushed to production as needed.

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
