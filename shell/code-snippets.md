# Code Snippets

- cat /etc/shells - gives overview of known shells on a linux system
- `eval` - command which takes an argument and constructs a command out of it, which will be executed by the shell. [example](https://unix.stackexchange.com/a/23117)
- `set` - command to set or unset values of shell options and positional parameters. e.g. `set -x` show commands and their arguments as they are executed. Useful for debugging shell script.
- To switch from one shell to another just type that shell’s name e.g. zsh, bash, ksh, csh
- `man <some command>` - shows documentation related to that command e.g. `man tail`
- `netstat -ntulp`-shows the list of ports and the things running on them (worked on ubuntu, not working on mac :(). To make it work on mac try one of these `lsof -i :<port-no>(optional)` or `netstat -vanp tcp`
- `sudo -u <user> <command>` - To run <command> as <user>. e.g. `sudo -u admin whoami`

