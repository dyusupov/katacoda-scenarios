Using neadm CLI configure NFS service by setting up cluster region namespace, service name, and share tenant's bucket

`
neadm cluster create region1; \
neadm tenant create region1/tenant1; \
neadm bucket create region1/tenant1/bk1; \
neadm service create nfs nfssvc
`{{execute}}

At this point service is ready to be attached to one or more Edge node by using "add" command and specifying server id (can be found in "neadm system status" output)

`
neadm system status
`{{execute}}

`
neadm service add nfssvc REPLACE_WITH_SERVER_ID
`{{copy}}

Now that service associated with the right server id, share tenant's bucket

`
neadm nfs share nfssvc region1/tenant1/bk1
`{{execute}}

and restart service to apply new changes

`
neadm service restart nfssvc; \
neadm service show nfssvc
`{{execute}}

By default service will be listening on NFS ports on all Docker container interfaces.

It will take few seconds for service to become active, please be patient..