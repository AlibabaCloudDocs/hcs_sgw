# Access an SMB share directory

This topic describes how to access an SMB share directory by using a Cloud Storage Gateway \(CSG\) agent on an Elastic Compute Service \(ECS\) instance that runs Windows.

An SMB share is created. For more information, see [Create a share](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Manage shares.md).

**Note:**

-   You can mount a maximum of 16 SMB share directories. The maximum number of SMB shares supported by different types of gateways varies depending on the CPU and memory. For more information, see [Specifications](/intl.en-US/Overview/Specifications.md).
-   After a share directory is mounted, the maximum capacity of file systems varies depending on the specifications of gateways. For more information, see the "Specifications of cloud file gateways" section of the [Table 1](/intl.en-US/Overview/Specifications.md) topic.
-   For gateways V1.0.35 and later, if you have not created a user, you can access SMB share directories as a public user by default. However, if you have added users, you must grant read and write or read-only permissions to a user before the user can access SMB share directories. For more information, see [Configure an SMB share](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Manage shares.md).
-   After you change SMB user permissions, you must clear user information saved on your CSG agent. You can run the net use/delete < share path \> command to clear user information in Windows. You do not need to restart the agent.

## Procedure

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/).

2.  Connect to your ECS instance that runs Windows. For more information, see [Connect to an ECS instance]().

3.  Open **This PC** and select **Map network drive**.

4.  Select a drive to mount the SMB share directory.

    -   IPv4: Enter the mount target that uses IPv4 in the **Folder** field.
    -   IPv6: Enter the mount target that uses IPv6 in the **Folder** field.

        **Note:**

        -   You can mount a share directory over IPv6 Only the China \(Hohhot\) region. Make sure that the VPC and vSwitch of the gateway support IPv6.
        -   If you mount a share directory over IPv6, make sure that an IPv6 address is configured for the CSG agent.
        -   If the VPC and vSwitch of an existing gateway support IPv6, you can obtain an IPv6 mount target after you enable IPv6 for the gateway. By default, gateways created in this VPC support IPv6.
    The mount target includes the IP address of the gateway and the share name. Specify this parameter based on your scenario. To query the mount target of the gateway, log on to the CSG console and navigate to the Share page of the gateway. By default, a mount target uses IPv4.

5.  Click **Finish** and enter your username and password of the Common Internet File System \(CIFS\).

    If you have joined an Active Directory \(AD\) domain, add the domain before the username. The format is <domain\><username\>.

6.  After you mount the share directory, check the result.

    If the following information appears, the share directory is mounted on the on-premises directory of the CSG agent.

    ![Mounting result](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5688115161/p57999.png)

7.  Access a share directory.

    After a share directory is mounted on the on-premises directory of your CSG agent, you can access the share directory in the same way that you access an on-premises directory. If you have write permissions, you can write data to the share directory. If you have read-only permissions, you can only read data from the share directory. For more information about the user permissions of share directories, see [Configure an SMB share](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Manage shares.md).

    **Note:** A share directory is synchronized with its associated OSS bucket. If you perform operations to a share directory, changes also occur to the associated OSS bucket.


