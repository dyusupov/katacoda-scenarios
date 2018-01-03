Cluster can be managed via CLI or GUI. In this tutorial we will explain how to use CLI to get cluster initialized.
Utility is pre-packaged into nexenta/nedge image and now available. For easy access, setup an alias

`
alias neadm="docker exec -it nfsdata neadm"
`{{execute}}

Verify that service is running (it might take few minutes for service to appear)

`
neadm system status
`{{execute}}

At this point you will see single node shows up in the status output. If desired you can add more nodes to the cluster.
Now, initialize cluster site installation. You will need to read (press enter to scroll), accept EULA and type "yes" at the end.
As a result cluster will be initialized with new GUID (Globally Unique ID).

`
neadm system init
`{{execute}}

Now that cluster initialized, setup DevOps license. We assume that you already have ACTIVATION_KEY token available and ready to be used.

Use e-mailed ACTIVATION_KEY to activate installation

`
neadm system license set online ACTIVATION_KEY
`{{copy}}
