# Access an NFS share directory

This topic describes how to access an NFS share directory by using a Cloud Storage Gateway \(CSG\) agent on a Linux-based client.

An NFS share is created. For more information, see [Install an NFS client](/intl.en-US/User Guide (On-Premises)/File Gateway/Manage NFS shares.md).

Before you can access an NFS share from a Linux-based client, you must mount the share on the on-premises file directory of the client. After the share is mounted, directory mappings are established between the share directory and the on-premises directory. You can access the share directory in the same way as you access an on-premises directory.

## Procedure

1.  Log on to the on-premises Linux-based client.

2.  Mount the NFS share to the on-premises directory of the client.

    1.  Run the following command to mount the share directory:

        ```
        mount.nfs 192.168.0.0:/shares local-directory
        ```

        -   192.168.0.0:/shares: the mount target of the gateway, including the IP address and the share directory name. Specify this parameter based on the actual scenario. To check the mount target of the gateway, log on to the CSG console and navigate to the Share page of the gateway.
        -   local-directory: the on-premises directory of the CSG client. Specify a file directory that supports read and write operations. You cannot specify a directory that does not exist.
        **Note:** For example, assume that your file gateway version is earlier than 1.0.35, and you have mounted shares by using the NFSv3 protocol. You must run the `showmount -e <gateway IP address>` command to query the mount path by performing the following steps:

        1.  Run the following command to query the mount path, for example, 192.168.0.0:/shares.

            ```
            `showmount -e <gateway IP address>`
            ```

        2.  Run the following command to mount the share directory:

            ```
            mount -t nfs -o vers=3,proto=tcp,nolock,noacl,sync 192.168.0.0:/shares local-directory
            ```

    2.  Run the `df -h` command to check the result.

        If the following information appears, the share directory is mounted on the on-premises directory of the client.

        **Note:** The capacity of the mounted share is equal to the capacity of the Object Storage Service \(OSS\) bucket. The displayed capacity 256 TB is the maximum capacity of the file system. OSS storage capacity is not limited.

        ![Mounting result](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/0812027951/p57623.png)

3.  Access the share directory.

    After a share directory is mounted on the on-premises directory of your client, you can access the share directory in the same way as you access an on-premises directory. If you have write permissions, you can write data to the share directory. If you have read-only permissions, you can only read data from the share directory.

    **Note:** A share directory is synchronized with its associated OSS bucket. If you perform operations to a share directory, changes occur to the associated OSS bucket too.


## Enable automatic mounting of a share directory

If you mount a share directory on an ECS instance, the mount information may be lost after the ECS instance is restarted. To resolve this issue, you can configure the fstab \(recommended\) file or rc.local file in the /etc/ directory of the instance. This way, you can enable automatic mounting of an NFS share directory when the ECS instance is restarted.

**Note:** Before you enable automatic mounting, make sure that the share directory is mounted on the on-premises directory of your client.

1.  Method 1: \(Recommended\) Open the fstab file in the /etc/ directory and add the mount command.

    **Note:** If your client runs CentOS 6, perform the following steps first:

    1.  Run the `chkconfg netfs on` command to enable NetFS autostartup.
    2.  Open the netconfig file in the /etc/ directory, and comment out inet6-related information.
    -   If you need to mount a share directory over NFSv4, run the following command:

        ```
        192.168.0.0:/shares local-directory nfs defaults 0 0
        ```

    -   If you need to mount a share directory over NFSv3, run the following command:

        ```
        192.168.0.0:/shares local-directory nfs vers=3.0 defaults 0 0
        ```

2.  Method 2: Open the rc.local file in the /etc/ directory and run the mount command.

    **Note:** Before you configure the rc.local file in the /etc/ directory, make sure that you have execute permissions on the rc.local file in the execute permissions directory and rc.local file in the /etc/rc.d/ directory. For example, in CentOS 7.x, execute permissions are not granted by default. Before you edit the rc.local file in the /etc/ directory, grant execute permissions to the account that you use to log on to the ECS instance.

    1.  If you need to mount a share directory over NFSv4, run the following command:

        ```
        sudo mount.nfs 192.168.0.0:/shares local-directory
        ```

    2.  If you need to mount a share directory over NFSv3, run the following command:

        ```
        sudo mount -t nfs -o vers=3,proto=tcp,nolock,noacl,sync 192.168.0.0:/shares local-directory
        ```

    The preceding commands consist of the following parameters:

    -   192.168.0.0:/shares: the mount target of the gateway, including the IP address and the share directory name. Specify this parameter based on the actual scenario. To check the mount target of the gateway, log on to the CSG console and navigate to the Share page of the gateway.
    -   local-directory: the on-premises directory of the CSG client. Specify a file directory that supports read and write operations. You cannot specify a directory that does not exist.
3.  Run the `reboot` command to restart the client.

