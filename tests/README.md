Tests informations
==================

IMPORTANT
---------

With self-signed certificates, Teleport have some stranges issues (infinite loops on web applications, silent crashes...). To test properly, you must use `--insecure` flag on **ALL** commands. Unfortunately you must start teleport daemon by hand and not use systemd service.

```
sudo systemctl stop service
sudo /usr/local/bin/teleport start --pid-file=/run/teleport.pid --insecure
```

This hack can be bypassed with a systemd unit override (PR welcome).

Tips
----

Create an admin user on teleport server:

```
tctl users add --roles editor,access --logins root,vagrant teleport-admin
```

Check database connection:
```
tsh login --proxy=teleport-server-debian-bullseye:443 --auth=local --user=teleport-admin --insecure

tsh db login --db-user=test_teleport --db-name=test_teleport_db --insecure vagrant-node-postgresql
tsh db connect vagrant-node-postgresql
```
