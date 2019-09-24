# -*- mode: ruby -*-
# vi: set ft=ruby :


Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/trusty64"
   
   config.vm.hostname = "DockerMachine"

   config.vm.network "private_network", ip: "192.168.33.19"

   config.vm.provider "virtualbox" do |vb|
     vb.gui = true
     vb.memory = "2048"
   end

   config.vm.provision "shell", inline: <<-SHELL
     apt-get update
     apt-get install \
     apt-transport-https \
     ca-certificates \
     curl \
     software-properties-common -y
     curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
     apt-key fingerprint 0EBFCD88
     add-apt-repository \
     "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
     $(lsb_release -cs) \
     stable"
     apt-get update
     apt-get install docker-ce -y
     usermod -aG docker vagrant
   SHELL

   config.push.define "ftp" do |push|
     push.host = "ftp.company.com"
     push.username = "kenanhancer"
   end
end
