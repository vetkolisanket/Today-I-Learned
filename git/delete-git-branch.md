# How to delete a git branch locally and remotely

- To delete a remote branch

`git push --delete <remote_name> <branch_name>`

In most cases `remote_name` is `origin`

- To delete a local branch 

`git branch -d <branch_name>`

The `-d` option is an alias for `--delete`, which only deletes the branch if it has already been fully merged in its upstream branch.

- `git branch -D <branch_name>`

You could also use `-D`, which is an alias for `--delete --force`, which deletes the branch "irrespective of its merged status."

[Reference](https://stackoverflow.com/a/2003515)
