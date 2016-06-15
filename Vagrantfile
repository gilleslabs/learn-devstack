# -*- mode: ruby -*-
# vi: set ft=ruby :

################################################################################################################
#                                                                                                              #
# Vagrantfile for provisioning ready-to-go  All-In-One Devstack VM                                             #
#                                                                                                              #
# Author: Gilles Tosi                                                                                          #
#                                                                                                              #
# The up-to-date version and associated dependencies/project documentation is available at:                    #
#                                                                                                              #
# https://github.com/gilleslabs/learn-devstack                                                                 #
#                                                                                                              #
################################################################################################################



######################################################################################################
#                                                                                                    #
#      Setup of $devstack variable which will be used for devstack VM Shell inline provisioning      #
#                                                                                                    #
######################################################################################################




$devstack = <<DEVSTACK
echo "Build start at    :" > /tmp/build
date >> /tmp/build 

################     Installing pre-requisites            ###################

sudo apt-get update
sudo ip link set dev eth2 up

apt-get install sudo -y
echo "vagrant ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers
sudo apt-get install git -y
sudo -i -u vagrant git clone https://git.openstack.org/openstack-dev/devstack
sudo -i -u vagrant cd devstack

###############  Configuring local.conf file for stack.sh shell ###############

sudo -i -u vagrant touch /home/vagrant/devstack/local.conf
sudo -i -u vagrant chmod 664 /home/vagrant/devstack/local.conf
echo "[[local|localrc]]" >> /home/vagrant/devstack/local.conf

echo "ADMIN_PASSWORD=cloud" >> /home/vagrant/devstack/local.conf
echo "DATABASE_PASSWORD=iheartdatabases" >> /home/vagrant/devstack/local.conf
echo "RABBIT_PASSWORD=flopsymopsy" >> /home/vagrant/devstack/local.conf
echo "SERVICE_PASSWORD=iheartksl" >> /home/vagrant/devstack/local.conf
echo "HOST_IP=192.168.99.11" >> /home/vagrant/devstack/local.conf
echo "SERVICE_HOST=$HOST_IP" >> /home/vagrant/devstack/local.conf
echo "disable_service n-net" >> /home/vagrant/devstack/local.conf
echo "enable_service q-svc" >> /home/vagrant/devstack/local.conf
echo "enable_service q-agt" >> /home/vagrant/devstack/local.conf
echo "enable_service q-dhcp" >> /home/vagrant/devstack/local.conf
echo "enable_service q-l3" >> /home/vagrant/devstack/local.conf
echo "enable_service q-meta" >> /home/vagrant/devstack/local.conf
echo "enable_service neutron" >> /home/vagrant/devstack/local.conf

echo "Q_USE_SECGROUP=True" >> /home/vagrant/devstack/local.conf
echo "FLOATING_RANGE=192.168.0.0/24" >> /home/vagrant/devstack/local.conf
echo "Q_FLOATING_ALLOCATION_POOL=start=192.168.0.224,end=192.168.0.254" >> /home/vagrant/devstack/local.conf
echo "PUBLIC_NETWORK_GATEWAY=192.168.0.1" >> /home/vagrant/devstack/local.conf
echo "PUBLIC_INTERFACE=eth2"


##############       Installing Devstack                         ###############

sudo -i -u vagrant /home/vagrant/devstack/stack.sh
sudo ovs-vsctl add-port br-ex eth2
echo "Build completed at      :" >> /tmp/build
date >> /tmp/build
cat /tmp/build
DEVSTACK


Vagrant.configure(2) do |config|

	config.vm.define "devstack" do |devstack|
        devstack.vm.box = "ubuntu/trusty64"
			config.vm.provider "virtualbox" do |v|
				v.cpus = 4
				v.memory = 4096
				v.customize ["modifyvm", :id, "--ioapic", "on"]
				v.customize ["modifyvm", :id, "--nicpromisc3", "allow-all"]
			end
        devstack.vm.network "private_network", ip: "192.168.99.11"
		devstack.vm.network "public_network", ip: "192.168.0.51"
		devstack.vm.provision :shell, inline: $devstack
    end
end