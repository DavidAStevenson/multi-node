# -*- mode: ruby -*-
# vi: set ft=ruby :

# Box image for each node, including the master
BOX_IMAGE = "bento/centos-7.5"
# How many nodes to create, in addition to the master 
NODE_COUNT = 2
# Virtualbox specs
MEMORY = 256
CPUS = 1

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|

  config.vm.box = BOX_IMAGE

  config.vm.provider "virtualbox" do |v|
      v.memory = MEMORY
      v.cpus = CPUS
  end

  config.vm.define "master", primary: true do |master|
      master.vm.hostname = "master"
      master.vm.network "private_network", ip: "192.168.33.10"
      master.vm.provider "virtualbox" do |v|
          v.memory = 2*MEMORY
      end
  end

  (1..NODE_COUNT).each do |i|
      config.vm.define "node#{i}" do |node|
          node.vm.hostname = "node#{i}"
          node.vm.network "private_network", ip: "192.168.33.#{i+10}"
      end
  end
  
end
