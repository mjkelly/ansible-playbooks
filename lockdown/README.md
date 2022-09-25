# Lockdown

This is the playbook I use to lock down my bastion hosts. They serve as ssh
jump hosts and as a wireguard endpoint.

**WARNING**: This is a fairly aggressive playbook in some ways, and lax in
others. It may not be suitable for you. Specifically:

- It currently works only for Debian.
- It locks the root password.
- It disables password ssh login for all users. (You can still log in with a
  password on the console.)
- It firewalls off all ports except 22 (and the wireguard port, if enabled) by
  default.

We do check that you aren't using root to run ansible (which implies you have
some other user who can sudo) so you won't lock yourself out, but that isn't a
perfect check and you could still lock yourself out other ways.

## Configuration

Make a copy of `hosts.example` that includes the hosts you want to configure.
This requires a user with passwordless sudo by default. (It uses
`ansible_become`.)


Copy `group_vars/all.yml.example` to `group_vars/all.yaml` to get a head start
on configuration.

It works out of the box, without wireguard. If you enable wireguard, you'll
need to do a bit of configuration.

## Running

Assuming you created a file named `hosts`, run this:

```
ansible-playbook -i hosts lockdown.yml
```
