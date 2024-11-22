# Ansible
${\color {red} {Installation  Steps  For  AmazonLinux:}}$
````
sudo yum update
````
````
sudo yum install ansible
````
````
ansible --version
````
create key-pair using ssh-keygen command

copy public-key from master to authorized_keys file in node .ssh dir
### set up inventory file
````
sudo nano /etc/ansible/hosts
private-ip of node
````
### ping all nodes to test connection
````
ansible all -m ping
````
### Playbook_File
````
- name: update and install and nginx
  hosts: all
  become: true

  tasks:
   
  - name: Upgrade all packages
    yum:
     name: '*'
     state: latest
      
  - name: Install the latest version of nginx
    yum:
     name: nginx
     state: latest
      
  - name: Start nginx
    service:
     name:  nginx
     state: started
     enabled: true
````
## run playbook
````
ansible-playbook nginx.yaml
````
${\color {red} {Installation  Steps  For  Ubuntu:}$

