# Saltstack test bed

# Vagrant setup
`vagrant up` to load boxes. You will need to specify a hosts file in the salt-setup to get the Ansible playbook to configure Saltstack onto these VMs

# Ansible
tl;dr `ansible-playbook saltcluster.yml -i hosts`

We run roles to setup the master, acquire the ip and fingerprint, then setup the minions, apply the configurations so that the minions can resolve the master, then restart the services. Lastly, we accept the minions by verifying the key fingerprints.

## Hosts file
Replace the fields that need replacing.
```
[masters]
master ansible_ssh_host=127.0.0.1 ansible_ssh_port=<vagrant_box_port> ansible_ssh_user='vagrant' ansible_ssh_private_key_file='vagrant_box_key'

[minions]
minion1 ansible_ssh_host=127.0.0.1 ansible_ssh_port=<vagrant_box_port> ansible_ssh_user='vagrant' ansible_ssh_private_key_file='vagrant_box_key'
minion2 ansible_ssh_host=127.0.0.1 ansible_ssh_port=<vagrant_box_port> ansible_ssh_user='vagrant' ansible_ssh_private_key_file='vagrant_box_key'
```
