# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "centos/8"

  config.vm.network "private_network", ip: "192.168.24.10"

  config.vm.provider :kvm do |kvm, override|
    kvm.memory_size = 4096
    kvm.cpus = 2
    kvm.gui = false
  end

  # SSH settings
  config.ssh.insert_key = false # Always use Vagrants insecure key
  config.ssh.forward_agent = true

  # Synced folders
  # config.vm.synced_folder ".", "/vagrant", 
  #   enabled: true,
  #   nfs: true,
  #   linux__nfs_options: ['rw','no_root_squash']

  # Start by updating the packages.
  config.vm.provision "shell", inline: <<-SHELL
    dnf update -y
  SHELL
end
