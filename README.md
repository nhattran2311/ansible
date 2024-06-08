# DevOps Environment Setup with Ansible

This repository contains Ansible playbooks for setting up a DevOps environment.
## Table of Contents

- [Installation](#installation)
- [Pre-Setup](#pre-setup)
- [Ad-hoc Commands](#ad-hoc-commands)

## Installation

Install the necessary dependencies with the following commands:

```bash
sudo apt-get update && sudo apt-get upgrade -y
sudo apt-get install python3-pip -y
sudo pip3 install pywinrm
sudo pip3 install pyvmomi
sudo pip3 install ansible
sudo apt-get install sshpass -y
```

## Pre-Setup
Before running the playbooks, make the following changes in `inventory/group_vars/all/vars.yaml`:

- `ansible_user`: Replace with the desired username for the SSH connection.
- `ansible_password`: Replace with the password for the SSH connection.
- `ansible_ssh_private_key_file`: Replace with the path to your SSH private key file. This key will be used for the SSH connection to your WSL.

## Ad-hoc commands

1. **Ping all machines:**
  Use the following command to check the connectivity of all machines:

   ```bash
   ansible-playbook -i inventory/inventory.yaml playbook/ping_all_machine.yaml --limit wsl
   ```

2. **Install setup environment:**
Use the following commands to install the required Ansible roles and run the setup playbook:
```
ansible-galaxy install -r requirements.yml 
ansible-playbook -i inventory/inventory.yaml playbook/setup_devops_environment.yaml --limit wsl
```

3. **Uninstall setup environment:**
```
ansible-playbook -i inventory/inventory.yaml playbook/remove_devops_environment.yaml --limit wsl
```

## Vault commands
Decrypt vault file:
```
ansible-vault decrypt inventory/group_vars/all/vault.yaml --vault-id ~/.vaultid
```

Encrypt vault file:
```
ansible-vault encrypt inventory/group_vars/all/vault.yaml --vault-id ~/.vaultid
```