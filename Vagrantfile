# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "minimal/centos7"
  # config.vm.box = "centos/7"

  config.vm.provider :virtualbox do |virtualbox|
    virtualbox.customize ["modifyvm", :id, "--usb", "on"]
    virtualbox.customize ["modifyvm", :id, "--usbehci", "off"]
    virtualbox.customize ["modifyvm", :id, "--memory", 1024]
    virtualbox.customize ["modifyvm", :id, "--cpus", 1]
    # virtualbox.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    # virtualbox.customize ["modifyvm", :id, "--ioapic", "on"]
  end

  config.vm.define "test" do |machine|
    machine.vm.network "forwarded_port", guest: 80, host: 8080
    machine.vm.hostname = "test"
    machine.vm.network :private_network, ip: "192.168.2.2"
    machine.ssh.insert_key = false
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "bootstrap.yml"
  end
end
