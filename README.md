# ansible_infra
## Install on wsl2
```
 sudo apt install python3-pip \
 && sudo pip3 install pywinrm \
 && sudo pip3 install pyvmomi \
 && sudo pip3 install ansible \
 && apt-get install sshpass
```
## Ad-hoc commands

ping all machines:
```
ansible all -i inventory.yaml -m ping -u tnh5hc
ansible-playbook -i inventory/inventory.yaml playbook/ping_all_machine.yaml --limit wsl
```
Install Docker on WSL2 locally:
```
ansible-playbook -i inventory/inventory.yaml playbook/deploy_docker_machine.yaml --limit wsl --vault-id ~/.vaultid
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
