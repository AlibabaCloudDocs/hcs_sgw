# Use an iSCSI volume from the Linux operating system

This topic describes how to connect to and use an iSCSI volume from the Linux operating system.

An iSCSI volume is created. For more information, see [Create an iSCSI volume](/intl.en-US/User Guide (On-Premises)/Block Gateway/Manage iSCSI volumes.md).

## Procedure

1.  Log on to the Linux operating system on your on-premises host.

2.  Install the iscsi-initiator-utils package.

    You must use the iscsi-initiator-utils package to connect to the iSCSI volume. If the iscsi-initiator-utils package is installed, skip this step.

    ```
    sudo yum install iscsi-initiator-utils
    ```

3.  Run the following command to verify that the iSCSI daemon is running.

    -   If you use Red Hat Enterprise Linux \(RHEL\) 5 or RHEL 6, run the following command:

        ```
        sudo /etc/init.d/iscsi status
        ```

    -   If you use RHEL 7, run the following command:

        ```
        sudo service iscsid status
        ```

    If the proceeding commands do not return **running** to you, run the `sudo /etc/init.d/iscsi start` command to start the iSCSI daemon.

4.  Optional. Configure CHAP authentication.

    **Note:** If you enable the CHAP authentication when you create an iSCSI volume, you must configure CHAP settings in this step. Then, you can use the iSCSI volume.

    1.  Run the following command to open the iscsid.conf configuration file:

        ```
        vi /etc/iscsi/iscsid.conf
        ```

    2.  Find CHAP Settings, delete the hash character \(**\#**\) before the related comments, and then set a CHAP username and password.

        -   Enter the CHAP username that you set when you created the iSCSI volume.
        -   Enter the CHAP password that you set when you created the iSCSI volume.
        ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5459830951/p60122.png)

5.  Run the following command to discover the iSCSI volume:

    ```
    iscsiadm -m discovery -t st -p 10.0.0.0:3260
    ```

    -   10.0.0.0 is the IP address of the block gateway. To obtain the IP address, you can choose **About** \> **Network Information** in the on-premises block gateway console.
    -   3260 is the access port. Do not change the port.
6.  Run the following command to mount the iSCSI volume:

    ```
    iscsiadm -m node -T iqn.2009-09.com.aliyun.iscsi-sgw:0test-test730 -p 10.0.0.0:3260 -l
    ```

    -   iqn.2009-09.com.aliyun.iscsi-sgw:0test-test730 is the target name of the iSCSI volume. You can obtain the target name in [Step 2](#step_0dv_1t5_trf).
    -   10.0.0.0 is the IP address of the block gateway. To obtain the IP address, you can choose **About** \> **Network Information** in the on-premises block gateway console.
    -   3260 is the access port. Do not change the port.
    **Note:** Due to the limits of the iSCSI protocol, you cannot mount one iSCSI volume to multiple Linux clients.

7.  Run the `fdisk -l` or `lsblk` command to view the iSCSI volume.

    In this case, the mounted iSCSI volume is an available raw disk. You can read data from and write data to the iSCSI volume from an on-premises host.

    ![View the iSCSI volume](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6459830951/p60107.png)

8.  Unmount the iSCSI volume.

    You can run the following command to unmount the iSCSI volume:

    ```
    iscsiadm -m node -T iqn.2009-09.com.aliyun.iscsi-sgw:0test-test730 -p 10.0.0.0:3260 -u
    ```


