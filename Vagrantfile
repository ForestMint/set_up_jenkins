# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-24.04"
  config.vm.box_version = "202502.21.0"

  config.vm.define "host1" do |host1|
    host1.vm.network :private_network, ip: "192.168.56.20"
    host1.vm.hostname = "host1"
  end


  config.vm.provision "shell", inline: <<-SHELL
  cat <<EOF > /home/vagrant/my_script.sh
#!/bin/bash
sudo apt install -y wget apt-transport-https gpg

sudo apt update

wget -O - https://packages.adoptium.net/artifactory/api/gpg/key/public | sudo apt-key add -

echo "deb https://packages.adoptium.net/artifactory/deb $(awk -F= '/^VERSION_CODENAME/{print$2}' /etc/os-release) main" | sudo tee /etc/apt/sources.list.d/adoptium.list

sudo apt update # update if you haven't already

yes Y | sudo apt install temurin-21-jdk

sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key

echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null

sudo apt-get update

yes Y | sudo apt-get install jenkins

EOF

  chmod +x /home/vagrant/my_script.sh
SHELL


end
