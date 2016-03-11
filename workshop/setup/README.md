Via Pip
=======

Ansible can be installed via
[pip](https://en.wikipedia.org/wiki/Pip_(package_manager)), the Python package
manager. If ``pip`` isn’t already available in your version of Python, you can
get pip by:

    $ sudo easy_install pip

> you can upgrade pip using: pip install --upgrade pip

Then install Ansible with:

    $ sudo pip install ansible

To install ``stable-2.0``:

    $ sudo pip install -U git+https://github.com/ansible/ansible.git@stable-2.0#egg=ansible
