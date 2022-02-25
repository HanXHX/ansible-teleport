Tests informations
==================

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
