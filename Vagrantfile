# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
    
  config.ssh.insert_key = false

  config.vm.define "centos" do |centos|
    centos.vm.box="venceslav_dimitrov/centos-stream-8"
    centos.vm.hostname = "centos.m6.hw"
    centos.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "4096"]
      vb.name = "NODE_M6"
    end
    centos.vm.network "private_network", ip: "192.168.99.11"
    centos.vm.synced_folder "prom", "/home/vagrant/prom"
    centos.vm.provision "shell", path: "add_hosts.sh"
    centos.vm.provision "shell", path: "addons_centos.sh"
    centos.vm.provision "shell", path: "centos_firewall_setup.sh"
    centos.vm.provision "shell", path: "docker-setup_centos.sh"
    centos.vm.provision "shell", path: "deploy_stack.sh"
  end

end
