# local-ca

Sets up a local CA (not trusted by default) and distributes certs to nodes.
Useful for setting up mutually-authenticated TLS connections.

Make a copy of `hosts.example` that includes the hosts you want to configure.
This requires a user with passwordless sudo by default. (It uses
`ansible_become`.)

## Running

Assuming you created a file named `hosts.local`, run this:

```
ansible-playbook -i hosts.local node.yml
```
