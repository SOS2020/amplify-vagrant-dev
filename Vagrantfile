# -*- mode: ruby -*-
# vi: set ft=ruby :
# NOTE: Variable overrides are in ./config.rb
require "yaml"
require "fileutils"

# Use a variable file for overrides:
CONFIG = File.expand_path("config.rb")
if File.exist?(CONFIG)
  require CONFIG
end

Vagrant.configure("2") do |config|

  config.vm.define "centos8vb" do |centos8vb|
    centos8vb.vm.box = $centos8_box
    centos8vb.vm.box_version = $centos8_box_ver
    centos8vb.ssh.username = $ssh_user
    centos8vb.ssh.host = $vb_private_ip
    #centos8vb.ssh.port = 22
    centos8vb.vm.synced_folder ENV['amplify_host_dir'], $vm_folder
    
    centos8vb.vm.network "private_network", ip: $vb_private_ip

    centos8vb.vm.provider "virtualbox" do |vb|
      vb.name = $vb_vm_name
      vb.cpus = $vcpus
      vb.memory = $vmem
      # Faster cloning and uses less disk space
      vb.linked_clone = false
    end

    # Provision box
    centos8vb.vm.provision "file", source: "ansible", destination: "/tmp/ansible"

    centos8vb.vm.provision "shell", path: "ansible/ansible.sh"

    centos8vb.vm.provision "shell", inline: "npm install -g @aws-amplify/cli"

  end
  
end