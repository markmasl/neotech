Zabbix server deployment.

In order to test functionality of the ansible playbook, please, clone this repository.

Playbook tested with ansible 2.4.2.0 and Vagrant 2.0.4 on Linux Mint 18 host

Zabbix was installed on Ubuntu 16.04.4 LTS guest machine.

In order to verigy ansible playbook, please run initiate vagrant. The Vagranfile is alredy configured.

Run ansible playbook from host machine:

ansible-playbook playbooks/zbx-server-installation.yml
