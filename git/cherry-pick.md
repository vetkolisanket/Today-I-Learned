1. Cherry picking in Git means to choose a commit from one branch and apply it onto another.
2. This is in contrast with other ways such as merge and rebase which normally apply many commits onto another branch.
3. Make sure you are on the branch you want to apply the commit to.

```git checkout master```

4. Execute the following:

```git cherry-pick <commit-hash>```
