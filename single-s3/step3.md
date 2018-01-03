Using neadm CLI configure S3 service by setting up cluster region namespace, service name and attach it to a tenant

`
neadm cluster create region1; \
neadm tenant create region1/tenant1; \
neadm service create s3 s3svc; \
neadm service serve s3svc region1/tenant1
`{{execute}}

At this point service is ready to be attached to one or more Edge node by using "add" command and specifying server id (can be found in "neadm system status" output)

`
neadm system status
`{{execute}}

`
neadm service add s3svc REPLACE_WITH_SERVER_ID
`{{copy}}

Now that service associated with the right server id, restart service to apply new changes

`
neadm service restart s3svc; \
neadm service show s3svc
`{{execute}}

By default service will be listening on HTTP port 9982 on all Docker container interfaces.

It will take few seconds for service to become active, please be patient..
