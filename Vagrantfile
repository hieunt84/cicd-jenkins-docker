# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  # make vm node1 - master
  config.vm.define "node1" do |node|
    node.vm.box = "generic/centos7"
    node.vm.box_check_update = false
    # node.vbguest.auto_update = false
    node.vm.hostname = "node1"
    node.vm.network "private_network", ip: "172.16.10.100"
    node.vm.provision "shell", path: "setup.sh"   
  end                  
                  
end