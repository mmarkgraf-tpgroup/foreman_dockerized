Foreman in docker_containers
============================

This was one of my projects while working at [Transporeon](https://www.transporeon.com/).
My employer allowed me to publish it here and I hope it is useful to you.

You will find three Ansible-roles here:

- foreman  
  this is a meta-role that pulls in the other two
- tp.foreman  
  installs foreman in a docker-container
- tp.foreman_configure  
  configures your freshly deployed instance with the help of your Ansible-group_vars
  and ensures the various api-calls are made in the right order.  See the roles README for more details.

To make use of these roles, you will need to have the [Foreman Ansible modules](https://theforeman.org/plugins/foreman-ansible-modules/) installed.
