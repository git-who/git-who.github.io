# Git-Flow why ?
![GitFlow](./media/gitflow.png)
## Opinion of the creator of GitFlow - Vincent Driessen
> If your team is doing continuous delivery of software, I would suggest to adopt a much simpler workflow (like GitHub flow) instead of trying to shoehorn git-flow into your team.<br/>
> If, however, you are building software that is explicitly versioned, or if you need to support multiple versions of your software in the wild, then git-flow may still be as good of a fit to your team as it has been to people in the last 10 years. In that case, please read on.<br/>
> To conclude, always remember that panaceas don't exist. Consider your own context. Don't be hating. Decide for yourself.

from [A successful Git branching model](https://nvie.com/posts/a-successful-git-branching-model/) By [Vincent Driessen](https://nvie.com/about/) , March 5, 2020

## Opinion from the creator of GitHubFlow and founder of GitHub - Scoot Chacon
> For teams that have to do formal releases on a longer term interval (a few weeks to a few months between releases), and be able to do hot-fixes and maintenance branches and other things that arise from shipping so infrequently, git-flow makes sense and I would highly advocate it’s use.<br\>
> For teams that have set up a culture of shipping, who push to production every day, who are constantly testing and deploying, I would advocate picking something simpler like GitHub Flow.

from [GitHub Flow](http://scottchacon.com/2011/08/31/github-flow.html) by [Scoot Chacon](http://scottchacon.com/2011/08/31/github-flow.html), August 31, 2011

## Why I worked on that

  This workflow was created for a  CI that use JIRA, Bitbucket server (Stash), and Jenkins; that produce Chocolatey, Nuget, NPM and Maven packages. The branching model is based on GitFlow with **bugfix/** branch, like suggest  the [BitBucket branching model](https://confluence.atlassian.com/bitbucketserver057/using-branches-in-bitbucket-server-945543608.html?utm_campaign=in-app-help&utm_medium=in-app-help&utm_source=stash), which give us the possibility to create branches directly from JIRA. It's was amended to fit with our [Year.Month.Release\[.Hotfix\] versioning model](Year.Month.Release[.Hotfix]+versioning+model.html), which conforms to the versioning model allowed by Chocolatey packaging system. Both of those models are based on the standard models of GitFlow with bugfix branches and on SemVer 1.0 with Microsoft 4 numbers versioning. Those models were adapted for a larger scope of life cycle styles.
