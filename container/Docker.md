# What is Container?
* OS-level virtualization, a server virtualization method where the Kernal of OS allows multiple isolated user space instances, such instances are often called containers.
* Duplicate copy of an OS run in a virtual resource space on a system.

# Why should I use it ?
* Faster than Virtual Machine.
* Soft memory, loads application directly on memory.
* Crash Management, can kill a container quick and start another one.
* Limit DDOS, if 1 instance is down start another instance quickly.
* Better security, limit attack space, kill compromised, snap-shot replace.
* Don't leave idle instances and can be scale.

# What is Docker?
* Provides standard container technology to put your application into hosted on whatever type of environment server or services that you need to hosted in.

# Advantage
* Huge community, dev & dev-ops.
* Open source project and written in Google's Go language.
* Lots of Dockerized apps.
* Works well with Chef, Puppet, OpenStack, AWS, Azure, Rackspace.

# Commands

Know your Linux Kernal version
```
apt-cache search linux-headers-$(uname -r)
```

Upgrade your linux-header version
```
sudo apt-get install linux-image-generic-lts-raring linux-headers-generic-lts-raring
```

Get gpg key
```
sudo sh -c "wget -q0- https://get.docker.io/gpg | apt-key add -"
```
