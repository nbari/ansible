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

Single host:

    ansible 10.13.15.2 -m ping

A group:

    ansible mygroup -m ping -u your_user_name -k

A group with sudo (raw ubuntu linux):

    ansible mygroup -m ping -u your_user_name -k --sudo -K

* -k ask for password
* -K ask for sudo password

Run a command:

    ansible all -a "uptime"

per group:

    ansible mygroup -m ping -u your_user_name -k --sudo -K -a "/bin/echo hello"

Remove ubuntu package:

    ansible mygroup -m apt -a "name=sudo-master state=absent" -u admin --sudo -K

Parallelism:

    ansible all -a "uptime" -f 4

* -f 4 specifies the usage of 4 simultaneous processes to use.

raw - Executes a low-down and dirty SSH command, example:

    ansible mygroup -m raw -a  "uname" -u operations


Send the SSH keys
-----------------

Use ``ssh-copy-id`` in Mac OS X you may need:

    brew install ssh-copy-id

Send keys:

    ssh-copy-id user@remote.server.tld

Playbooks
=========

Run the playbook:

    ansible-playbook book.yml

Ask sudo password:

    ansible-playbook book.yml -K

Playbook for specific hosts:

    # file ping.yml (playbook)
    ---
    - hosts: '{{ target }}'
    ...

Run the playbook:

    ansible-playbook ping.yml --extra-vars "target=your_host"

if ``{{ target }}`` isn't defined, the playbook does nothing. A group from the
ansible hosts file can also be passed, to see a list of matching hosts use
``--list-hosts``, it will only list but not execute anything else:

    ansible-playbook ping.yml --extra-vars "target=aws" --list-hosts

Check Mode:

    ansible-playbook ping.yml --check
