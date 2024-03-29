## yacreader-appimager

Scripting my way to building an appimage of yacreader.

* https://yacreader.com
* https://github.com/YACReader/yacreader/blob/develop/INSTALL.md

## STATUS

This does not yet actually do anything else but grab a vagrant box and update its packages and install some basic tooling.

## SSH variables

There's a file `ansible/vars/ssh.yml.example` which you are supposed to copy into `ansible/vars/ssh.yml`. The values in example file should be fitting for vagrant. In case you need to run the build somewhere else, you can edit those values.

## Requirements

* Linux system, unless you want to do the legwork for this run in Windows/Mac. Seeing as this whole thing exists in order to create Linux AppImages, I gather it wouldn't be an onerous requirement. Also, I only have a Linux system available to me to work on this, so I can't really test other platforms... 

Likely, a recentish (upstream) version of: 

* vagrant with vagrant-libvirt plugin and all that jazz
    * You'll probably want to install kvm/libvirt stuff onto your linux. `virt-manager` should do the trick for ubuntu 18.04
    * Why not virtualbox? Well, performance and more importantly, [this](https://github.com/chocolatey-community/chocolatey-coreteampackages/issues/1145).
* ansible (I use 2.9.2 as of this writing)

## Usage:

1. `$ vagrant up` (You'll have to wait a bit for the package manager to update)
2. `$ ansible-playbook -i ansible/inventory.ini ansible/playbook.yml` (accept the host key for the first time you run it)

If you destroy the vm and create it again, it'll shout nasty things about changed host key. Don't panic, read the message carefully and then clean the old key away from `~/.ssh/known_hosts` as instructed in the message. 
