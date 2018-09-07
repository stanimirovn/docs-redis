# docs-redis

## Update documentation using the branches as described below:

### Master

This is the main 'going forward' branch, and contains the **next unreleased version**.
This branch builds to the <br> <strong>cf-services-edge > redis-edge</strong> pipeline, and does not go to production until release time. <br>
1. Update this branch for any 'going-forward' changes:
    * New features in next release</br>
    * Reorganization, Enhancements </br>
    * Doc bug fixes</br>

2. If appropriate cherry-pick or copy your changes from <strong>master</strong> to 'live' branches (in production), for example 1.9.

### Other branches in production (e.g., 1.11, 1.10, 1.9...)

These branches build to the <strong>cf-services > redis</strong> pipeline,
and are manually pushed to production as needed.
<br>
1. Update the branches in production as necessary to expose high priority content changes you made to the <strong>master</strong> branch,
 that also apply to live branches. <br><br>
    Example: If you forgot to document a v1.9 feature, document it first in the <strong>master</strong> branch,
    then cherry-pick the change to the 1.9 branch in production.

2. Fix doc bugs that affect customers in the live branches, after you've fixed them in the <strong>master</strong> branch first.

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
