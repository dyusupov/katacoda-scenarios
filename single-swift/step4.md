Assuming that default Docker bridge address assigned to container is 172.18.0.2 verify that Edge SWIFT service port is listening verify that curl command can now access default port 9981

`
curl http://172.18.0.2:9981
`{{execute}}

Lets now play with the service a little bit... Create new bucket

`
curl -X PUT http://172.18.0.2:9981/v1/tenant1/bk1
curl -X PUT http://172.18.0.2:9981/v1/tenant2/bk1
`{{execute}}

Generate new 10MB file

`
dd if=/dev/zero of=/tmp/10mb count=10 bs=1M
`{{execute}}

Upload file to the tenant's bucket /bk1

`
curl http://172.18.0.2:9982/v1/tenant1/bk1/10mb --upload-file /tmp/10mb
curl http://172.18.0.2:9982/v1/tenant2/bk1/10mb --upload-file /tmp/10mb
`{{execute}}

View file metadata for tenant1's /bk1

`
curl -I http://172.18.0.2:9982/v1/tenant1/bk1/10mb
`{{execute}}

View file metadata for tenant2's /bk1

`
curl -I http://172.18.0.2:9982/v1/tenant2/bk1/10mb
`{{execute}}
