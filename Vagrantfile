# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/xenial64"

  config.vm.network "public_network"

  #Configure VM
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
    vb.cpus = 2
  end

  #Install and start stable Clickhouse version with default config
  config.vm.provision "shell", inline: <<-SHELL
    apt update
    apt install -y dirmngr
    apt-key adv --keyserver keyserver.ubuntu.com --recv E0C56BD4
    echo "deb http://repo.yandex.ru/clickhouse/deb/stable/ main/" | sudo tee /etc/apt/sources.list.d/clickhouse.list
    apt update
    apt install -y clickhouse-server clickhouse-client
    service clickhouse-server start
  SHELL
end
