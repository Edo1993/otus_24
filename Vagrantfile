# -*- mode: ruby -*-
# vim: set ft=ruby :

MACHINES = {

  :route1 => {
    :box_name => "centos/7",
    :net => [
              {adapter: 2, auto_config: false, virtualbox__intnet: "vlan10"},
              {adapter: 3, auto_config: false, virtualbox__intnet: "vlan30"},
              {ip: '10.10.10.1', adapter: 4, netmask: "255.255.255.0", virtualbox__intnet: "areaR1"},
            ]
  },
  :route2 => {
    :box_name => "centos/7",
    :net => [
              {adapter: 2, auto_config: false, virtualbox__intnet: "vlan10"},
              {adapter: 3, auto_config: false, virtualbox__intnet: "vlan20"},
              {ip: '10.20.20.1', adapter: 4, netmask: "255.255.255.0", virtualbox__intnet: "areaR2"},
            ]
  },

  :route3 => {
    :box_name => "centos/7",
    :net => [
              {adapter: 2, auto_config: false, virtualbox__intnet: "vlan20"},
              {adapter: 3, auto_config: false, virtualbox__intnet: "vlan30"},
              {ip: '10.30.30.1', adapter: 4, netmask: "255.255.255.0", virtualbox__intnet: "areaR3"},
            ]
  },
}

Vagrant.configure("2") do |config|

  MACHINES.each do |boxname, boxconfig|

    config.vm.define boxname do |box|

        box.vm.box = boxconfig[:box_name]
        box.vm.host_name = boxname.to_s

        config.vm.provider "virtualbox" do |v|
          v.memory = 512
        end

        boxconfig[:net].each do |ipconf|
          box.vm.network "private_network", ipconf
        end

        if boxconfig.key?(:public)
          box.vm.network "public_network", boxconfig[:public]
        end

        box.vm.provision "shell", inline: <<-SHELL
          mkdir -p ~root/.ssh
          cp ~vagrant/.ssh/auth* ~root/.ssh
          setenforce 0
        SHELL

      end

  end

  config.vm.provision "ansible" do |ansible|
  ansible.verbose = "vvv"
  ansible.playbook = "playbook_1.yml"
  ansible.become = "true"
  end

end
