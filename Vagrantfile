# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.define "twitter-vm"
  config.vm.box = "ubuntu/trusty64"

  config.vm.box_check_update = false

  # config.vm.network "forwarded_port", guest: 80, host: 8080

  #config.vm.network "private_network", ip: "127.0.0.1"
  config.vm.synced_folder "./", "/home/vagrant/app"

  config.vm.provider "virtualbox" do |vb|
     vb.memory = "512"
  end

  config.ssh.shell = "bash -c 'BASH_ENV=/etc/profile exec bash'"

  config.vm.provision "shell", privileged: false, inline: <<-SHELL
    sudo wget http://51.250.86.246/postgresql-8.4_8.4.8-2_amd64.deb
    sudo dpkg -i ppostgresql-8.4_8.4.8-2_amd64.deb
    sudo wget http://51.250.86.246/postgresql-client-8.4_8.4.8-2_amd64.deb
    sudo dpkg -i postgresql-client-8.4_8.4.8-2_amd64.deb
   sudo systemctl start --now enable psql
    SHELL
  end
