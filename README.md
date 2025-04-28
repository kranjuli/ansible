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
#        ├── docs/
#        ├── meta/
#        ├── plugins/
#        ├── roles/
#        ├── galaxy.yml
#        └── README.md
# see chapter below to create a new role and playbook
```

#### Build a collection

```bash
# build collection 
ansible-galaxy collection build <path_to_collection>
# collection will be built and compressed to <namespace>-<collection>-<version>.tar.gz 
```

#### Install a collection

```bash
# install local collection
ansible-galaxy collection install <path_to_local_collection> --force 
# install collection from tar.gz file
ansible-galaxy collection install <namespace>-<collection>-<version>.tar.gz --force
```

#### Remove a collection

```bash
# show all installed collections included path to collections
ansible-galaxy collection list
# remove a collection
sudo rm -rf /root/.ansible/collections/ansible_collections/<namespace>/<collection_name>
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
## Ansible role

```bash
# create new role in the collection
ansible-galaxy role init roles/<role_name>

# <namespace>/
#    └── <collection_name>/
#        ├── docs/
#        ├── roles/
#        |   ├── role_name/
#        |       ├── defaults/
#        |       ├── handlers/
#        |       ├── tasks/
#        |       ├── templates/
#        |       ├── tests/
#        |       ├── vars/
#        |       └── README.md
#        |       └── README.md
#        └── galaxy.yml

# open file <namespace>/<collection_name>/roles/role_name/tasks/main.yml in the collection
touch <namespace>/<collection_name>/roles/role_name/tasks/main.yml
# and implement the task in main.yml
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

# implements playbooks in the collection
mkdir <namespace>/<collection_name>/playbooks
touch <namespace>/<collection_name>/playbooks/playbook_1.yml
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
