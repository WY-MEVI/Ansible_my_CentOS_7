# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.vm.define "host" do |node|
    node.vm.box = "bento/centos-7.2"
    node.vm.hostname = "host"
    node.vm.network :private_network, ip: "192.168.52.51"
	    # Run Ansible from the Vagrant VM
    node.vm.provision :ansible_local do |ansible|
      ansible.playbook       = "provision/playbook.yml"
      ansible.verbose        = true
      ansible.install        = true
      ansible.install_mode   = :default
      ansible.limit          = "all" # or only "nodes" group, etc.
      ansible.inventory_path = "provision/inventory"
    end
  end
end
