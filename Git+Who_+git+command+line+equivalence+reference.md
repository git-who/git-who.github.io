# Git Who: git command line equivalence reference

## After the initial commit was pushed of a new repository.

git branch develop

git push -u origin develop

## After a clone

git checkout -t origin/develop

## Syncing **develop** and **master **branches, this should be before any operation listed below

git fetch --all -p -P -t

git pull origin develop

git pull origin master

## Starting a **feature/** branch, when not done from Jira or BitBucket.

git checkout develop

git checkout -b feature/JIRA-999-example

git push -u origin feature/JIRA-999-example

## Syncing a **feature/ ** for the first time, when started from Jira or Bitbucket

git checkout -t origin/feature/JIRA-999-example

Syncing a **feature/** branch

**When in feature/JIRA-999-example branch**

git pull

\# normally the pull should return: Already up to date.

git push

**Anywhere**

git pull origin feature/JIRA-999-example

git push origin feature/JIRA-999-example

## Updating a **feature/** branch with the lasted changes of **develop**

**When in feature/JIRA-999-example branch**

git pull origin develop \#normally done by the syncing of develop and
master brnaches

git merge --no-ff develop

## Finishing a **feature/** branch, without a pull-request

**When in feature/JIRA-999-example branch**

git checkout develop

git merge --no-ff feature/JIRA-999-example

git push

\# delete the local branch

git branch -d feature/JIRA-999-example

\#delete the remote branch

git push origin :feature/JIRA-999-example

## Delete merged **feature/** branch after been finished by a pull-request

**anywhere**

\# delete the local branch

git branch -d feature/JIRA-999-example

\#delete the remote branch, if not already done by the pull-request

git push origin :feature/JIRA-999-example

## Starting a **release/** branch, when is not done from BitBucket

git checkout develop

git checkout -b release/19.6.4

git push -u origin release/19.6.4

## Syncing a **release/ ** for the first time, when started from Bitbucket

git checkout -t origin/release/19.6.4

## Syncing a **release/** branch

**When in release/19.6.4 branch**

git pull

\# normally the pull should return: Already up to date.

git push

**When NOT in release/19.6.4 branch**

git pull origin release/19.6.4

git push origin release/19.6.4

## Updating **develop **with the lasted changes of **release/**

**When in release/19.6.4 branch**

git checkout develop

git pull

git merge --no-ff release/19.6.4

git push

git checkout -

## finishing **release/**

**When in release/19.6.4**

\# develop and master branches must be absolutely synced

\# if the distance between this branch and develop branch is not 0, you
should do the update develop with the lasted changes of release/

git checkout master

\# merge prefers changes from the release/ branch and don't edit the
message

git merge --no-ff -X theirs --no-edit release/19.6.4

git tag 19.6.4

\# it's preferable to push the tags before the master branch

git push origin 19.6.4

git push

\# delete the local branch

git branch -d release/19.6.4

\# delete the remote branch

git push origin :release/19.6.4

git checkout develop

## Starting a **bugfix/** branch, when not done from Jira or BitBucket.

git checkout release/19.6.4

git checkout -b bugfix/JIRA-999-example

git push -u origin bugfix/JIRA-999-example

## Syncing a **bugfix/ ** for the first time, when started from Jira or Bitbucket

git checkout -t origin/bugfix/JIRA-999-example

## Syncing a **bugfix/** branch

**When in bugfix/JIRA-999-example branch**

git pull

\# normally the pull should return: Already up to date.

git push

**Anywhere**

git pull origin bugfix/JIRA-999-example

git push origin bugfix/JIRA-999-example

## Finishing a **bugfix/** branch, without a pull-request

**When in bugfix/JIRA-999-example branch**

git checkout release/19.6.4

git merge --no-ff bugfix/JIRA-999-example

git push

\# delete the local branch

git branch -d bugfix/JIRA-999-example

\#delete the remote branch

git push origin :bugfix/JIRA-999-example

\#do the Updating develop with the lasted changes of release/

## Delete merged **bugfix/** branch after been finished by a pull-request

**anywhere**

\# delete the local branch

git branch -d bugfix/JIRA-999-example

\#delete the remote branch, if not already done by the pull-request

git push origin :bugfix/JIRA-999-example

## Starting a **hotfix/** branch, when is not done from BitBucket

git checkout master

git checkout -b hotfix/19.6.4.1

git push -u origin hotfix/19.6.4.1

## Syncing a **hotfix/ ** for the first time, when started from Bitbucket

git checkout -t origin/hotfix/19.6.4.1

## Syncing a **hotfix/** branch

**When in hotfix/19.6.4.1 branch**

git pull

\# normally the pull should return: Already up to date.

git push

**When NOT in hotfix/19.6.4.1 branch**

git pull origin hotfix/19.6.4.1

git push origin hotfix/19.6.4.1

## Updating **release/ **with the lasted changes of **hotfix/**

**When in hotfix/19.6.4.1 branch**

git checkout release/19.6.5

git pull

git merge --no-ff hotfix/19.6.4.1

git push

git checkout -

## finishing **hotfix/**

**When in hotfix/19.6.4.1**

\# develop and master branches must be absolutely synced

\# if the distance between this branch and develop branch is not 0, you
should do the update develop with the lasted changes of hotfix/

git checkout master

\# merge prefers changes from the hotfix/ branch and don't edit the
message

git merge --no-ff -X theirs --no-edit hotfix/19.6.4.1

git tag 19.6.4.1

\# it's preferable to push the tags before the master branch

git push origin 19.6.4.1

git push

\# delete the local branch

git branch -d hotfix/19.6.4.1

\# delete the remote branch

git push origin :hotfix/19.6.4.1

git checkout develop
