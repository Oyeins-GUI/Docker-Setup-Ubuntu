# **How to setup Docker for Clarinet Integrate in Ubuntu**
## System Requirements
- 4GB of RAM
- 64-bit operating system

## Uninstall Old Versions
```
$ sudo apt-get remove docker docker-engine docker.io containerd runc
```

## Uninstall Docker Engine
1. Uninstall the Docker Engine, CLI, containerd, and Docker Compose packages:Uninstall the Docker Engine, CLI, containerd, and Docker Compose packages:
```
$ sudo apt-get purge docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin docker-ce-rootless-extras
```
2. Images, containers, volumes, or custom configuration files on your host aren’t automatically removed. To delete all images, containers, and volumes:
```
$ sudo rm -rf /var/lib/docker
$ sudo rm -rf /var/lib/containerd
```
## Installation Steps
### Setup the Repository
1. Update the apt package index and install packages to allow apt to use a repository over HTTPS:
```
$ sudo apt-get update

$ sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```
2. Add Docker’s official GPG key:
```
$ sudo mkdir -m 0755 -p /etc/apt/keyrings
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```
3. Use the following command to set up the repository:
```
$ echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

### Install Docker Engine
1. Update the apt package index:
```
$ sudo apt-get update
```
2. Install Docker Engine, containerd, and Docker Compose.
```
$ sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
## Manage Docker as a non-root user
