# ansible_infra
## Install on wsl2
```
 sudo apt update -y \
 sudo apt install python3-pip -y \
 && sudo pip3 install pywinrm -y \
 && sudo pip3 install pyvmomi -y \
 && sudo pip3 install ansible -y \
 && apt-get install sshpass -y
```
## Ad-hoc commands

ping all machines:
```
ansible-playbook -i inventory/inventory.yaml playbook/ping_all_machine.yaml --limit wsl
```
Install Docker on WSL2 locally:
```
ansible-playbook -i inventory/inventory.yaml playbook/deploy_docker_machine.yaml --limit wsl
```

```
ansible-playbook -i inventory/inventory.yaml playbook/setup_devops_environment.yaml --limit wsl
```

Uninstall Setup
```
ansible-playbook -i inventory/inventory.yaml playbook/uninstall_devops_environment.yaml --limit wsl -vvv
```

## Vault commands
```
ansible-vault decrypt inventory/group_vars/all/vault.yaml --vault-id ~/.vaultid
```
```
ansible-vault encrypt inventory/group_vars/all/vault.yaml --vault-id ~/.vaultid
```
Check current directory after login:
```
ansible all -i inventory.yaml -m shell -a "pwd" -u ci
```



Excute playbook to install Docker on Guest VMs
```
ansible-playbook -i inventory.yaml playbook.yaml
```
