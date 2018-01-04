Assuming that default Docker bridge address assigned to container is 172.18.0.2 verify that Edge iSCSI LUN is visible

Assuming this server is a client, install open-iscsi

`
apt install -y open-iscsi
`{{execute}}

Discover LUNs and automatically login

`
iscsiadm -m discovery -t st -p 172.18.0.2 -l
`{{execute}}

Now our LUN should be visible

`
dmesg | tail
`{{execute}}
