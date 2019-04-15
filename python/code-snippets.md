# Code Snippets

- To install gRPC and protobuffers
```
python -m pip install grpcio-tools
pip install --upgrade protobuf
python -m pip install grpcio
```
- To generate client side file for gRPC
```
protoc --proto_path=. --python_out=proto proto/api.proto --proto_path=home/shree/include
```
The second proto_path specifies location of any dependency like say google/protobuf/Any.go, up until the directory which contains this structure
- To generate server side file for gRPC
```
python -m grpc.tools.protoc --proto_path=. api.proto --python_out=. --grpc_python_out=. --proto_path=/home/shree/include
```
The second proto_path specifies location of any dependency like say google/protobuf/Any.go, up until the directory which contains this structure
