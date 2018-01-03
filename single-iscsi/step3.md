Using neadm CLI configure iSCSI service by setting up cluster region namespace, service name and attach it to a tenant

`
neadm cluster create region1; \
neadm tenant create region1/tenant1; \
neadm bucket create region1/tenant1/bk1; \
neadm service create iscsi iscsisvc; \
`{{execute}}

Create 8gb LUN with 128K chunk size and replication count 1

`
neadm iscsi create iscsisvc region1/tenant1/LUN1 8G -s 128K -r 2
`{{execute}}

At this point service is ready to be attached to one or more Edge node by using "add" command and specifying server id (can be found in "neadm system status" output)

`
neadm system status
`{{execute}}

`
neadm service add iscsisvc REPLACE_WITH_SERVER_ID
`{{copy}}

Now that service associated with the right server id, restart service to apply new changes

`
neadm service restart iscsisvc; \
neadm service show iscsisvc
`{{execute}}

Verify that service is running

`
neadm iscsi status iscsisvc
`{{execute}}

By default service will be listening on iSCSI port 3260 on all Docker container interfaces.

It will take few seconds for service to become active, please be patient..
