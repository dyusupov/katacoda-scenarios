NexentaEdge is designed to be "shared-nothing" scale-out SDS solution where data storage containers spread out across physical server nodes connected via Ethernet network (we call it Replicast/UDP backend network).
In this first step we will setup first host node as Edge data node with a location where to keep data blobs:

`
mkdir /var/tmp/data
`{{execute}}

In real deployments the above location ideally has to point to previously prepared mount point using ext4, xfs or zfs filesystems. More complex configuration allows usage of direct raw disk interface as well.

Now that we setup data blobs location, start nexenta/nedge daemon and Edge NFS compatible service

`
docker run --name nfsdata -v /etc/localtime:/etc/localtime:ro -v /var/tmp/data:/data -d nexenta/nedge start -j ccowserv -j nfsserv
`{{execute}}

It will take few minutes for docker image to download. Please be patient..
