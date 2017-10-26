Digital Ocean Bootstrap
=======================

Bootstrap Digital Ocean droplets using Ansible to:

* Configure SSH key
* Launch a droplet
* Configure DNS domain
* Destroy droplet

Inspired by [hostmaster/ansible-digitalocean-bootstrap](https://github.com/hostmaster/ansible-digitalocean-bootstrap)
Modified from [yoshz/ansible-digitalocean](https://github.com/yoshz/ansible-digitalocean)


Installation
------------

* Install Ansible
* Install pip
* Install dopy
* Copy vars.yml.dist to vars.yml and change the variables to your needs
* Copy the id_rsa for pulling from github to files/id_rsa
* Make your hosts file


Digital Ocean configuration
---------------------------

Create a new API key on the [API access page](https://cloud.digitalocean.com/api_access).
Add the api_token to `vars.yml`.


GitHub configuration
---------------------------

Create a personal access token [GitHub Developer Settings](https://github.com/settings/developers).
Add the access token to `vars.yml`.


Playbooks
=========

launch.yml
----------

Launch and provision a new server on Digital Ocean.

```
    ansible-playbook -i hosts launch.yml
```

What this Playbook do for you?

- configure swap file
- install ufw, fail2ban
- configure ufw allow ports for SSH
- make sshd more secure:
  - PermitRootLogin=no
  - PasswordAuthentication=no
  - AllowGroups=sudo
- config sudoers
- clones git repos
- generates virtual hosts
- secures hosts with Let's Encrypt

destroy.yml
-----------

Destroys a server on Digital Ocean.

```
    ansible-playbook -i hosts destroy.yml
```

To-Do List
------------

* Add digitalocean monitoring
* Automatically add hostkey
* Add sqlite
