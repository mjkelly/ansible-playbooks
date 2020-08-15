# Ansible

Ansible experiments. This assumes you have python3.

I use virtualenv for this stuff. Here's the initial setup:

```
python3 -m venv venv
./venv/bin/pip install -r requirements.txt
```

You can do either of the following things when you want to use ansible:

**Thing 1**: Source the virtualenv and use `ansible-playbook` there:
```
source .venv/bin/activate
# run ansible-playbook
```
(Run `deactivate` to exit the environment without exiting your shell.)

**Thing 2**: Run `.venv/bin/ansible-playbook` directly from the virtualenv. No
sourcing required!
