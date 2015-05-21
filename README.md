# ansible

Basic setup
-----------

Definie ``ANSIBLE_HOSTS`` example:

    export ANSIBLE_HOSTS=~/ansible/hosts

Content of hosts looks like:

    [work]
    10.15.1.3 ansible_python_interpreter=/usr/local/bin/python

    [aws]
    54.72.130.39

    [freebsd]
    10.13.15.2
    10.13.15.3

    [freebsd:vars]
    ansible_python_interpreter=/usr/local/bin/python

> ``ansible_python_interpreter`` allows to define where is python on the remote node

Test
----

A basic ping test:

    ansible all -m ping

Test sudo:

    ansible all -m ping --sudo
