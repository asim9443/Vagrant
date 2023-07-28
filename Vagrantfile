 # -*- mode: ruby -*-
# vi: set ft=ruby :
 
 
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/jammy64"

  config.vm.define "nginx-proxy" do |nxp|
    nxp.vm.hostname = "nginx-proxy"
    nxp.vm.network "private_network", ip: "100.100.100.100"
    nxp.vm.network "forwarded_port", guest: 80, host: 4000
    nxp.vm.network "forwarded_port", guest: 80, host: 4000, host_ip: "127.0.0.1"
    nxp.vm.synced_folder ".", "/vagrant"
    nxp.vm.provision "shell", path:"./install-nginx.sh"
      nxp.vm.provider "virtualbox" do |vb|
        vb.name = "nginx-proxy"
        vb.memory = "1024"
        vb.cpus = 1
        vb.gui = true 
      end    
  end
  config.vm.define "blue-environment" do |blue|
      blue.vm.hostname = "blue"
      blue.vm.network "private_network", ip: "100.100.100.101"
      blue.vm.network "forwarded_port", guest: 80, host: 5000
      blue.vm.network "forwarded_port", guest: 80, host: 5000, host_ip: "127.0.0.1"
      blue.vm.synced_folder ".", "/vagrant"
      blue.vm.provision "shell", path:"./install-docker.sh"
        blue.vm.provider "virtualbox" do |vb|
          vb.name = "blue-environment"
          vb.memory = "1024"
          vb.cpus = 1
          vb.gui = true 
      end    
  end
  config.vm.define "green-environment" do |green|
      green.vm.hostname = "green"
      green.vm.network "private_network", ip: "100.100.100.102"
      green.vm.network "forwarded_port", guest: 80, host: 6000
      green.vm.network "forwarded_port", guest: 80, host: 6000, host_ip: "127.0.0.1"
      green.vm.synced_folder ".", "/vagrant"
      green.vm.provision "shell", path:"./install-docker.sh"
        green.vm.provider "virtualbox" do |vb|
          vb.name = "green-environment"
          vb.memory = "1024"
          vb.cpus = 1
          vb.gui = true 
      end    
  end
end


