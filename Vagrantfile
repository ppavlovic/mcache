# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

    config.vm.box = "ubuntu/trusty64"

    config.vm.hostname = "mcache"

    config.vm.network "private_network", ip: "192.168.32.12"

    config.vm.synced_folder "./", "/vagrant_data"

    config.vm.provider "virtualbox" do |vb|
        vb.memory = 1024
        vb.cpus = 2
    end

    config.berkshelf.enabled = true

    config.berkshelf.berksfile_path = './cookbooks/engine/Berksfile'

    config.vm.provision "infra", type: "chef_solo" do |chef|
        chef.channel = "stable"
        chef.version = "12.10.24"
        chef.add_recipe 'apt'
        chef.add_recipe 'engine'
        chef.add_recipe 'engine::php5'
    end

end
