# telegraf

Installs [telegraf](https://www.influxdata.com/time-series-platform/telegraf/) and gives it a base configuration that works for me, which means:

- collect system stats
- export to prometheus

This is not necessarily a general-purpose setup, but the config in
`roles/telegraf/files/telegraf.conf` and is easy to change.

Make a copy of `hosts.example` that includes the hosts you want to configure.
This requires a user with passwordless sudo by default. (It uses
`ansible_become`.)

## Configuration

Check `group_vars/all.yml` for config options.

## Running

Assuming you created a file named `hosts.local`, run this:

```
ansible-playbook -i hosts.local telegraf.yml
```
