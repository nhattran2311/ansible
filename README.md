# ansible_infra
## Install on wsl2
```
 sudo apt install python3-pip \
 sudo pip3 install pywinrm \
 sudo pip3 install pyvmomi \
 sudo pip3 install ansible
```
## Ad-hoc commands

ping all machines:
```
ansible all -i inventory.yaml -m ping -u tnh5hc
```
Check current directory after login:
```
ansible all -i inventory.yaml -m shell -a "pwd" -u ci
```


## Playbook:
See all available  [Ansible modules](https://docs.ansible.com/ansible/2.9/modules/list_of_all_modules.html)



Excute playbook to install Docker on Guest VMs
```
ansible-playbook -i inventory.yaml playbook.yaml
```
