# Code Snippets

### To start a process via supervisor server
```
sudo supervisord -c supervisor.conf
```

### To check status of running process
```
supervisorctl -c supervisor.conf
> status
```

### To check logs of a running process
```
> tail -f <process_name>
>tail -f <process_name> stderr
```

### For help in supervisor client
```
> help
```

### To exit supervisor client
```
> exit
```

[Reference](https://www.digitalocean.com/community/tutorials/how-to-install-and-manage-supervisor-on-ubuntu-and-debian-vps)
