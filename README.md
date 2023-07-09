# ansible_infra
## Install on WSL2
```
 sudo apt update -y \
 && sudo apt install python3-pip -y \
 && sudo pip3 install pywinrm \
 && sudo pip3 install pyvmomi \
 && sudo pip3 install ansible \
 && sudo apt-get install sshpass -y
```

## Pre-Setup
Please make the following changes in inventory/group_vars/all/vars.yaml:
* ansible_user: Replace with the desired username for SSH connection.
* ansible_password: Replace with the password for SSH connection.
* ansible_ssh_private_key_file: Replace with the path to your SSH private key file used for SSH connection to your WSL.
## Ad-hoc commands

1. Ping all machines:
```
ansible-playbook -i inventory/inventory.yaml playbook/ping_all_machine.yaml --limit wsl
```
1. Install Docker on WSL2 locally:
```
ansible-playbook -i inventory/inventory.yaml playbook/deploy_docker_machine.yaml --limit wsl
```

1. Install setup environment:
```
ansible-playbook -i inventory/inventory.yaml playbook/setup_devops_environment.yaml --limit wsl
```

1. Uninstall setup environment:
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

Check the current directory after login:

```
ansible all -i inventory.yaml -m shell -a "pwd" -u ubuntu
```



Execute playbook to install Docker on guest VMs:
```
ansible-playbook -i inventory.yaml playbook.yaml
```
