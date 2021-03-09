# Use an iSCSI volume from the Windows operating system

This topic describes how to connect to and use an iSCSI volume from the Windows operating system.

-   An iSCSI volume is created. For more information, see [Create an iSCSI volume](/intl.en-US/User Guide (On-Premises)/Block Gateway/Manage iSCSI volumes.md).
-   The Microsoft iSCSI initiator service is started in the Windows operating system.

    ![Start the Microsoft iSCSI initiator service](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8559830951/p60049.png)


## Procedure

1.  Log on to the Windows operating system on your on-premises host.

2.  Find and start the **iSCSI Initiator**.

3.  Configure an iSCSI portal.

    1.  In the iSCSI Initiator Properties dialog box, click the Discovery tab, and then click **Discover Portal**.

    2.  In the Discover Target Portal dialog box, enter the IP address of the block gateway, and then click **OK**.

        -   10.0.0.0 is the IP address of the block gateway. To obtain the IP address, you can choose **About** \> **Network Information** in the on-premises block gateway console.
        -   3260 is the access port. Do not change the port.
4.  Connect to the iSCSI volume.

    1.  In the iSCSI Initiator Properties dialog box, click the Targets tab, and then click **Connect**.

    2.  In the Connect to Target dialog box, select the iSCSI volume and the **Add this connection to the list of Favorite Targets** check box.

    3.  Optional. In the Connect to Target dialog box, click **Advanced** and configure CHAP settings.

        **Note:** If you enable the CHAP authentication when you create an iSCSI volume, you must configure the CHAP settings in the Advanced Settings dialog box. Then, you can use the iSCSI volume.

        In the Advanced Settings dialog box, select the **Enable CHAP log on** check box, and then set the **Name** and **Target secret** parameters.

        -   In the **Name** field, enter the CHAP username that you specified when you created the iSCSI volume.
        -   In the **Target secret** field, enter the CHAP password that you specified when you created the iSCSI volume.
    4.  In the Connect to Target dialog box, click **OK**.

    5.  Verify that the connection is established.

        If the iSCSI volume is in the **Connected** state, the connection is established.

5.  Open the Computer Management tool, and choose **Disk Management** \> **Rescan Disks** to discover the newly added iSCSI volume.

    After the connection is established, you can use the iSCSI volume from your on-premises host.

6.  Disconnect the iSCSI volume.

    1.  In the iSCSI Initiator Properties dialog box, click the Targets tab, and then click **Disconnect**.

        If you disconnect the iSCSI volume, the related disk is no longer displayed on the on-premises host.

    2.  Verify the disconnection result.

        If the iSCSI volume is in the **Inactive** state, the iSCSI volume is disconnected.


