# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.ssh.insert_key = false
  #config.vm.synced_folder '.', '/vagrant', type: 'nfs'

  # VMware Fusion.
  # `vagrant up vmware --provider=vmware_fusion`
  config.vm.define "vmware" do |vmware|
    vmware.vm.hostname = "centos7-vmware"
    vmware.vm.box = "file://builds/vmware-ol7.box"
    vmware.vm.network :private_network, ip: "192.168.3.2"

    config.vm.provider :vmware_desktop do |v, override|
      v.gui = false
      v.vmx["memsize"] = 4096
      v.vmx["numvcpus"] = 2
    end

    config.vm.provision "shell", inline: "echo Hello, World"
  end

  # VirtualBox.
  # `vagrant up virtualbox --provider=virtualbox`
  config.vm.define "virtualbox" do |virtualbox|
    virtualbox.vm.hostname = "virtualbox-centos7"
    virtualbox.vm.box = "file://builds/virtualbox-ol7.box"
    virtualbox.vm.network :private_network, ip: "172.16.3.2"

    config.vm.provider :virtualbox do |v|
      v.gui = false
      v.memory = 4096
      v.cpus = 2
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--ioapic", "on"]
    end

    config.vm.provision "shell", inline: "echo Hello, World"
  end

end