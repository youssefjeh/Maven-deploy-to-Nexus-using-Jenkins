
# Maven deploy to Nexus using Jenkins
Our goal is upload artifact into nexus server


## Steps

- Need to creat repos in nexus

- Need to integrate jenkins nexus

- Need to setup repo details in pom.xml maven

- Need to connect maven server to nexus server in settings.xml add nexus creds

- Need artifact into nexus server


## Installation

Install Docker on Ubuntu 

```bash
# Update the apt package index and install packages to allow apt to use a repository over HTTPS
  apt-get update
  apt-get install -y \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common

# Add Docker's official GPG key
  curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -

# Set up the stable Docker repository
  add-apt-repository \
    "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
    $(lsb_release -cs) \
    stable"

# Update the apt package index and install the latest version of Docker
  apt-get update
  apt-get install -y docker-ce

# Add the current user to the docker group
  usermod -aG docker $USER

# Start the Docker daemon
  systemctl start docker

```
Install Jenkins on Docker
```bash
docker run -p 8080:8080 -p 50000:50000 -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts
```
Install Maven on Ubuntu
```bash
sudo apt install maven
```
Install Nexus Repository Manager on Ubuntu

 - [How to Install Nexus Repository Manager on Ubuntu 22.04](https://www.howtoforge.com/how-to-install-nexus-repository-manager-on-ubuntu-22-04/)


