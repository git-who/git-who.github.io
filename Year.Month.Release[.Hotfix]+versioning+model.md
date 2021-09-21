# Year.Month.Release\[.Hotfix\] versioning model

This versioning model was created to be conform to the Chocolatey
packaging system and should be compatible with most packaging system.
This model is made to be used with the [Git Who Branching
Model](file:///E:\\display\\GEDDEV\\Git+Who+Branching+Model) or any
implementation of GitFlow that doesn't use the support branch. It's made
to create a readable link between each commit of a Git repository and
the version number. And also, this model is automated in Jenkins by a
Jenkins-libraries and should have command line helpers. Also this model
support release  (only periods separated numbers) and pre-release
(periods separated numbers followed by a dash and a string) principles
and is be sort-able.

Version of Chocolatey package are based on [Nuget versioning
model. ](https://docs.microsoft.com/en-us/nuget/reference/package-versioning) Which
is basically the [SemVer 1.0](https://semver.org/spec/v1.0.0.html)
 framework with Microsoft 4 numbers versioning.   The model
Major.Minor.Patch of SemVer is not suitable for most SDLC, because the
Major,Minor.Patch make no sense because we cannot predict, if each minor
or patch changes will be delivered after or before another ones.  And
it's always better to have separate developments on different majors
versions.  So it's easier to put the major version in the name of the
products, packages and repositories.  Because of that it's preferable to
use a date based model. Since 2 or more releases or commits can happen
on the same day or simply having only one or 2 releases a week, it's
preferable to use only the year and month. Also since hot fix could
happen, normally only when a release preparation is going on, the 4
numbers version will be needed to kept the all version sort-able and
increasing in times. 

All branches names will be in bold: **master   
**Version number will be in bold and
underline: <span class="underline">**19.5.1**  
</span>Notation used below:

  - **<span class="underline">YY</span>** is 2 digits year,

  - **<span class="underline">M</span>** is the numbers of the month,

  - **<span class="underline">R</span>** is release number in a month
    (incremental, starting at 1)

  - **<span class="underline">H</span>** is hotfix number (incremental,
    starting at 1) 

  - **<span class="underline">B</span>** is the Jenkins build number (0
    if not build in Jenkins or in a CI)

  - **<span class="underline">CCCCCCC</span>** is the short Git commit
    hash

  - ... is almost any string  

## Release version numbering:

> RELEASE or PRODUCTION version:
> 
> Git branch: **master**
> 
> **<span class="underline">YY.M.R</span>** or
> **<span class="underline">YY.M.R.H</span>**
> where:  **<span class="underline">YY.M.R</span>** or **YY.M.R.H **is
> the Git tag
> 
> Ex: **<span class="underline">19.5.2</span>
> <span class="underline">19.5.2.1</span>
> <span class="underline">19.5.2.2</span>
> <span class="underline">19.5.3</span> **

## Pre-release version numbering:

> RELEASE CANDIDATE or RC version:
> 
> Git branch: **release/YY.M.R**
> 
> **<span class="underline">YY.M.R-rc-B-CCCCCCC</span>** where:  **<span class="underline">YY.M.R</span> **is
> the suffix of the branch   
> 
> Ex: **<span class="underline">19.5.2-rc-4-4b47a5b</span>** **<span class="underline">19.5.2-rc-5-321abc5</span>** 
> 
> HOT FIX or HF version
> 
> Git branch: **hotfix/YY.M.R.H**
> 
> **<span class="underline">YY.M.R.H-hf-B-CCCCCCC</span>** where:  **<span class="underline">YY.M.R.H</span> **is
> the suffix of the branch 
> 
> Ex: **<span class="underline">19.5.2.1-hf-1-a5b6396</span> <span class="underline">19.5.2.1-hf-2-1abc5e0</span>** 
> 
> BUG FIX or BF version
> 
> Git branch: **bugfix/...**
> 
> **<span class="underline">YY.M.R-bf-B-CCCCCCC</span>** where:  **<span class="underline">YY.M.R</span> **is
> the suffix of the related **release/YY.M.R** branch,
> 
> Ex: **<span class="underline">19.5.2-bf-12-63a96e3</span>** **<span class="underline">19.5.2-bf-13-63a96e3</span>** 
> 
> BETA Version
> 
> Git branch: **develop**
> 
> **<span class="underline">YY.M.R-beta-B-CCCCCCC</span>** where: **<span class="underline">YY.M.R</span> **is
> the next version (automatically calculated),
> 
> Ex: **<span class="underline">19.5.2-beta-12972-a96e3ac</span>** **<span class="underline">19.5.2-beta-12973-6e32521</span>** 
> 
> ALPHA Version 
> 
> Git branch: **feature/...**
> 
> **<span class="underline">YY.M.R-alpha-B-CCCCCCC</span>** where: **<span class="underline">YY.M.R</span> **is
> the next version (automatically calculated),
> 
> Ex: **<span class="underline">19.5.2-alpha-7-a6eac43</span>** **<span class="underline">19.5.2-alpha-28-6ce2a21</span>**
