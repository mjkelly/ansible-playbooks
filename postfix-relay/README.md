# postfix-relay

Installs postfix and configures it to relay all mail to a smarthost.

First, fill out `group_vars/all.yml`. Then, run:

```
ansible-playbook -i hosts postfix-relay.yml
```

## How to use this

This requires a fairly specific setup:
1. The host from which you send mail should have a fully-qualified domain name,
   e.g. host.example.com
2. You should authorize the domain example.com in SES.

Then, you'll get the following:
1. All email coming from user@host.example.com will be rewritten as
   user@example.com.
2. All email will be delivered to the the value of `localhost_relay_email` in
   `group_vars/all.yml`.  The original recipient will still appear in headers.

There are some other configuration parameters that should allow docker hosts to
serve as smarthost for their containers, as well.

## Why it is this way

This is how I run my home setup, and I think it has these advantages:

1. You don't have to authorize each new domain in SES. If you spin up and shut
   down VMs frequently, this allows you to bake this configuration into new
   VMs. Even if you don't set up new hosts frequently, there are fewer moving
   parts when you do.
2. This minimizes the settings in main.cf -- host rewriting is a fairly
   straightforward application of address masquerading:
   <http://www.postfix.org/ADDRESS_REWRITING_README.html#masquerade>.
3. Because we use the FQDN of the host, we don't have to ask you to for a
   domain name in ansible config, either.

It's not perfect, though, because now we can't distinguish between mail coming
from different machines. The workarounds are that most common sources of mail
(cron) will leave hints for you, and you can always send mail _to_ `$HOSTNAME`,
which won't affect the final destination, but will be left in the header for
you!
