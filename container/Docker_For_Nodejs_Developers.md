# Docker for Node.js developers

## Prerequisites

1. [Introduction to Docker](https://github.com/hegdeashwin/articles/blob/master/container/Docker.md)

## Assumptions

1. Docker is already installed and running.
2. Enable logging into Docker Ubuntu container instance.

## Installing Node.js inside Docker container
```
sudo apt-get update

sudo apt-get install nodejs

sudo apt-get install npm
```

Below are few steps **in-case** apt-get command is not working inside container instance.
1. Open NetworkManager.conf file using below command. Note: I have used ```nano``` editor; you can use your ```gedit, vi``` etc. based on your choice.
```
sudo nano /etc/NetworkManager/NetworkManager.conf
```

2. Comment our below line of code in file. Note: ```#``` is a way to comment a single line.
```
#dns=dnsmasq
```

3. Reboot network-manager / restart your Ubuntu
```
reboot network-manager
```

## Check if Node.js and npm are installed
```
nodejs -v

__OUTPUT__
v4.4.7

npm -v

__OUTPUT__
3.5.2

```
