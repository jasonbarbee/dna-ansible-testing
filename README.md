# Cisco SD-Access Testing - Ansible
## Author : Jason Barbee 

# Purpose 
To login to each border and ping test *reachable* and expected *unreachable* devices in an Cisco DNA SD-Access Deployment. Makes a good test package when doing any maintenance to the fabric or core routing.

Edit the dictionary list under group_vars/all.yml to change the source, destinatation and expected unreachable destinations.

HOW? - It will login to each device via SSH and run these commands. 

# Setup 

Download Ansible and install it for your platform. 
Copy the folder structure down to the computer that will run this.

If you want to use Ansible-Vault -

create a file with the vault password in it so that credentials are secure.
```
echo "password" > vault-pass.key
ansible-vault create roles/secrets/vars/main.yml
```
Paste in these variables and save it.
```
ansible_user: sshuser
ansible_ssh_pass: sshpassword
```

# Usage
Without Ansible-Vault
```
ansible-playbook site.yml -i inventory
```
or With Ansible-Vault
```
ansible-playbook site.yml -i inventory --vault-password-file  vault-pass.key
```


# Reference
Ansible uses roles to group tasks like borders and cores. It's built like this because the borders are IOS, and the cores are NX-OS. The syntax is slightly different.

# Tested on version
Ansible 2.7
