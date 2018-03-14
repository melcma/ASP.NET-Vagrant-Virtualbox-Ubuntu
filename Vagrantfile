# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-16.04"

  config.vm.provider :virtualbox do |v|
    v.memory = 2048
    v.linked_clone = true
  end

  config.vm.define "aspnet" do |aspnet|
     aspnet.vm.hostname = "asp.net"
     aspnet.vm.network :private_network, ip: "192.168.100.4"
     aspnet.vm.network :forwarded_port, guest: 22, host: 2222, id: "ssh"
     aspnet.vm.network :forwarded_port, guest: 80, host: 8080, id: "localhost"

     aspnet.vm.network :forwarded_port, guest: 8001, host: 8001, host_ip: "127.0.0.1", auto_correct: false

     aspnet.vm.synced_folder "www/", "/var/www"
   end

   config.vm.provision "shell", inline: <<-SHELL
     apt-get update
     curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
     mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
     sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-xenial-prod xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
     apt-get install apt-transport-https -y
     apt-get update
     apt-get install dotnet-sdk-2.1.101 -y
   SHELL
end
