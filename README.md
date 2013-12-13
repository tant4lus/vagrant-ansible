# Purpose
This is an easy example of getting started with Vagrant and Ansible.  It's great for any beginner who has installed Ansible and Vagrant to learn by example, to see vagrant create a VM and run Ansible to immediately set up the environment with dependencies right after.

# Getting started
## Requirements
Only tested on Mac OS X!  That's what I ran it on. There are no warranties or assurance that this will work on your system.  Windows systems may need to modify the file paths accordingly.

## Let's go already
Your basic setup files are ready to go.  Startup vagrant in our favourite way.
```
vagrant up
```

# Modify and test Ansible script
If you decide you want to make some changes to playbook/vagrant.yml and you want to test it, you may do so with:
```
vagrant provision
```
or using ansible:
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

Happy learning!
