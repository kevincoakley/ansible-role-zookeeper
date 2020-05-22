Ansible Role: Zookeeper
=========

![](https://github.com/kevincoakley/ansible-role-zookeeper/workflows/Molecule%20Test/badge.svg)

An Ansible role that installs Apache Zookeeper in either a standalone or replicated environment. Test with Zookeeper version 3.6.1.

Requirements
------------

You must be running a Linux OS that has systemd enabled by default (CentOS 7, CentOS 8, Ubuntu 18.04 and Ubuntu 20.04).

Role Variables
--------------

Name of system host group in /etc/ansible/hosts to automatically configure the replicated environment.

	zookeeper_ansible_host_group: zookeeper

Variable name of the Ansible fact to be used in conf/zoo.conf to define the servers in the cluster.

    zookeeper_server_variable: ansible_ssh_host

Version of Zookeeper to install.

	zookeeper_version: 3.4.7

tickTime variable in conf/zoo.cfg.

	zookeeper_tick_time: 2000

initLimit variable in conf/zoo.cfg.

	zookeeper_init_limit: 10

syncLimit variable in conf/zoo.cfg.

	zookeeper_sync_limit: 5

Directory where Zookeeper data is stored.

	zookeeper_data_dir: /tmp/zookeeper/

Zookeeper client port.

	zookeeper_client_port: 2181

maxClientCnxns variable in conf/zoo.cfg.

	zookeeper_max_client_cnxns: 60

Directory where Zookeeper logs are stored.

	zookeeper_log_dir: /tmp/


Dependencies
------------

None

Example Playbook
----------------

Example zookeeper_playbook.yml:

	- hosts: zookeeper
  	  sudo: yes

	  vars:
	    zookeeper_version: 3.6.1

	  roles:
	    - zookeeper


Example /etc/ansible/hosts:

	[zookeeper]
	zookeeper-0 zookeeper_id=0
	zookeeper-1 zookeeper_id=1
	zookeeper-2 zookeeper_id=2


License
-------

BSD

Author Information
------------------

Kevin Coakley (https://github.com/kevincoakley)
