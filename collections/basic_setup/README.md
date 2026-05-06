# Ansible Collection - kranjuli.basic_setup

Documentation for the collection `basic_setup`.

## Roles

### upgrade_debian_os_packages

The role `upgrade_debian_os_packages` will be used to upgrade debian os packages.

### shell

The role `shell` will be used to disable shell history.

## playbooks

* basic_setup_pi: basic setup for raspberry pi
* docker_pi: install docker on the pi
* github_repo_clone_pi: clone github repos to the pi

### Run playbook

```bash

# run playbook without install collection
ansible-playbook -i <ip_target_host>, ansible/collections/basic_stup/playbooks/basic_setup_pi.yml -u ansible --private-key <path_to_ssh_private_key>

ansible-playbook -i <ip_target_host>, ansible/collections/basic_stup/playbooks/docker_pi.yml -u ansible --private-key <path_to_ssh_private_key>

ansible-playbook -i <ip_target_host>, ansible/collections/basic_stup/playbooks/github_repo_clone_pi.yml -u ansible --private-key <path_to_ssh_private_key>
```
