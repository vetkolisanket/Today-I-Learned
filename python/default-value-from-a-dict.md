# How to get a default value from a dict in case a key is not present

If you query for a key in a dict in python and the key is not present, it will return a `KeyError`, you can always workaround this by checking if the key is present in the dict by doing something like below

```
if "k" in d:
    #do something
```

which will return `True` if the key `k` is present in dict `d` or false otherwise. This can work in most cases but there is another way, you can do something like below

```
v = d.get("k")
```

this will assign the value stored against key `k` to variable `v`, and if the key `k` is not present in the dict it will return `None`. So now you can do something like

```
v = d.get("k")
if not v is None:
    #do something
```

You can extend this further to return a default value if a key is not present in the dict by doing something like this

```
v = d.get("k", "your default val")
```

This way if the key `k` is not present in the dict `d` variable `v` will get assigned string value `your default val`. This can be useful in cases where your dict is supposed to store a list against a key, you can return an empty list as the default value

```
v = d.get("k", [])
```
