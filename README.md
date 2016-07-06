emmetog.swarm-master
====================

An Ansible role for provisioning servers with docker swarm masters.

This role ensures that a docker swarm master instance is running on a host.

Usually used with the [emmetog.swarm-agent](https://github.com/emmetog/ansible-swarm-agent) role which installs
swarm agents on hosts.

Requirements
------------

This role requires the `emmetog.docker-compose` role since docker-compose is used to start the swarm services.
Also, a respectably recent version of Docker should be already installed on the hosts.
The role assumes that a consul agent is reachable on the same host on port 8500.

You can use the [emmetog.consul](https://galaxy.ansible.com/emmetog/consul/) role to install consul.

Role Variables
--------------

This role doesn't need any variables.

Usage
-----

First install the role from ansible galaxy:
```
$ ansible-galaxy install emmetog.swarm-master
```

Then use the role in a playbook as follows:
```yml
- hosts: swarm_masters
  roles:
     - emmetog.swarm-master
```

If used with the [emmetog.swarm-agent](https://github.com/emmetog/ansible-swarm-agent) role then you might decide to run both
in one block like this:
```yml
- hosts: swarm_nodes
  roles:
     - emmetog.swarm-master
     - emmetog.swarm-agent
```
Note: That will run both a swarm master and a swam agent on each node, which may or may not be what you want to do. Add
salt to taste.

License
-------

MIT

Author Information
------------------

Made with love by Emmet O'Grady.

I am the founder of [NimbleCI](https://nimbleci.com) which builds Docker containers for feature branch workflow projects in Github.

I blog on my [personal blog](http://blog.emmetogrady.com) and about Docker related things on the [NimbleCI blog](http://blog.nimbleci.com).