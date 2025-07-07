# Set up Jenkins


## 📜 Prerequisites
🇻 Have Vagrant installed on your host (e.g. version 2.4.7)\
🌐 Have your host machine connected to the Internet


## 💻 On your host machine

### 🚀 Start the virtual machine
```bash
vagrant up
```

### 👨‍💻 Vagrant SSH into the virtual machine
```bash
vagrant ssh
```


## 📦 On you box

install SSH and setup account
```bash
(sudo apt-get install sshpass) && (sudo useradd -m alfredo) && (sudo passwd alfredo) && (sudo usermod -aG sudo alfredo)
```

## On your host machine 

ssh alfredo@192.168.56.20

check /var/lib/jenkins/secrets/initialAdminPassword for the initial admin password
```bash
sudo chmod 777 /var/lib/jenkins/secrets/initialAdminPassword

sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```


open a tunnel to the Internet for webhooks
```bash
ngrok config add-authtoken <your-auth-token> # add authentication token

ngrok http 8080 # to expose Jenkins running on port 8080
# this command will show a public HTTPS URL like https://7a45-176-149-217-153.ngrok-free.app/
```

## 💻 On any client machine

open you favorite browser and type in the seqrch bar the public HTTPS URL displayed by ngrok

type the password previously displayed to unlock your aceess to your Jenkins server
