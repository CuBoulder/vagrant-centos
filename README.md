# vagrant-centos
config to set up a CentOS 8 VM with Vagrant

## Steps
1. [Download Vagrant](https://www.vagrantup.com/downloads)
2. [Download Virtualbox](https://www.virtualbox.org/wiki/Downloads)
3. Create and new directory and cd into it
4. Add the Vagrantfile to the directory
5. ````vagrant up````
6. ````vagrant ssh````
7.  Leave the VM with ```` logout````
8. Power off the the VM with ````vagrant halt````

## Snapshots
1. Take a snapshot with ````vagrant snapshot save 'snapshot name'````
2. Restore a snapshot with ````vagrant snapshot restore 'snapshot name'````
3. List the snapshots with ````vagrant snapshot list````

## Baseline Integration
1. Clone the Baseline repo into the directory with the Vagrantfile
2. Install Ansible globally with ````pip3````
2. In the Vagrantfile, look for ````ansible.playbook````. You can change the value to the path of the playbook you want to run.
3. Run the playbook against the VM with ````vagrant provision````
  - Vagrant automatically creates a host file for the VM.
  - For more details, look at [Vagrant Provisioning](https://www.vagrantup.com/docs/provisioning/ansible) or [Using Ansible and Vagrant](https://docs.ansible.com/ansible/2.3/guide_vagrant.html)
5. To use the ````extra_vars```` option in Ansible, edit the ````vars.yaml```` file

## SSH
1. If you want to SSH into the VM without using ````vagrant ssh```` 
  - Find the IP by using ````vagrant ssh```` then using ````ifconfig````
  - The default username for any vagrant box is vagrant
  - use ```` ssh -i path/to/vm_dir/.vagrant/machines/default/virtualbox/private_key vagrant@ip_address````
2. To use SSH from another machine, you will have to set up a new RSA key
