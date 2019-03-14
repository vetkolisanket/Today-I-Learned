# Code Snippets

- To compile a protocol buffer definition file
```
protoc --go_out=. *.proto
```
- If the proto file specifies RPC services
```
protoc --go_out=plugins=grpc:. *.proto
```
