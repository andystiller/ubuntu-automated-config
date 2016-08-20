# ubuntu-automated-config
Procedure and scripts to automatically install and set-up addition software on Ubuntu Desktop.

## 1. Restore back-up
Restore the backup including the ssh keys.

## 2. Install Ansible
Run the ansible-setup.sh script as root.
Edit the /et/ansible/hosts file to add the following
```
[me]
127.0.0.1
```

## 3. Configure SSH Server

## 4. Install standard software
First create the personal.yml file in the vars folder.
The variable that need to be configured are:
* sudopassword:
* mysql_root_password:
* ansible_ssh_user:

Check that the base-software.yml file includes all the required software.
```ansible-playbook base-software.yml```

## 4. Set-up LAMP