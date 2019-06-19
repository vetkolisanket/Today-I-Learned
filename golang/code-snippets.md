# Code Snippets

- To compile a protocol buffer definition file
```
protoc --go_out=. *.proto
```
- If the proto file specifies RPC services
```
protoc --go_out=plugins=grpc:. *.proto
```
- You can see your godoc rendered as HTML by running a local godoc server. This is great for previewing your godoc before committing changes. To do that, Make sure your code is in GOPATH and run:
```
godoc -http ":8080"
```
Go to http://localhost:8080/pkg and you should see your packages on the list.
