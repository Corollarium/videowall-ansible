# UBUNTU INSTALLATION

This documents installation of Camera360 in a Ubuntu server. It was tested on a 20.04 installation with Ansible 2.9.
Either the Server or Desktop versions will work.

## Basics

- run `bootstraph.sh` on the client to setup the user and keys if you need it.

- edit `group_vars/all.yml`

- if you are running ansible locally, run `sudo apt-get install ansible`. If you are running remotely you don't need this

- login as camera360 and allow ssh to localhost or the remote host: 
  - `ssh-keygen -t rsa`
  - `cat .ssh/id_rsa.pub >> .ssh/authorized_keys`

- run installation: 
	- pure web server: `ansible-playbook videowall.yml -i hosts --ask-become-pass`
	- if you have a tunnel.bash, move it to /home/camera360/.tunnel.bash and add: `--extra-vars opentunnel=true`

## Update

- /usr/bin/ansible-playbook self-update.yml -i hosts
