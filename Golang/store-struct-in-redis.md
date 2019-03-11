# How to store struct in redis the right way

If you want to store a struct in redis, you can always convert it into bytes and then store it, something like this

```
dataBytes := json.Marshal(r)
r.Set("key", dataBytes, 0)
```
 and then while retrieving the struct back, you will get the string form of the data which you can convert back to your struct
 
 ```
 
 ```
