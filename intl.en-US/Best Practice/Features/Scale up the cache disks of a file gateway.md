# Scale up the cache disks of a file gateway

This topic describes how to scale up the cache disks of a file gateway.

In the current climate, business changes take place all the time, and underlying systems must be scaled to meet these changes. If the local cache capacity of a cloud storage gateway \(CSG\) no longer meets your business requirements, you can scale up the cache disks of the gateway to increase the capacity. If the workloads increase and the local cache capacity cannot handle the new workload, you can scale up the cache disks. The cache capacity in use cannot be scaled up. You must configure the scale-up process. The following example shows you how to scale up the cache disks of a file gateway in the CSG console and the local console of the file gateway. We recommend that you use the specified formula to calculate the cache capacity of a file gateway. For more information.

## Prepare for the scale-up of the cache disks

When you scale up the cache disks, you must detach the file system. Therefore, make sure that no I/O write operations are performed and all NFS and SMB clients have stopped reading and writing during the scale-up process. Unmount CSG on all clients. Wait until the cache disks of the file gateway on the Share page is in the Sync Completed state, as shown in the following figu

## Delete other CSG instances that are associated with the OSS bucket

Back up the configurations of the file gateway \(bucket, share name, access control list, and advanced options\). Delete other CSG instances that are associated with the Object Storage Service \(OSS\) bucket in the CSG console and the local console of the gateway. The cache disks are not removed. However, the local cache is detached from the OSS bucket. The cache disks of the file gateway are in the Sync Completed state. Therefore, all data is uploaded to the OSS bucket. When you delete shares, no data loss occurs.

## Scale up the cache disks of the file gateway

Log on to the CSG console. Click Cache in the left-side navigation pane. On the page that appears, click the Add icon in the Actions column, as shown in the following figure.

Click the Add icon in the Actions column. The following window appears.

Specify a new cache capacity to scale up the cache disks. The minimum cache capacity is 1 GB. Click OK. A purchase order is generated. After you confirm the purchase and complete the payment, the scale-up process is complete. You can view the new cache capacity in the CSG console.

If you want to scale up the cache disks of a local file gateway, you must go to the VMware vSphere, Virtual Hard Disk \(VHD\), or Kernel-based Virtual Machine \(KVM\) deployment platforms. For more information, see Add disks.

## Recreate shares

Recreate shares based on the previous share names and configurations. When you recreate shares, select the cache disks that are scaled up. The new shares show the new cache capacity. For more information, see.

