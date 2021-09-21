# Commit checker in BitBucket

On each repos:

Go in : Repository setting - Hooks  
And Enable : Yet Another Commit Checker  
Finally click on: Edit settings for Yet Another Commit Checker:

![](./media/image1.tmp)

In: JIRA Issue Requirements   
Select :  Require Valid JIRA Issue(s)  
And select: Ignore Unknown JIRA Project Keys

![](./media/image2.tmp)

In: Branch Requirements  
Put in :  Branch Name Regex 

|                                                                                                                                                   |
| ------------------------------------------------------------------------------------------------------------------------------------------------- |
| **(?:master|develop|feature/.\*|release/\[0-9\]+\\.\[0-9\]+\\.\[0-9\]+|bugfix/.\*|hotfix/\[0-9\]+\\.\[0-9\]+\\.\[0-9\]+\\.\[0-9\]+|abandon/.\*)** |

![](./media/image3.tmp)

In: Exclude Commits  
Select: Exclude Merge Commits  
And select: Exclude Service User Commits  
And put in: Exclude User Commits

|            |
| ---------- |
| **GEDTWO** |

![](./media/image4.tmp)

Finally, click: Save
