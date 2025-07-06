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
open a tunnel to the Internet for webhooks
```bash
sudo apt update && sudo apt install unzip -y #install unzip

wget https://bin.equinox.io/c/bNyj1mQVY4c/ngrok-stable-linux-amd64.zip # download the .zip file from the web

unzip ngrok-stable-linux-amd64.zip

sudo mv ngrok /usr/local/bin

ngrok config add-authtoken <your-auth-token> # add authentication token

ngrok http 8080 # to expose Jenkins running on port 8080
# this command will show a public HTTPS URL like https://7a45-176-149-217-153.ngrok-free.app/
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
