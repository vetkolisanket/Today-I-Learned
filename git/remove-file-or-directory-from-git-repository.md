# How to remove a file/directory from git repository

- If you have accidentally pushed a file or directory to a git repository and want to remove it, here are the 2 ways in which you can do it

## Remove directory from git and local
- You could checkout 'master' with both directories;
```
git rm -r one-of-the-directories
git commit -m "Remove duplicated directory"
git push origin <your-git-branch> (typically 'master', but not always)
```

## Remove directory from git but NOT local
- As mentioned in the comments, what you usually want to do is remove this directory from git but not delete it entirely from the filesystem (local)

In that case use:
```
git rm -r --cached myFolder
```

[Reference](https://stackoverflow.com/a/6313301/4291698)
