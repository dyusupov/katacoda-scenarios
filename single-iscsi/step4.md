Assuming that default Docker bridge address assigned to container is 172.18.0.2 verify that Edge iSCSI port is listening

`
netstat -ant|grep "3260"|grep LISTEN
`{{execute}}
