Via Pip
=======

Ansible can be installed via
[pip](https://en.wikipedia.org/wiki/Pip_(package_manager)), the Python package
manager. If ``pip`` isn’t already available in your version of Python, you can
get pip by:

    $ sudo easy_install pip

> you can upgrade pip using: pip install --upgrade pip

Then install Ansible with:

    $ pip install --user ansible

To install ``stable-2.0``:

    $ sudo pip install -U git+https://github.com/ansible/ansible.git@stable-2.0#egg=ansible

passlib:

    $ pip install --user passlib

Create pass:

    $ python -c "from passlib.hash import sha512_crypt; import getpass; print sha512_crypt.encrypt(getpass.getpass())"
