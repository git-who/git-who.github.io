# Git Who Branching Model

![](./media/image1.tmp)

In the following  text:

  - All branches names will be in bold: **master**

  - Command line will be in italic: *ls -al*

  - Version number will be bold and
    underline: **<span class="underline">19.5.1</span>**

  - Jira ticket will be in italic and
    underline:<span class="underline"> *GEDDO-15*</span>

<span class="underline">And we will apply those concepts:</span>

  - **commit:** They are any types of Git commits including direct,
    merge, revert and cherry-pick ones. They are basically any points on
    a Git tree.

  - **direct commit:** A commit created by a basic *git commit* command.
    Which are changes applied directly by a developer. 

  - **merge commit**; A commit create by a no-fast-forward merge.
# Why

Why this workflow was created for a  CI that use JIRA, Bitbucket server (Stash), and Jenkins; that produce Chocolatey, Nuget, NPM and Maven packages.
The branching model is based on GitFlow with **bugfix/** branch, like suggest  the [BitBucket branching
mode](https://confluence.atlassian.com/bitbucketserver057/using-branches-in-bitbucket-server-945543608.html?utm_campaign=in-app-help&utm_medium=in-app-help&utm_source=stash)l,
which give us the possibility to create branches directly from JIRA.
It's was amended to fit with our [Year.Month.Release\[.Hotfix\]
versioning
model]({% link /Year.Month.Release[.Hotfix]+versioning+model.md %}),
which conforms to the versioning model allowed by Chocolatey packaging
system. Both of those models are based on the standard models of GitFlow
with bugfix branches and on SemVer 1.0 with Microsoft 4 numbers
versioning. Those models were adapted for a larger scope of life cycle
styles. 

# The branching models

GitFlow, itself has a major flaw, long-lived prefixes branches
will inevitably create merge conflicts and other problems. To avoid
that,  we simply always kept the whole Git repository tree, up-to-date
and especially for the develop branch.  We will call that the "Updating"
process in rest of this document. Most of the process of GitWho has been
automated in [the GitWho automation
Jenkins-Libraries](https://github.com/mikeboutch/GitWho-JenkinsLibs).



# THE BRANCHES:

# The Main branches or Trunk branches or Permanent branches

Those branches are always present and must not be deleted. Nobody should
ever commit directly to those branches. Those branches should be always
synced, and tracked. 

## Production or the real release branch: **master**

> This is the ready-to-be-released branch, the production branch. This
> must only contain what we consider as production-ready. Version are
> given by tags, which come from the suffix of
> a **release/** or **hotfix/** branches.  All commits must result
> from a merge of **release/** or **hotfix/** branches. We name this
> branch **master**, since **master** is the default branch of Git, so
> it's will give a simpler way to do Git command or configuring Git
> related software and that especially for *git clone* command. Normally
> this should have restricted access, only the release managers or
> non-developer should approve merge to this branch. 

## Development or the real main trunk: **develop **

> This is the main branch who represent latest delivered development
> changes. It's also called integration branch and contain normally
> latest stable codes. Contain normally pull request (merge) from
> the **feature/** or merge from **release/** or indirect merge
> from **hotfix/** branches.  **develop **normally contain newer code
> than **master**.  This branch must be updated with all know good
> changes, since this branch represent the latest know stable codes.

# Supporting branches or Prefixes branches or Developer workplace

Those branches are created per need and once completed should be
deleted. Those branches are the places where developers works.

## **feature/...**

  - ***Starting*: **Branch off **develop**, this is done preferably from
    Jira.

  - ***Suffix*:** Jira ticket number
    (*<span class="underline">GEDTECH-9999</span>*) followed by a
    comment if needed.

  - ***Finishing*: **Merge back to **develop**, this is done by doing a
    Pull-Request in BitBucket. The **feature/** branch is deleted after
    been merged and that deletion is automated by the GitWho automation
    Jenkins-Libraries.

  - ***Updating*:** If needed, **develop** can be merged into the
    current **feature/** branch.  Should not be automated and be done
    manually by the developers.

  - **Contain: **Direct commits of any types of changes and merge
    commits from **develop**.

> Branch from **develop **and merge back into **develop **normally by a
> pull request. This is where developers mainly works and commit
> directly their stuff. May contain, new features, future release, bug
> fix, improvement, sandbox code. etc..  You can have
> many **feature/** branches open at the same time. This permit
> parallel development. If a **feature/** branch is kept open too long,
> it's will not be phased with the latest changes. So developer can
> manually merge the latest change from **develop** into
> that **feature/** branch. This would help to diminish merge conflicts
> when the branch is finished.  

## Release preparation branches:

Those prefixes branches are a cut-offs of the rest (or the equivalent of
a code freeze for staging propose) to permit a preparation for a new
production release.

## **release/...**

  - ***Starting*: **Branch off from **develop**, this is done preferably
    from Bitbucket.

  - ***Suffix*: **Target version, 3 numbers separated
    in **<span class="underline">YY.MM.R</span>** format.
    (**<span class="underline">19.5.1</span>**)

  - ***Finishing*: **Merge into **master**, tagged on **master** with
    the target version.  The **release/** branch is deleted after
    that. With the GitWho automation Jenkins-Libraries,  it's better to
    finish with a Pull Request. Jenkins will do all the check, tag the
    merge commit and delete the **release/** branch.

  - ***Updating*: **Each commit (normally merge commits) should be
    merged into **develop**. This is automated with the GitWho
    automation Jenkins-Libraries.

  - **Contain: **Merge commits from **bugfix/** and **hotfix/**.

> They have the target release version number as suffix branch name. The
> target release version must be a new release version, never used
> before. This branch should be merged back to **develop** after each
> commit, that will permit to kept the **develop** branch
> updated.** **This branch should be deleted at the end of every
> release, once the branch has been merged to **master**, and tagged
> on **master** with the target release version. Developers commit
> changes through a branch-off  **bugfix/ **branch, who will be merged
> back  into. Only bug fixes, configuration, documentation or
> presentation changes, should be merged. Only one  **release/ **branch
> can be open at same the time.** **

## **hotfix/...**

  - ***Starting*: **Branch off **master**, this is done preferably from
    Bitbucket normally only when a **release/** branch is already open.
    If not it should be really outside the normal release cycle.

  - ***Suffix*: **Target version, 4 numbers separated
    in **<span class="underline">YY.MM.R.H</span>** format,
    where **<span class="underline">YY.MM.R</span>** is tagged version
    number of the branching off commit of **master**.
    (**<span class="underline">19.5.1.1</span>**)

  - ***Finishing*: **Merge into **master**, tagged on **master** with
    the target version.  The **hotfix/** branch is deleted after that.
    With the GitWho automation Jenkins-Libraries, it's better to finish
    with a Pull Request.  Jenkins will do all the check, tag the merge
    commit and delete the **hotfix/** branch.

  - ***Updating*: **Each commit should be merged into the
    open **release/ **branch and will be indirectly merged
    from **release/** into **develop**. If no **release/** branch is
    open, just merge each commits into **develop.** This is automated
    with the GitWho automation Jenkins-Libraries.

  - **Contain: **Direct commits of emergency patches.

> They have the target release version number as suffix branch name.
> Normally created when  it's too much complicated to branch off
> of **develop ,** the bug happen in production and the bug should be
> fixed as soon as possible. Should normally have a **release/** branch
> open, to start a **hotfix/** and should be finished before
> the **release/** finish.  Normally this branch should be use only
> when needed, when it's an emergency (duct tape and tie wrap situation)
> and must be treated has a major derogation of the life-cycle. And
> since that branch is only for emergency, we shouldn't do any kind of
> pull request or code review during the life of the branch. Basically
> once the creation is approved (normally by an escalation), fix things
> ASAP, test it ASAP and deployed it after the approval of release
> managers in production ASAP. The main difference
> from **release/** branch is that it's branch off normally
> from **master**.  Developers commit directly bug fixes,
> configuration, presentation changes, only. Only one **hotfix/** can
> be open at same the time.** **This branch should be merged into the
> open **release/** branch after each commit, that will permit to kept
> the **release/ **branch updated and indirectly
> the **develop** branch.  If no **release/ **branch is open, just
> merge each commits into **develop**, The updating process for this
> branch is more prone to merge conflicts.

## **bugfix/...**

  - ***Starting*: **Branch off from the open **release/ **branch, this
    is done preferably from Jira.

  - ***Suffix*:** Jira ticket number
    (*<span class="underline">GEDTECH-9999</span>*) followed by a
    comment if needed.

  - ***Finishing*: **Merge back to the open **release/ **branch, this is
    done by doing a Pull-Request in BitBucket. The **bugfix/** branch is
    deleted after been merged and that deletion is automated by GitWho
    automation Jenkins-Libraries.

  - ***Updating*:**  A **bugfix/** branch shouldn't live for a too long
    times, so no update from their commits. When finished and merged
    into **release/**, the merged commit will be indirectly merged
    from **release/** into **develop**. This is automated with GitWho
    automation Jenkins-Libraries.

  - **Contain: **Direct commit of bug fixes, configuration,
    documentation or presentation changes.

> Branch from **release/** and merge back into **release/ **normally by
> a pull request.  You can have many **bugfix/** branches open at the
> same time. This permit parallel development. Only bug fixes,
> configuration, documentation or presentation changes, should be
> committed. This branch should be deleted after been finished.

# Downsizing Git who for smaller and/or simpler project.

## First level: Don't use **bugfix/ **branches (Use the original GitFlow)

> Commit change directly in release/ branch.

## Second level: Don't use **release/** or **hotfix/ **branch

> That option work only if you DONT use Pull Request for releasing.

## Second level: Don't use **feature/ **branch

> That option work only if you DONT use Pull Request for your
> development .

# Common mistakes:

## Create or use branches outside of the the model.

> Even if the default naming could be confusing, it better to use it.
> It's would avoid some typo error and also it will be easier to use
> with Atlassian products like BitBucket and JIRA. And please never ever
> never use other nomenclatures for branches name. **feature/ **branch
> only branch off and merge back with **develop**. etc... etc...

## Not doing frequently syncing.

>  **develop** and **master** branches should be synced before any
> branch off or merge.

## Doing merge that are not "no fast-forward"

> ...

## Prefixes branches aren't deleted after been finished.

> To have a readable network of branches it's better to delete all
> branches are finished. So basically you should have open only 
> the **master** and **develop** branches and prefixes branches that
> are in progress. That would help also any automation process, since we
> don't have to check all the branches. You may have
> some **feature/** branch left because the feature was abandoned, but
> it's better to delete them if they will not be used in the future.
> Normally abandoned **release/** branch are simply deleted. Be careful
> because deleted branches on the remote will not be deleted
> automatically from your local working copy, if you don't re-clone the
> repositories.

## Merge **feature/** branch into **develop** without good testing and/or approval.

> **develop** should be a stable version of the project. So code review
> is important, but also the approval from the owner of the change. Also
> the **feature/** should sometime be rewritten before the the PR, so
> the it will ease the code review and kept a readable and clean tree in
> the Git repositories. The same things apply to
> the **bugfix/** branches,

## Misuse of release preparation branches.

> Basically those branches are not **feature/** branches. Those branches
> are the last place to apply changes.  Their are not the place to apply
> changes of business logic.  The overuse of **hotfix/ **branches or a
> over crowded **release/** branches with bug fixes, can be a sign of a
> not so good QA or development process....

## Open prefixes branches too soon.

> Branching off at right time will increase the possibility that you
> have the latest wanted changes. So
> for **feature/** or **bugfix/ ** branches should be created only,
> when you somebody will write some code in it, right-away.

## Assume that all release are perfectly good and must be deployed.

> **master** contain all the releases, but bad or unwanted release
> happen. So not all point of **master** should be deployed.

## Assume that we must create **release/** branch from the head of **develop**, or create **hotfix/** from the head of **master**.

> Since **develop** it's a living branch and it's should be fully tested
> before branching out a **release/** branch. **release/** branches
> will  be sometime branch out from a previous commit of **develop**. 
> 
> When the last deployed release version has a major defect, you can
> branch out a **hotfix/** branch from a previous release
> in **master**. But like any other **hotfix/** branches, they should
> be considerate has an emergency patch and a derogation.

 

# Advanced GIT.

## Rewriting **feature/** and **bugfix/ **branches: Kept them clean and readable.

...

## *git revert* : Remove bad or so not ready **feature/** merge in **develop** without rewriting **develop**.

>  The *git revert* command can be also used for removing  specific
> unwanted merge commit from the **develop** branch. And you can always
> revert the revert so your **develop** branch will have the reverted
> merge.

## The use of feature flag : The best way to kept only one source code source repository.

> That is not Git related...
