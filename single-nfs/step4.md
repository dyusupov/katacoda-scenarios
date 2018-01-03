Assuming that default Docker bridge address assigned to container is 172.18.0.2 verify that Edge NFS port is listening

Run on the client to verify that portmapper listening

`
rpcinfo -p
`{{execute}}

See if export shows up on the client

`
showmount -e 172.18.0.2 | grep bk1
`{{execute}}
