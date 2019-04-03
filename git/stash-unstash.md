If you have any changes on some branch which are not yet committed and want to move onto some other branch you can use the ```stash``` ```unstash``` commands.

First of all stash your changes which you have not committed yet by using the below command

```git stash```

This will stash your changes in a stack
Next switch to the branch on which you'd like to unstash this changes

```git checkout feature/xyz```

And finally unstash your changes on the newly checked out branch by using the below command

```git stash pop```

Now all the changes will be unstashed on to the new branch, you can add and commit them to you new branch
