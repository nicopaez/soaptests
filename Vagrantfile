# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = 'ubuntu/xenial64'

  config.vm.hostname = 'bpm-tests'
  config.vm.network 'forwarded_port', guest: 3000, host: 3000
  config.vm.provider 'virtualbox' do |vb|
    vb.memory = '1024'
    vb.name = config.vm.hostname
  end

  config.vm.provision 'shell', privileged: false, inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y build-essential git
    wget https://s3.amazonaws.com/downloads.eviware/soapuios/5.5.0/SoapUI-5.5.0-linux-bin.tar.gz
    sudo tar -xzf SoapUI-5.5.0-linux-bin.tar.gz -C /opt/
    sudo apt-get install -y default-jdk
  SHELL
end
