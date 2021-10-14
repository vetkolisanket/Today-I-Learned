# Code Snippets

- To change a commit which has not been pushed

```
git commit --amend
```

  Will open the previous commit in vim, you can edit the commit now
- To check the configuration of the current git project
```
git config --list
```

- To list your remote branches
```
git branch
```

- To create a tag
```
git tag -a <tag_name> -m "<message>"
e.g. git tag -a v1.4 -m "Added so and so feature"
``` 

- To print git logs in a readable formatted way
```
git log --pretty="* %s"
e.g. git log --pretty="* %s" --since="midnight" --no-merges
```

- To show a list of tags
```
git tag --list
```
