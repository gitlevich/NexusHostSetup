# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"
  
  config.vm.network "private_network", ip: "192.168.50.6"

  config.vm.provider "virtualbox" do |v|
    v.memory = 2048
  end

  config.vm.define "relay-nexus" do |machine|
    machine.vm.hostname = "relay-nexus"
  end

  config.vm.provision "ansible" do |ansible|
    ansible.extra_vars = { ansible_ssh_user: 'vagrant' }
    ansible.groups = {
      "nexus.development" => ["relay-nexus"]
    }
    ansible.playbook = "nexus.yml"
  end
end
