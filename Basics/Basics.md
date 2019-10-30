# Linux Basics

Author: methylDragon    
Exactly what you think it means!    

------

## Extra Contributors

- batuhantaysi 



## Introduction

Play this first for all the basics!

http://web.mit.edu/mprat/Public/web/Terminus/Web/main.html

Here's another cheatsheet that I didn't write!

https://www.cheatography.com/davechild/cheat-sheets/linux-command-line/



## Linux Basics

### Basic Commands

No seriously, play [Terminus](http://web.mit.edu/mprat/Public/web/Terminus/Web/main.html) first!

Here's a list of useful commands!

```shell
# Get help
$ man

# Superuser
$ sudo

# Basic commands
$ echo
$ cd
$ ls
$ pwd

# File commands
$ cat
$ touch
$ less
$ mv
$ rm
$ cp

# Folder Commands
$ mkdir
$ rmdir

# More commands
$ watch
$ nano
$ grep
```



### Terminal Shortcuts

| Command      | Description                                      |
| ------------ | ------------------------------------------------ |
| CTRL-c       | Stop current command                             |
| CTRL-z       | Sleep program                                    |
| CTRL-a       | Go to start of line                              |
| CTRL-e       | Go to end of line                                |
| CTRL-u       | Cut from start of line                           |
| CTRL-k       | Cut to end of line                               |
| CTRL-r       | Search history                                   |
| !!           | Repeat last command                              |
| !*abc*       | Run last command starting with *abc*             |
| !*abc*:p     | Print last command starting with *abc*           |
| !$           | Last argument of previous command                |
| ALT-.        | Last argument of previous command                |
| !*           | All arguments of previous command                |
| ^*abc*^*123* | Run previous command, replacing *abc* with *123* |



### See Kernel System

```shell
$ uname -a # All
$ uname -v # Version only
```



### See Operating System

Any of these should work

```shell
$ cat /etc/os-release
$ lsb_release -a
$ hostnamectl
```



### Check IP Address

Either one

```shell
$ ifconfig

$ ip addr show
$ ip addr show <specific_interface>
```



### Check Free Disk Space

```shell
$ df -ah
```



### Manage Services

Either one (service is older)

```shell
$ service <service_name> status
$ service <service_name> start
$ service <service_name> stop

$ systemctl status <service_name>
$ systemctl start <service_name>
$ systemctl stop <service_name>
$ systemctl reload <service_name>
```



### Check Size of Directory

Disk Usage - du

```shell
$ du -sh <directory>
```



### Check Open Ports

```shell
# Listen for ports
$ netstat -listen
$ netstat -l

# Display open ports
$ netstat -vatn # Ports with TCP connections
$ netstat -vaun # UDP ports only
$ netstat -vat # Convert ports to human readable names
```

You can also use lsof

```shell
$ lsof -i
```



### Check Processes

```shell
$ ps aux
$ ps aux | grep <specific_process>

$ ps axjf # Check processes in hierarchy form

$ top
$ htop
```



### Mount Devices

```shell
$ mount # Check mounts
$ cat /etc/fstab # Check mounts

$ mount /dev/<device_dir> /mnt
$ umount /mnt # Unmount the device
```



```
                            .     .
                         .  |\-^-/|  .    
                        /| } O.=.O { |\    
```

------

 [![Yeah! Buy the DRAGON a COFFEE!](../assets/COFFEE%20BUTTON%20%E3%83%BE(%C2%B0%E2%88%87%C2%B0%5E).png)](https://www.buymeacoffee.com/methylDragon)
