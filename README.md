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

VBoxManage guestproperty enumerate <Jenkins-server-name>
```

ping the IP address to check it reponds
```bash
ping <Jenkins-server-IP>
```

open you favorite browser and go to http://Jenkins-server-IP:8080

type the password previously displayed to unlock your aceess to your Jenkins server
