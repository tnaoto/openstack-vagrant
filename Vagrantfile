# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

# https://ask.openstack.org/en/question/9487/packstack-allinone-vagrant-setup-how-to-pass-in-root-password/

$script = <<SCRIPT
sudo yum install -y http://rdo.fedorapeople.org/rdo-release.rpm
sudo yum install -y openstack-packstack expect

expect << EOF
set timeout -1
spawn "/usr/bin/packstack" "--answer-file=/vagrant/answerfile"
expect "Setting up ssh keys...root@192.168.65.11's password:"
send "vagrant\n"
expect eof
EOF

SCRIPT

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "CentOS65" # with LVM vol for cinder-volumes 
  config.vm.network "private_network", ip: "192.168.65.11"
  config.vm.provider :virtualbox do |vb|
     vb.customize ["modifyvm", :id, "--memory", "4096"]
  end
  config.vm.provision "shell", inline: $script
end
