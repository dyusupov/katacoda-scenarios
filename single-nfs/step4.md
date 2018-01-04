Assuming that default Docker bridge address assigned to container is 172.18.0.2 verify that Edge NFS port is listening

Run on the client to verify that portmapper listening

`
rpcinfo -p 172.18.0.2
`{{execute}}

See if export shows up on the client

`
showmount -e 172.18.0.2 | grep bk1
`{{execute}}

Now lets play with it a little bit, mount it

`
mkdir /tmp/a; \
mount -t nfs 172.18.0.2:/bk1 /tmp/a
`{{execute}}

Copy few files to it

`
cp /var/log/*.log /tmp/a/
`{{execute}}

Remount and list files again

`
umount /tmp/a; \
mount -t nfs 172.18.0.2:/bk1 /tmp/a; \
ls -l /tmp/a/
`{{execute}}
