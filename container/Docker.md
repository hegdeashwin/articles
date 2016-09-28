# Introduction to Docker

## What is Container?
* OS-level virtualization, a server virtualization method where the Kernal of OS allows multiple isolated user space instances, such instances are often called containers.
* Duplicate copy of an OS run in a virtual resource space on a system.

## Why should I use it ?
* Faster than Virtual Machine.
* Soft memory, loads application directly on memory.
* Crash Management, can kill a container quick and start another one.
* Limit DDOS, if 1 instance is down start another instance quickly.
* Better security, limit attack space, kill compromised, snap-shot replace.
* Don't leave idle instances and can be scale.

## What is Docker?
* Provides standard container technology to put your application into hosted on whatever type of environment server or services that you need to hosted in.

## Advantage
* Huge community, dev & dev-ops.
* Open source project and written in Google's Go language.
* Lots of Dockerized apps.
* Works well with Chef, Puppet, OpenStack, AWS, Azure, Rackspace.

## Commands [For Ubuntu]

Know your Linux Kernal version
```
apt-cache search linux-headers-$(uname -r)
```

Upgrade your linux-header version
```
sudo apt-get install linux-image-generic-lts-raring linux-headers-generic-lts-raring
```

Install Docker
```
sudo wget -qO- https://get.docker.io/ | sed -e "s/docker.com/docker.io/g" | sh

OR

sudo apt-get install docker.io

__FINAL OUTPUT__
Client:
 Version:      1.9.1
 API version:  1.21
 Go version:   go1.4.2
 Git commit:   a34a1d5
 Built:        Fri Nov 20 13:16:54 UTC 2015
 OS/Arch:      linux/amd64

Server:
 Version:      1.9.1
 API version:  1.21
 Go version:   go1.4.2
 Git commit:   a34a1d5
 Built:        Fri Nov 20 13:16:54 UTC 2015
 OS/Arch:      linux/amd64

If you would like to use Docker as a non-root user, you should now consider
adding your user to the "docker" group with something like:

  sudo usermod -aG docker hegdeashwin

Remember that you will have to log out and back in for this to take effect!
```

Pull down Ubuntu image / Interactive Shell
```
sudo docker run -i -t ubuntu

__OUTPUT__
root@c295a70da8fe: <= Container instance
```

Check if container instances running
```
sudo docker ps
```

Search from Docker Hub for images
```
sudo docker search ubuntu

__OUTPUT__
NAME                              DESCRIPTION                                     STARS     OFFICIAL   AUTOMATED
ubuntu                            Ubuntu is a Debian-based Linux operating s...   4771      [OK]       
ubuntu-upstart                    Upstart is an event-based replacement for ...   66        [OK]      
...

```

Run searched image
```
sudo docker run hegdeashwin/ubuntu-docker echo "hello world"
```

Docker acts as client
```
search
pull
login
push
```

Can also search standard images
```
https://hub.docker.com/explore
```

Print the output of your app:
```
# Get container ID
$ sudo docker ps

# Print app output
$ sudo docker logs <container-id>

# Example
Running on http://localhost:9000
```

Test
To test your app, get the port of your app that Docker mapped:
```
sudo docker ps

__OUTPUT__
CONTAINER ID        IMAGE      COMMAND       CREATED             STATUS         PORTS      NAMES
80044ba82ff5        ubuntu     "/bin/bash"   9 seconds ago       Up 8 seconds              mad_fermat

```

To kill any Docker instance
```
sudo docker kill ecc
```
