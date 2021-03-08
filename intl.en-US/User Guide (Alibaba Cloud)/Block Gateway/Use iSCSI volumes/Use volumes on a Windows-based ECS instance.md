# Use volumes on a Windows-based ECS instance

This topic describes how to connect to and use iSCSI volumes on a CSG agent on an ECS instance that runs Windows.

-   An iSCSI volume is created. For more information, see [Create an iSCSI volume](/intl.en-US/User Guide (Alibaba Cloud)/Block Gateway/Manage iSCSI volumes.md).
-   The **Microsoft iSCSI initiator service** is enabled on the Windows-based instance.

    ![Microsoft iSCSI initiator service](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8559830951/p60049.png)


## Connect to the iSCSI volume

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/).

    **Note:** If your on-premises server is connected to a virtual private cloud \(VPC\) over an Express Connect circuit, you can also perform the following steps on your server.

2.  Connect to your ECS instance that runs on Windows. For more information, see [Connect to an ECS instance]().

3.  Find and start the **iSCSI Initiator**.

4.  Set up an iSCSI portal.

    1.  In the iSCSI Initiator Properties dialog box, click the Discovery tab, and then click **Discover Portal**.

    2.  In the Discover Target Portal dialog box, enter the IPv4 address or IPv6 address of the block gateway. Click **OK**.

        -   Enter the IPv4 address in the Discover Target Portal dialog box, as shown in the following figure.
        -   Enter the IPv6 address in the Discover Target Portal dialog box, as shown in the following figure.
        -   The port number is set to 3260 by default. We recommend that you do not change the setting.
        -   For example, 10.0.0.0 is the IPv4 address of a block gateway, and 2408:4004:110:6000:4656:f88e:1c14:e578 is the IPv6 address of a block gateway.

            You can query the IPv4 address or IPv6 address of a block gateway in the CSG console. Navigate to the Volume Information page to query the IPv4 address of a block gateway. In the Service IP column of the gateway list, you can query the IPv6 address of a block gateway.

            **Note:**

            -   File gateways version 1.6.0 and later support IPv6.
            -   Mounting over IPv6 is supported only in the China \(Hohhot\) region. The VPC and vSwitch of a gateway must support IPv6.
            -   If you mount a share directory over IPv6, make sure that an IPv6 address is configured for your CSG agent.
            -   If the VPC and vSwitch of an existing gateway support IPv6, you can obtain an IPv6 mount target after you enable IPv6 for the gateway. By default, the gateways created in this VPC support IPv6.
5.  Connect to the iSCSI volume.

    1.  In the iSCSI Initiator Properties dialog box, click the Target tab and then click **Connect**.

    2.  In the Connect to Target dialog box, select the iSCSI volume and the **Add this connection to the list of Favorite Targets** check box.

    3.  Optional. In the Connect to Target dialog box, click **Advanced** and configure CHAP settings. **Click OK**.

        **Note:** If you enabled CHAP when you created the iSCSI volume, you must configure CHAP settings in the Advanced Settings dialog box before you can use the iSCSI volume.

        In the Advanced Settings dialog box, select the **Enable CHAP log on** check box and enter the name and target secret.

        -   In the **Name** field, enter the CHAP username that you set when you created the iSCSI volume.
        -   In the **Target secret** field, enter the CHAP password that you set when you created the iSCSI volume.
    4.  Verify that the connection is established.

        If the status of the iSCSI volume is **Connected**, the connection is established.


## View the iSCSI volume

To view a connected iSCSI volume, perform the following steps:

1.  Open the Computer Management tool and choose **Disk Management** \> **Rescan Disks** to discover the newly added disk.

    After the connection is established, you can use the iSCSI volume on your ECS instance.


## Delete the iSCSI volume

If you disconnect the iSCSI volume, it no longer appears on the ECS instance.

1.  In the iSCSI Initiator Properties dialog box, click the Target tab and then click **Disconnect**.

2.  Verify that the iSCSI volume is disconnected.

    If the status of the iSCSI volume is **Inactive**, the volume is disconnected.


