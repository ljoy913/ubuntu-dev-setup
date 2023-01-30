# Ubuntu Dev Setup

Install scripts for Ubuntu dev environment

<br>

Ubuntu 18 VM Developer Setup  
- Installs Node.js 
- Installs latest Git
- Installs Docker
- Installs Java Runtime

<br>

## Update packages

```
# Apt Update one-liner
sudo apt update -y && sudo apt full-upgrade -y && sudo apt autoremove -y && sudo apt clean -y && sudo apt autoclean -y
```


## Install Node & NVM
```
# Install  NVM
curl https://raw.githubusercontent.com/creationix/nvm/master/install.sh | bash 

# Reload your profile to enable nvm
. ~/.profile

# Check version
nvm -v

# Install Node.js LTS
nvm install --lts

# Check version
node -v

# (Optional) Update npm
npm install npm@latest -g

# Check version
npm -v
```


## Install latest Git

```
# Add git repository
sudo add-apt-repository ppa:git-core/ppa -y
sudo apt update

# Install git
sudo apt install git -y

# Check version
git --version
```


## Install Docker

```
# Required apps. Ubuntu 18 already has all these:
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release

# Install Docker PGP key
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

# Add Docker repository
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Install Docker apps
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io

# Test installation with Hello World image (to test that docker works)
sudo docker run hello-world 

# Remove the Hello World image
sudo docker image rm -f hello-world

# Check version
docker -v

# Docker will require sudo to use unless you add yourself to the docker group. newgrp will apply the changes in the current session
sudo usermod -aG docker $USER; newgrp docker

# Should you want to remove the user from the docker group.
sudo deluser $USER docker;
```


## Install Java Runtime

```
# Install Java Runtime (JRE)
sudo apt install -y default-jre

# Check version
java --version

# Alternate, install 17
sudo apt install -y openjdk-17-jre
```
