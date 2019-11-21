# -*- mode: ruby -*-
# vi: set ft=ruby :

TEST1_IP               = '192.168.56.101'
OS                      = "ubuntu/bionic64"

Vagrant.configure("2") do |config|

  config.ssh.insert_key = true

# define TEST1 server
  config.vm.define "test1" do |test1|
    test1.vm.hostname = "machine-test1"
    test1.vm.box = OS
    test1.vm.network "private_network", ip: TEST1_IP
    test1.vm.provider "virtualbox" do |v|
      v.name = "test1"
      v.cpus = 4
      v.memory = 8192
    end
    config.vm.provision "file", source:"~/.ssh/id_rsa.pub", destination:"~/.ssh/authorized_keys"
  end

end
