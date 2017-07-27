# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  config.vm.define "centos" do |centos|
    centos.vm.box = "centos/7"
    centos.vm.hostname = "centos.dev.local"
    centos.vm.network "private_network", ip: "192.168.140.140"
    centos.vm.network "forwarded_port", guest: 389, host: 3389
    centos.vm.provision :hosts, :sync_hosts => true
    centos.ssh.forward_x11 = true
    #, auto_config: false
  end

  config.vm.provision "ansible" do |ansible|
    ansible.verbose  = "vv"
    ansible.playbook = "site.yml"
    ansible.config_file = "ansible.cfg"
  end
 end
