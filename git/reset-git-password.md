# How to reset git password

To fix this on macOS, you can use
```
git config --global credential.helper osxkeychain
```
A username and password prompt will appear with your next Git action (pull, clone, push, etc.).

For Windows, it's the same command with a different argument:
```
git config --global credential.helper wincred
```


[Reference](https://stackoverflow.com/questions/20195304/how-do-i-update-the-password-for-git)
