# Use volumes on a Linux-based ECS instance

This topic describes how to connect to and use the iSCSI volumes of a CSG agent on an ECS instance that runs Linux.

An iSCSI volume is created. For more information, see [Create an iSCSI volume](/intl.en-US/User Guide (Alibaba Cloud)/Block Gateway/Manage iSCSI volumes.md).

## Procedure

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/).

    **Note:** If your ECS instance is connected to a virtual private cloud \(VPC\) over an Express Connect circuit, you can also perform the following steps on your instance.

2.  Connect to your ECS instance that runs Linux. For more information, see [Connect to an ECS instance]().

3.  Install the iscsi-initiator-utils package.

    You need the iscsi-initiator-utils package to connect to the iSCSI volume. If you have already installed the iscsi-initiator-utils package, skip this step.

    ```
    sudo yum install iscsi-initiator-utils
    ```

4.  Run the following command to verify that the iSCSI daemon is running:

    -   If you are using RHEL 5 or RHEL 6, run the following command:

        ```
        sudo /etc/init.d/iscsi status
        ```

    -   If you are using RHEL 7, run the following command:

        ```
        sudo service iscsid status
        ```

    If the proceeding commands do not return **running**, run the `udo /etc/init.d/iscsi start` command to start the iSCSI daemon.

5.  Optional. Configure CHAP authentication.

    **Note:** If you enabled CHAP when you created the iSCSI volume, you must configure CHAP settings in the Advanced Settings dialog box before you can use the iSCSI volume.

    1.  Run the following command to open the iscsid.conf configuration file:

        ```
        vi /etc/iscsi/iscsid.conf
        ```

    2.  Find CHAP Settings and delete the hash character \(**\#**\) before the relevant comments, and set the CHAP username and password.

        -   Enter the CHAP username that you set when you created the iSCSI volume.
        -   Enter the CHAP password that you set when you created the iSCSI volume.
        ![Configure CHAP authentication](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5459830951/p60122.png)

6.  Discover the iSCSI volume.

    -   Run the following command to discover the iSCSI volume over IPv4:

        ```
        iscsiadm -m discovery -t st -p 10.0.0.0:3260
        ```

    -   Run the following command to discover the iSCSI volume over IPv6:

        ```
        iscsiadm -m discovery -t st -p [2408:4004:110:6000:4656:f88e:1c14:e578]:3260
        ```

    -   For example, 10.0.0.0 is the IPv4 address of a block gateway, and 2408:4004:110:6000:4656:f88e:1c14:e578 is the IPv6 address of a block gateway.

        You can query the IPv4 address or IPv6 address of a block gateway in the CSG console. Navigate to the Volume Information page to query the IPv4 address of a block gateway. In the Service IP column of the gateway list, you can query the IPv6 address of a block gateway.

        **Note:**

        -   Gateways version 1.6.0 and later support IPv6.
        -   You can mount a share directory over IPv6 Only the China \(Hohhot\) region. The VPC and vSwitch of a gateway must support IPv6.
        -   If you mount a share directory over IPv6, make sure that an IPv6 address is configured for your CSG agent.
        -   If the VPC and vSwitch of an existing gateway support IPv6, you can obtain an IPv6 mount target after you enable IPv6 for the gateway. By default, the gateways created in this VPC support IPv6.
    -   The port number is set to 3260 by default. We recommend that you do not change the setting.
7.  Run the following command to mount the iSCSI volume:

    -   IPv4:

        ```
        iscsiadm -m node -T iqn.2009-09.com.aliyun.iscsi-sgw:0test-test730 -p 10.0.0.0:3260 -l
        ```

    -   IPv6:

        ```
        iscsiadm -m node -T iqn.2009-09.com.aliyun.iscsi-sgw:0test-test730 -p [2408:4004:110:6000:4656:f88e:1c14:e578]:3260 -l
        ```

    -   iqn.2009-09.com.aliyun.iscsi-sgw:0test-test730 is the iSCSI volume. You can obtain the volume name in Step 6.
    -   For example, 10.0.0.0 is the IPv4 address of a block gateway, and 2408:4004:110:6000:4656:f88e:1c14:e578 is the IPv6 address of a block gateway.

        You can query the IPv4 address or IPv6 address of a block gateway in the CSG console. Navigate to the Volume Information page to query the IPv4 address of a block gateway. In the Service IP column of the gateway list, you can query the IPv6 address of a block gateway.

        **Note:**

        -   Gateways version 1.6.0 and later support IPv6.
        -   You can mount a share directory over IPv6 Only the China \(Hohhot\) region. The VPC and vSwitch of a gateway must support IPv6.
        -   If you mount a share directory over IPv6, make sure that an IPv6 address is configured for your CSG agent.
        -   If the VPC and vSwitch of an existing gateway support IPv6, you can obtain an IPv6 mount target after you enable IPv6 for the gateway. By default, the gateways created in this VPC support IPv6.
    -   The port number is set to 3260 by default. We recommend that you do not change the setting.
    **Note:** Due to the limits of the iSCSI protocol, do not mount one iSCSI volume on multiple Linux clients.

8.  Run the `fdisk -l` or `lsblk` command to view the iSCSI volume.

    In the current status, the mounted iSCSI volume becomes an available raw disk. You can read data from and write data to the iSCSI volume by using an on-premises computer.

    ![View the iSCSI volume](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6459830951/p60107.png)

9.  Unmount the iSCSI volume

    You can run the following command to unmount an iSCSI volume:

    -   IPv4:

        ```
        iscsiadm -m node -T iqn.2009-09.com.aliyun.iscsi-sgw:0test-test730 -p 10.0.0.0:3260 -u
        ```

    -   IPv6:

        ```
        iscsiadm -m node -T iqn.2009-09.com.aliyun.iscsi-sgw:0test-test730 -p [2408:4004:110:6000:4656:f88e:1c14:e578]:3260 -u
        ```


