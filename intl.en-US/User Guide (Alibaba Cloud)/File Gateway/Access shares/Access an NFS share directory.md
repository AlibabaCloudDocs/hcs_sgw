# Access an NFS share directory

This topic describes how to access an NFS share directory by using a Cloud Storage Gateway \(CSG\) agent on an Elastic Compute Service \(ECS\) instance that runs Linux.

An NFS share is created. For more information, see [Create a share](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Manage shares.md).

## Mount the NFS share directory

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/).

2.  Connect to your ECS instance that runs Linux. For more information, see [Connect to an ECS instance]().

3.  In the ECS console, run the following command to mount the NFS share directory on the on-premises directory of the CSG agent:

    -   IPv4:

        ```
        mount.nfs 192.168.0.0:/shares local-directory
        ```

    -   IPv6:

        ```
        mount.nfs [2408:4004:ffff:ffff:ffff:ffff:ffff:ffff]:/shares local-directory
        ```

    **Note:**

    -   You can mount a share directory by using IPv6 only in the China \(Hohhot\) region. Make sure that the virtual private cloud \(VPC\) and vSwitch of the gateway support IPv6.
    -   If you mount a share directory by using IPv6, make sure that an IPv6 address is configured for the CSG agent.
    -   If the VPC and vSwitch of an existing gateway support IPv6, you can obtain an IPv6 mount target after you enable IPv6 for the gateway. By default, the gateways created in this VPC support IPv6.
    The preceding command consists of the following parameters:

    -   `192.168.0.0:/shares`: the mount target of the gateway, including the IPv4 address and the share directory name. Specify this parameter based on the actual scenario. To query the mount target of the gateway, log on to the CSG console and navigate to the Share page of the gateway.
    -   `[2408:4004:ffff:ffff:ffff:ffff:ffff:ffff]:/shares`: the mount target of the gateway, including the IPv4 address and the share directory name. Specify this parameter based on the actual scenario. To query the mount target of the gateway, log on to the CSG console and navigate to the Share page of the gateway.
    -   `local-directory`: the on-premises directory of the CSG agent. Specify a file directory that supports read and write operations. You cannot specify a directory that does not exist.
    -   `noac`: If you enable the express synchronization feature and add the share that you want to mount to an express synchronization group, you can specify this parameter in the command. After you specify this parameter, the CSG agent obtains the file system metadata from the gateway in real time. This allows you to check the synchronization result on the CSG agent at the earliest opportunity. This parameter may impact the read and write performance of the CSG agent. If the CSG agent is able to identify data changes, we recommend that you specify this parameter. If the CSG agent requires high read and write performance, we recommend that you do not specify this parameter. The following command is used as an example:

        ```
        mount.nfs -o noac 192.168.0.0/shares local-directory
        ```

    -   If your file gateway version is earlier than 1.0.35, and you have mounted shares by using the NFSv3 protocol, perform the following steps:

1.  Run the following command to query the mount path, for example, `192.168.0.0:/shares`:

    ```
    `showmount -e <gateway IP address>`
    ```

2.  Run the following command to mount the share directory:

    ```
    mount -t nfs -o vers=3,proto=tcp,nolock,noacl,sync 192.168.0.0:/shares local-directory
    ```

4.  Run the `df -h` command to check the result.

    If the following information appears, the share directory is mounted on the on-premises directory of the CSG agent.

    **Note:** After you mount the share directory on the on-premises directory of your CSG agent, the capacity of the file systems that belong to the share appears. For more information about the capacity of the file systems supported by different gateways, see [Specifications](/intl.en-US/Overview/Specifications.md). OSS storage capacity is not limited.


## Access a share directory

After a share directory is mounted on the on-premises directory of your CSG agent, you can access the share directory in the same way as you access an on-premises directory. If you have write permissions, you can write data to the share directory. If you have read-only permissions, you can only read data from the share directory.

**Note:** A share directory is synchronized with its associated OSS bucket. When you manage a share directory, the changes to the share directory are also applied to the associated OSS bucket.

## Enable automatic mounting of a share directory

If you mount a share directory on an ECS instance, the mount information may be lost after the ECS instance is restarted. To resolve this issue, you can configure the fstab \(recommended\) file or rc.local file in the /etc/ directory of the instance. This way, you can enable automatic mounting of an NFS share directory when the ECS instance is restarted.

**Note:** Before you enable automatic mounting, make sure that the share directory is mounted on the on-premises directory of your CSG agent.

-   Method 1 \(recommended\): Open the fstab file in the /etc/ directory and run the mount command.

    **Note:** If your ECS instance runs CentOS 6, perform the following steps:

    1.  Run the `chkconfg netfs on` command first to enable NetFS autostartup.
    2.  Open the netconfig file in the /etc/ directory, and comment out inet6-related information.
    -   If you need to mount a share directory over NFSv4, run the following commands:
        -   IPv4:

            ```
            192.168.0.0:/shares local-directory nfs defaults 0 0
            ```

        -   IPv6:

            ```
            [2408:4004:ffff:ffff:ffff:ffff:ffff:ffff]:/shares local-directory nfs defaults 0 0
            ```

    -   If you need to mount a share directory over NFSv3, run the following commands:
        -   IPv4:

            ```
            192.168.0.0:/shares local-directory nfs vers=3.0 defaults 0 0
            ```

        -   IPv6:

            ```
            [2408:4004:ffff:ffff:ffff:ffff:ffff:ffff]:/shares local-directory nfs vers=3.0 defaults 0 0
            ```


-   Open the rc.local file in the /etc/ directory and run the mount command.

    **Note:** Before you configure the rc.local file in the /etc/ directory, make sure that you have execute permissions on the rc.local file in the execute permissions directory and the rc.local file in the /etc/rc.d/ directory. For example, in CentOS 7.x, execute permissions are not granted by default. Before you edit the rc.local file in the /etc/ directory, grant execute permissions to the account that you use to log on to the ECS instance.

    -   If you need to mount a share directory over NFSv4, run the following commands:
        -   IPv4:

            ```
            sudo mount.nfs 192.168.0.0:/shares local-directory
            ```

        -   IPv6:

            ```
            sudo mount.nfs [2408:4004:ffff:ffff:ffff:ffff:ffff:ffff]:/shares local-directory
            ```

    -   If you need to mount a share directory over NFSv3, run the following commands:
        -   IPv4:

            ```
            sudo mount -t nfs -o vers=3,proto=tcp,nolock,noacl,sync 192.168.0.0:/shares local-directory
            ```

        -   IPv6:

            ```
            sudo mount -t nfs -o vers=3,proto=tcp,nolock,noacl,sync [2408:4004:ffff:ffff:ffff:ffff:ffff:ffff]:/shares local-directory
            ```

    The preceding command consists of the following parameters:

    -   `192.168.0.0:/shares`: the mount target of the gateway, including the IPv4 address and the share directory name. Specify this parameter based on the actual scenario. To query the mount target of the gateway, log on to the CSG console and navigate to the Share page of the gateway.
    -   `[2408:4004:ffff:ffff:ffff:ffff:ffff:ffff]:/shares`: the mount target of the gateway, including the IPv4 address and the share directory name. Specify this parameter based on the actual scenario. To query the mount target of the gateway, log on to the CSG console and navigate to the Share page of the gateway.
    -   `local-directory`: the on-premises directory of the CSG agent. Specify a file directory that supports read and write operations. You cannot specify a directory that does not exist.
    -   `noac`: If you enable the express synchronization feature and add the share that you want to mount to an express synchronization group, you can specify this parameter in the command. After you specify this parameter, the CSG agent obtains the file system metadata from the gateway in real time. This allows you to check the synchronization result on the CSG agent at the earliest opportunity. This parameter may impact the read and write performance of the CSG agent. If the CSG agent is able to identify data changes, we recommend that you specify this parameter. If the CSG agent requires high read and write performance, we recommend that you do not specify this parameter. The following command is used as an example:

        ```
        mount.nfs -o noac 192.168.0.0/shares local-directory
        ```


1.  Run the reboot command to restart the ECS instance.

