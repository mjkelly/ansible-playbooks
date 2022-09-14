# Lockdown

Make a copy of `hosts.example` that includes the hosts you want to configure.
This requires a user with passwordless sudo by default. (It uses
`ansible_become`.)

It currently works only for Debian. There used to be a CentOS version, but I
haven't maintained it.

## WARNING

This is a fairly aggressive playbook I use for my own purposes. It may not be
suitable for you. Specifically:

- We lock the root password
- We disable password login for all users
- We firewall off all ports except 22 (by default)

We do check that you aren't using root to run ansible (which implies you have
some other user who can sudo) so you won't lock yourself out, but that isn't a
perfect check and you could still lock yourself out other ways.

## Configuration

`group_vas/all.yaml` contains configuration options.

## Running

Assuming you created a file named `hosts`, run this:

```
ansible-playbook -i hosts lockdown.yml
```

## Caveats

I'm a total noob at Ansible; don't look here for best practices. This is just
an exercise to give me a little more familiarity with writing my own Ansible
stuff.
