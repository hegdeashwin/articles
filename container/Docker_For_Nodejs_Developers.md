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

## Clone below example repository

```
git clone https://github.com/hegdeashwin/ubuntu-docker.git
```

This repository contains below things:
* Dockerfile - Holds all configuration for Docker to create image.
* Rest of the files like server.js, package.json, .. etc. are path of Node.js source code.

## Building your image

Go to cloned repository and execute
```
sudo docker build -t hegdeashwin/ubuntu-docker .
```

Note:
* ```.``` [dot] at the end is required.

Your image will now be listed by Docker:
```
sudo docker images
```

## Run the image

Running your image with -d runs the container in detached mode, leaving the container running in the background. The -p flag redirects a public port to a private port inside the container. Run the image you previously built:
```
sudo docker run -p 49160:9000 -d hegdeashwin/ubuntu-docker

__OUTPUT__
85e547fd9cb83701cf6b2868ff18191a68c52c21e6e1676119733085d92adb59
```

## Test

Docker mapped the 9000 port inside of the container to the port 49160 on your machine.
Now you can call your app using curl (install if needed via: sudo apt-get install curl):
```
sudo docker logs 85e547fd9cb83701
curl -i http://localhost:49160 or Open Browser => Hit http://localhost:49160

__OUTPUT__
HTTP/1.1 200 OK
X-Powered-By: Express
Content-Type: text/html; charset=utf-8
Content-Length: 12
Date: Sun, 02 Jun 2013 03:53:22 GMT
Connection: keep-alive

Hello World! Node.js is running on Ubuntu Docker container
```

## Refs:
https://nodejs.org/en/docs/guides/nodejs-docker-webapp/
