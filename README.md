# Getting started
Your basic setup files are ready to go.  Startup vagrant in our favourite way.
`vagrant up`

# Modify and testing the provisioning script
If you decide you want to make some changes to playbook/vagrant.yml and you want to test it, you may do so with:
`vagrant provision`
or using ansible:
`ansible-playbook -i vagrant_ansible_inventory_default --verbose --user=vagrant --private-key=~/.vagrant.d/insecure_private_key playbook/vagrant.yml`

A full test would be to destroy the virtual machine with the command:
`vagrant destroy`
so it can re-create it from scratch and run the playbook/vagrant.yml again
`vagrant up`
