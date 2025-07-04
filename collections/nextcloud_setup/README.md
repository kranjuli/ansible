# Ansible collection nextcloud_setup

Install nextcloud on Raspberry Pi
The collection can be downloaded at github

## Ansible roles

* debian_os_upgrade: run os upgrade on raspberry pi
* mounting: create mount point for nextcloud config file and database
* nextcloud: install and setup nextcloud

## Ansible playbook

Nextcloud can be installed with the playbook `install_nextcloud`

````shell
# install collection
ansible-galaxy collection install <path_to_nextcloud_setup_collection> --force 

ansible-playbook -i 192.168.4.218 krankjuli.nextcloud_setup.install_nextcloud.yml
````

