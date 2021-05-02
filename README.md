# Ansible

Ansible experiments. This assumes you have python3.

I use virtualenv for this stuff. 

## Initial setup

This is handled by the Makefile,
so just run:

```
make
```

It takes a minute to install the ansible packages.

## Running playbooks

You can do either of the following things when you want to use ansible:

**Way 1**: Run `.venv/bin/ansible-playbook` directly from the virtualenv. No
sourcing required!

**Way 2**: Source the virtualenv and use `ansible-playbook` there:
```
source .venv/bin/activate
# run ansible-playbook
```
(Run `deactivate` to exit the environment without exiting your shell.)

There are example host files in most playbooks.

Is an example command line to get you started:
```
./venv/bin/ansible-playbook -i lockdown/hosts.local lockdown/lockdown.yml
```
