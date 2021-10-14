# Restoring Failover Cluster after a failure
This uses Powershell since there's no GUI in our setup.
## Hardware configuration
```
       _________________________
      |                         |
    NODE1 <-----> NAS <-----> NODE2
           iSCSI       iSCSI
```

Since DC, DNS and DHCP services runs on cluster, if it fails, we need physical access to one of the node to restore cluster.

## Check iSCSI connection
Just use `Get-IscsiTarget` and validate target is connected

    PS C:\> Get-IscsiTarget
    IsConnected NodeAddress 
    ----------- ----------- 
    True iqn.1991-05.com.contoso:testiscsi-deepcore-target

If it's not connected, try to reconnect to target.

## Restart cluster ressources
Once connectivity is back and node are back online, failover ressources must be restarted:

    Get-ClusterResource | Start-ClusterResource

To restart specific VM:

    Get-ClusterResource -Name *VMNAME | Get-VM | Start-VM

## Fileshare
Fileshare role didn't start right away. Check that resources like disk, network and IP address for this role are up before trying to bring it up.

    #failovercluster #powershell #fc
