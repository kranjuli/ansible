# ansible

Collection of ansible collections and playbooks.

## Ansible Collection

### Create, build and install an ansible collection with galaxy.yml

#### Create a collection

```bash
# create skeleton of collection
ansible-galaxy collection init <namespace>.<collection_name>

# <namespace>/
#    └── <collection_name>/
#        ├── playbooks/
#        │   └── playbook_1.yml
#        ├── roles/
#        │   ├── role_1/
#        │       ├── tasks/
#        │           └── main.yml
#        └── galaxy.yml

# implements roles in the collection
mkdir <namespace>/<collection_name>/roles/role_1/tasks
touch <namespace>/<collection_name>/roles/role_1/tasks/main.yml
# implement the task in main.yml

# implements playbooks in the collection
mkdir <namespace>/<collection_name>/playbooks
touch <namespace>/<collection_name>/playbooks/playbook_1.yml
```

#### Build a collection

```bash
# build collection 
ansible-galaxy build
# collection will be built and compressed to <namespace>-<collection>-<version>.tar.gz 
```

#### Install a collection

```bash
# install collection 
ansible-galaxy install <namespace>-<collection>-<version>.tar.gz
# run playbook
ansible-playbook <namespace>.<collection>.playbook_1.yml 
```

#### Install ansible dependencies in requirements.yml

The ansible dependencies can be defined in requirements.yml

```yaml
---
collections:
    - source: url_to_custom_collection.tar.gz
      type: url
    - name: ansible.posix
        version: 2.0.0
    - name: community.general
        version: 10.5.0
```

```bash
ansible-galaxy install -r requirements.yml
```

## Playbook

### Create a playbook

Playbook must be created manually.

```bash
# <namespace>/
#    └── <collection_name>/
#        ├── playbooks/
#        │   └── playbook_1.yml
#        ├── roles/
#        └── galaxy.yml
```

### Run a playbook

```bash

# run playbook without install collection
ansible-playbook -i <ip_target_host>, <namespace>/<collection_name>/playbooks/playbook_1.yml -u <ssh_user_on_target_host> --private-key <path_to_ssh_private_key>

# run playbook with install collection
ansible-playbook -i <ip_target_host>, <namespace>.<collection_name>.playbook_1.yml

# debugging
ansible-playbook -i <ip_target_host>, <namespace>.<collection_name>.playbook_1.yml -vvv
```
