1. Cherry picking in Git means to choose a commit from one branch and apply it onto another.
2. This is in contrast with other ways such as merge and rebase which normally apply many commits onto another branch.
3. Make sure you are on the branch you want to apply the commit to.

```git checkout master```

4. Execute the following:

```git cherry-pick <commit-hash>```

5. Git 1.7.2 introduced the ability to cherrypick a range of commits. From the release notes:

Note 1: In the ```cherry-pick A..B``` form, A should be older than B. If they're the wrong order the command will silently fail. – damian

Note 2: Also, this will not cherry-pick A, but rather everything after A up to and including B. – J. B. Rainsberger

Note 3: To include A just type git cherry-pick ```A^..B``` – sschaef 

[Reference](https://stackoverflow.com/a/3933416/4291698)
