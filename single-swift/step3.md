Using neadm CLI configure SWIFT Object service by setting up cluster region namespace with few tenants and service name

`
neadm cluster create region1; \
neadm tenant create region1/tenant1; \
neadm tenant create region1/tenant2; \
neadm service create swift swiftsvc; \
neadm service serve swiftsvc region1
`{{execute}}

At this point service is ready to be attached to one or more Edge node by using "add" command and specifying server id (can be found in "neadm system status" output)

`
neadm system status
`{{execute}}

`
neadm service add swiftsvc REPLACE_WITH_SERVER_ID
`{{copy}}

Now that service associated with the right server id, restart service to apply new changes

`
neadm service restart swiftsvc; \
neadm service show swiftsvc
`{{execute}}

By default service will be listening on HTTP port 9982 on all Docker container interfaces.

It will take few seconds for service to become active, please be patient..
