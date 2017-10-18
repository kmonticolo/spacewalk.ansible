# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "scalefactory/centos7"
  config.vm.network "public_network"
  config.vm.provider "virtualbox" do |vb|
     vb.memory = "6024"
  end
  config.vm.provision "shell", inline: <<-SHELL
  which ansible || yum -y install ansible
  which git || yum -y install git
  git clone https://github.com/kmonticolo/spacewalk.ansible.git
  cat >hosts<<EOF
  [spacewalk-server]
  localhost
EOF
  ansible-playbook spacewalk.ansible/spacewalk.yml -i hosts -c local
SHELL
end
