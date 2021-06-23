# Delete a tag locally and remotely

- To delete a tag locally:
```
git tag --delete tagname
```
- To delete a tag remotely
You can push an 'empty' reference to the remote tag name:
```
git push origin :tagname
```
Or, more expressively, use the --delete option (or -d if your git version is older than 1.8.0):
```
git push --delete origin tagname
```
Note that git has tag namespace and branch namespace so you may use the same name for a branch and for a tag. If you want to make sure that you cannot accidentally remove the branch instead of the tag, you can specify full ref which will never delete a branch:
```
git push origin :refs/tags/tagname
```
