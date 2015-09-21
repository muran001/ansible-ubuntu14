# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.define :webserver1 do |node|
    node.vm.box = "ubuntu/trusty64"
    # node.vm.network "forwarded_port", guest: 80, host: 8080
    node.vm.network "private_network", ip: "192.168.33.10"
    # node.vm.synced_folder "../data", "/vagrant_data"
    node.vm.provider "virtualbox" do |vb|
      vb.memory = "2048"
    end
    node.vm.provision "ansible" do |ansible|
      ansible.playbook = "playbook.yml"
      ansible.inventory_path = "hosts"
      ansible.limit = "webservers"
    end
  end
  config.vm.define :dbserver1 do |node|
    node.vm.box = "ubuntu/trusty64"
    # node.vm.network "forwarded_port", guest: 80, host: 8080
    node.vm.network "private_network", ip: "192.168.33.20"
    # node.vm.synced_folder "../data", "/vagrant_data"
    node.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
    end
    node.vm.provision "ansible" do |ansible|
      ansible.playbook = "playbook.yml"
      ansible.inventory_path = "hosts"
      ansible.limit = "dbservers"
    end
  end
end
