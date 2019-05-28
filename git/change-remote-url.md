# How to change remote url of an existing git project?

- Go to the root directory
- Delete the exisiting ```.git``` directory
```
rm -rf .git
```
- Initialize a new git directory
```
git init
```
- Add the new remote origin
```
git remote add origin <remote-url>
```
- Add files
```
git add -A .
```
- Make initial commit
```
git commit -a -m "Initial commit"
```
- Push the code
```
git push origin master
```
- To check your changes have reflected 
```
git config --list
```
