# Code Snippets

- To connect to a remote machine
```
ssh <username>@<ip-address>
```
e.g. ssh root@127.0.0.1

- To transfer a file to a remote machine
```
scp <file> <username>@<ip-address>:<location>
```
e.g. scp hello_world.py root@127.0.0.1:/Users/admin/my_projects/python/

- To copy a file from remote machine to local machine
```
scp <username>@<ip-address>:<location> <file>
```
e.g. scp username@remoteHost:/remote/dir/file.txt /local/dir/
