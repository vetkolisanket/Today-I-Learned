# Coming soon...

Command to generate *.pb.go file from *.proto file
```
protoc --go_out=plugins=grpc:. *.proto
```

1. Specify what your gRPC service is supposed to do in a proto file
```
// The greeting service definition.
service Greeter {
  // Sends a greeting
  rpc SayHello (HelloRequest) returns (HelloReply) {}
}

// The request message containing the user's name.
message HelloRequest {
  string name = 1;
}

// The response message containing the greetings
message HelloReply {
  string message = 1;
}
```

The `message` blocks are the holders of data via which communication happens in a gRPC service. The service block specifies the interface methods via which communication happens between the server and the client using different message blocks for request and response.  

[Reference](https://github.com/grpc/grpc-go/tree/master/examples)
