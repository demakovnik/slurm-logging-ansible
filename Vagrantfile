# -*- mode: ruby -*-
# vi: set ft=ruby :
 
# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
    config.vm.provision "file", 
    source: "ansible/ssh-keys/ansible.pub", 
    destination: "/home/vagrant/.ssh/"

    config.vm.define "controlnode" do |controlnode|
      controlnode.vm.provider "virtualbox" do |vb|
      # Display the VirtualBox GUI when booting the machine
      vb.gui = false
      # Customize the amount of memory on the VM:
      vb.memory = "4096"
      vb.cpus = 1
    end
    controlnode.vm.box = "bento/ubuntu-22.04"
    controlnode.vm.hostname = "controlnode"
    controlnode.vm.synced_folder "./ansible","/home/vagrant/ansible"
    controlnode.vm.network "public_network", ip: "192.168.0.201"
    controlnode.vm.provision "shell", inline: <<-SHELL
       cat /home/vagrant/.ssh/ansible.pub >> /home/vagrant/.ssh/authorized_keys
       apt-add-repository ppa:ansible/ansible -y
       apt update -y
       apt install -y ansible
  SHELL
  end
  
    config.vm.define "monitoring" do |monitoring|
      monitoring.vm.provider "virtualbox" do |vb|
        # Display the VirtualBox GUI when booting the machine
        vb.gui = false
        # Customize the amount of memory on the VM:
        vb.memory = "4096"
        vb.cpus = 1
      end
      monitoring.vm.box = "bento/ubuntu-22.04"
      monitoring.vm.hostname = "monitoring"
      monitoring.vm.network "public_network", ip: "192.168.0.202"
      monitoring.vm.provision "shell", inline: <<-SHELL
         cat /home/vagrant/.ssh/ansible.pub >> /home/vagrant/.ssh/authorized_keys
    SHELL
    end
  end
  
