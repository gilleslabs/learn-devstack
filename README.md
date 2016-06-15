# Vagrant learn-devstack

Vagrant learn-devstack creates ready-to-go [Devstack All-In-One] (http://docs.openstack.org/developer/devstack/) VM.

Devstack is ideal to have an [Openstack] (http://www.openstack.org/) PoC/Demo environment

Openstack services installed in learn-devstack

+ **Horizon**
+ **Nova**
+ **Neutron**
+ **Glance**
+ **Cinder**

## Requirements

- [VirtualBox](https://www.virtualbox.org/wiki/Downloads). Tested on 5.0.20, but should also work on 5.0.20+ release.
- [Vagrant](http://www.vagrantup.com/downloads.html). Tested on 1.7.4

The VM is provisioned using ubuntu/trusty64 (Ubuntu 14.04 Trusty Tahr) from [atlas.hashicorp.com] (https://atlas.hashicorp.com/ubuntu/boxes/trusty64) images, thus your workstation must have a direct internet access. 

## VMs details

VM | vCPU/vRAM | IP Address| user/password | root / Administrator password |
---|---|---|---|---|
**devstack** | 4vCPU/4096MB | 192.168.99.11 | vagrant/vagrant | vagrant |
+ **Recommended hardware :** Computer with Multi-core CPU and 8GB+ memory

## Installation

#### Getting started:

Run the commands below:

	git clone https://github.com/gilleslabs/learn-devstack
	cd learn-devstack


###### Launching Devstack ready-to-go VM:

1. Run the command below:

	```
	vagrant up
	```

2. The setup will take some time to finish (approximatively 30 minutes depending on your hardware and Internet connection speed). Sit back and enjoy!

3. When the setup is done you can browse Openstack Horizon at **http://192.168.99.11/**

######Devstack credentials

User | Password |
---|---|
admin | cloud |
demo | cloud |



## Know issues


## Credits

This project was totally inspired from [Devstack Single-Machine](http://docs.openstack.org/developer/devstack/guides/single-machine.html)


## MIT

Copyright (c) 2016 Gilles Tosi

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE
