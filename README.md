# Purpose
This is an easy example of getting started with Vagrant and Ansible.  It's great for any beginner who has installed Ansible and Vagrant to learn by example, to see vagrant create a VM and run Ansible to immediately set up the environment with dependencies right after.

# Getting started
## Requirements
Only tested on Mac OS X on a 2013 Macbook Air 11"!  That's what my computer is. There are no warranties or assurance that this will work on your system.  Windows systems may need to modify the file paths accordingly.
1. Git – to clone and forking this repository, although you could just download it as a zip file.
2. Ansible – if you do not a package you can easily install from a linux repo, it can be run standalone by cloning its repository here: https://github.com/ansible/ansible , changing to the `ansible` directory on your local disk then running `./hacking/env-setup` to setup your environment variables.
3. Vagrant – download from http://www.vagrantup.com

## Let's go already
1. Clone this repository to your computer.  Your basic setup files are ready to go.  
2. Startup vagrant in our favourite way.
```
vagrant up
```

## What just happened?
When you run the `vagrant up` vagrant goes through its `Vagrantfile` to begin creating a VM.  Below we have the section in which defines what type of operating system will be installed and the hostname that is given.  precise32 is a Ubuntu Linux variety but feel free to change it.  You can find a good listing of VirtualBox VM snapthos that can be used with Vagrant from http://www.vagrantbox.es
```
  config.vm.box = "precise32"
  config.vm.box_url = "http://files.vagrantup.com/precise32.box"
```

Next we ask Vagrant to setup port forwarding. If you run an application server, web server, database, it will map the VM port 8080 to port 3751 on your local machine.  This means that http://localhost:3751 on your physical machine will get forwarded to http://virtualmachine:8080.
```
  config.vm.network :forwarded_port, guest: 8080, host: 3751
  config.vm.network :forwarded_port, guest: 80, host: 3750
```


# Extending the Ansible script
So you want to install more packages, use some different Ansible modules.  Make some changes to start learning Ansible.
1. Fork this repository.
2. Make your changes to playbook/vagrant.yml 
3. Run vagrant's provisioning portion - which is when it calls Ansible (or Puppet or Chef).
```
vagrant provision
```
4. Optionally, you can also call ansible directly with the following command:
```
ansible-playbook -i vagrant_ansible_inventory_default --verbose --user=vagrant --private-key=~/.vagrant.d/insecure_private_key playbook/vagrant.yml
```


A full provisioning test would be to destroy the virtual machine with the command:
```
vagrant destroy
```
so it can re-create it from scratch and run the playbook/vagrant.yml again
```
vagrant up
```

-----

Do you need more examples?  Take a look at the official Ansible examples git repo: https://github.com/tant4lus/ansible-examples and you should now be able to run the examples using vagrant.

Happy learning!
