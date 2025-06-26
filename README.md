# Set up Jenkins


## 📜 Prerequisites
🇻 Have Vagrant installed on your host (e.g. version 2.4.7)\
🌐 Have your host machine connected to the Internet


## 💻 On your host machine

### 🚀 Start the virtual machine
```bash
vagrant up
```

### 👨‍💻 SSH into the virtual machine
```bash
vagrant ssh
```


## 📦 On you box

### ☕ Install Java

```bash
lsb_release -a # check that the OS distribution is Ububtu 24.04

sudo apt install -y wget apt-transport-https gpg

sudo apt update

wget -O - https://packages.adoptium.net/artifactory/api/gpg/key/public | sudo apt-key add -

echo "deb https://packages.adoptium.net/artifactory/deb $(awk -F= '/^VERSION_CODENAME/{print$2}' /etc/os-release) main" | sudo tee /etc/apt/sources.list.d/adoptium.list

sudo apt update # update if you haven't already

sudo apt install temurin-21-jdk

java -version
```

### 🤵🏻 Install Jenkins

```bash
sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key

echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null

sudo apt-get update

sudo apt-get install jenkins

systemctl cat jenkins

systemctl --full status jenkins

jenkins --version
```

check /var/lib/jenkins/secrets/initialAdminPassword for the initial admin password
```bash
sudo chmod 777 /var/lib/jenkins/secrets/initialAdminPassword

sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```


## 💻 Back to your host machine

### 🤵🏻 Find the IP of the server and connect to Jenkins

set the network Adapter 1 to 'Attached to : Bridge Adapter' for your Jernkins server in virtualbox

find the IP in the variable /VirtualBox/GuestInfo/Net/0/V4/IP

```bash
vboxmanage list runningvms # display information about the running VMs

VBoxManage guestproperty enumerate <Jenkins-server-IP>
```

ping the IP address to check it reponds
```bash
ping <Jenkins-server-IP>
```

open you favorite browser and go to http://Jenkins-server-IP:8080

