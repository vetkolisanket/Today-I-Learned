# How to remove untracked files?

You can use the `git clean` command to remove untracked files.
Options available are


-d -> Remove untracked directories in addition to untracked files. If an untracked directory is managed by a different git repository, it is not removed by default. Use -f option twice if you really want to remove such a directory.

-f, --force -> If the git configuration variable clean.requireForce is not set to false, git clean will refuse to run unless given -f or -n.

-n, --dry-run -> Don't actually remove anything, just show what would be done.

-q, --quiet -> Be quiet, only report errors, but not the files that are successfully removed.

-x -> Don't use the ignore rules. This allows removing all untracked files, including build products. This can be used (possibly in conjunction with git reset) to create a pristine working directory to test a clean build.

-X -> Remove only files ignored by git. This may be useful to rebuild everything from scratch, but keep manually created files.
