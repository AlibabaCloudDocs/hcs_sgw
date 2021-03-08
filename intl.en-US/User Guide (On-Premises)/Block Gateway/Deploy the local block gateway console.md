# Deploy the local block gateway console

This topic describes how to deploy the local block gateway console \(a web console\) by using an image. The procedure includes: download the image, install the image, configure network settings, and then activate the gateway.

1.  An Alibaba Cloud account is created and the real-name verification is completed. For more information, see [Create an Alibaba Cloud account](https://www.alibabacloud.com/help/zh/doc-detail/50482.html).

    **Note:** We recommend that you log on to the CSG console as a RAM user. For more information, see [Use RAM to implement account-based access control](/intl.en-US/Best Practice/Use RAM to implement account-based access control.md).

2.  CSG is activated.

    When you log on to the for the first time, activate the CSG service as prompted.

3.  You have created the Alibaba Cloud AccessKey pair, you can log on to the [User Management console](https://usercenter.console.aliyun.com/#/manage/ak) to obtain your AccessKey pair.

Cloud Storage Gateway \(CSG\) can be deployed in on-premises data centers. You can deploy the local block gateway console on the following platforms: VMware vSphere, Hyper-V, and Kernel-based Virtual Machine \(KVM\). Before the deployment, you can download the corresponding gateway image in the CSG console to your local computer.

**Note:**

-   OVA images of version 1.0.30 and later can be deployed only on web clients of vCenter version 6.0 and later.
-   Images downloaded from the Alibaba Cloud CSG console cannot be imported to ECS instances.

## Hardware requirements for virtual machines

The virtual machine where the local block gateway is deployed must meet the following requirements.

-   The virtual machine has at least four virtual CPUs.
-   The virtual machine has at least 8 GB of memory resources.
-   The virtual machine has at least 100 GB of disk space, which is required for installing the CSG image and storing system data.
-   We recommend that you use thick-provisioned cache disks on the virtual machine to obtain excellent I/O performance. The capacity of each cache disk must be 20 GB or larger.

## Installation methods

The installation methods and installation files vary depending on the hypervisor. You can obtain the installation file when you create a local block gateway.

|Hypervisor|Installation method|Installation file format|
|----------|-------------------|------------------------|
|VMware vSphere|You can import an OVA image to VMware to install a gateway.|OVA|
|KVM|You can open the virt-manager and use the QCOW2 file to install a gateway.|QCOW2|
|Hyper-V|You can use a VHD image to create a virtual machine to install a gateway.|VHD|

## Step 1: Download the image

1.  Log on to the [CSG console](https://sgwnew.console.aliyun.com/).

2.  Select the region where you want to create a block gateway.

3.  In the left-side navigation pane, click Gateways. On the Current Gateway Cluster page, select the gateway cluster, and then click **Create**.

    If you have not created a gateway cluster, click **Create Gateway Cluster** on the Overview page to create a gateway cluster.

4.  On the **Basic Information** page, set the following parameters and click **Next**.

    |Parameter|Description|
    |---------|-----------|
    |**Name**|Specify a name for the gateway.|
    |**Location**|Select where you want to deploy the gateway. In this example, select **On-premise**.|
    |**Type**|Select the type of the gateway. In this example, select **iSCSI Gateway**.|

5.  In the **Billing Information** step, set the required parameters, and then click **Next**. The following table describes the parameters.

    |Parameter|Description|
    |---------|-----------|
    |**Billing Method**|The method that the system uses to calculate fees for the gateway. Valid values: **Pay-as-you-go** and **Subscription**. For more information, see [Billable items and billing methods](/intl.en-US/Pricing/Billable items and billing methods.md). If you select **Subscription**, you are redirected to the Cloud Storage Gateway \(Subscription\) page after you create the block gateway. Then, you must complete the payment as prompted. For more information, see [Purchase a subscription gateway](/intl.en-US/Pricing/Subscription/Purchase a subscription gateway.md). |
    |**Expiration Policy**|Select an expiration policy for the gateway. Valid values: **Switch to Pay-as-you-go** and **Release**.|

6.  On the Image Download tab, download the required image to your local machine.


## Step 2: Install the image

After you download the image, you can use it to deploy the block gateway. For more information, see [How do I deploy Cloud Storage Gateway instances in on-premises data centers](/intl.en-US/FAQs/General questions/How do I deploy Cloud Storage Gateway instances in on-premises data centers?.md) .

## Step 3: Configure network settings

After you install the gateway image, you can configure the gateway IP address in the gateway command-line interface \(CLI\).

1.  Start the gateway, and open the Linux terminal of the virtual machine.

2.  Enter the user name and password to log on to the gateway CLI.

    The default user name is root and the password is Alibaba\#sgw\#1030.

3.  Select a language.

    The virtual machine may not support Chinese characters. We recommend that you select English for further configurations.

    ![Language](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2712027951/p58052.png)

4.  Select **Configure the Network** to configure the network.

    ![Configure the network](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2712027951/p58053.png)

    1.  Select **use static ip address** and configure the IP address.

        **Note:** Valid values of Netmask: 1 to 32. For example, if the subnet mask is 255.255.255.0, enter 24.

        ![Configure the IP address](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2712027951/p58054.png)

    2.  Select **config dns** and enter the Domain Name System \(DNS\) server IP address.

        ![Configure DNS settings](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2712027951/p58055.png)

    3.  Select **network test** and check the network configuration result.

        The following message indicates that the network settings have been configured.

        ![Verify DNS settings](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2712027951/p58058.png)

5.  Select **Configure the Date/time** and configure the Network Time Protocol \(NTP\) server.

    The Alibaba Cloud NTP server ntp.aliyun.com is used by default. You can also choose to **specify the time**. The time must be synchronized with that of Alibaba Cloud.

    ![Configure the NTP server](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2712027951/p58063.png)


## Step 4: Activate the gateway

1.  Log on to the [CSG console](https://sgwnew.console.aliyun.com/).

2.  Activate the gateway.

    -   \(Recommended\) Method 1
        1.  Find the target block gateway, and click **Activate Gateway** in the Actions column.
        2.  In the Activate Gateway dialog box that appears, set the following parameters, and click **Activate**.
            -   **Gateway IP address**: Enter the IP address of the gateway.

                **Note:**

                -   Make sure that your browser can connect to the gateway IP address.
                -   The gateway IP address can be the internal IP address of the on-premises data center.
                -   The gateway IP address does not require Internet access.
            -   **Username**: Specify the user name used to log on to the local block gateway console.
            -   **Password**: Specify the password used to log on to the local block gateway console.
            -   **Confirm Password**: Confirm the password that you have specified.
        3.  Open your browser, and enter `https://<IP address of the target block gateway>` in the address bar to connect to the local block gateway console.
        4.  In the dialog box that appears, enter the user name and password.

            **Note:** If this is your first time logging on to the gateway console, you must provide the AccessKey pair of your Alibaba Cloud account. You can log on to the [User Management console](https://usercenter.console.aliyun.com/#/manage/ak) to obtain your AccessKey pair.

    -   Method 2
        1.  Find the target block gateway, and click **Download Certificate** in the Actions column to download the certificate to your local machine.
        2.  Open your browser, and enter `https://<IP address of the target block gateway>` in the address bar to connect to the local block gateway console.
        3.  On the Cloud Storage Gateway Register page, set the following parameters, and click **OK**.

            -   **Upload Certificate**: Click **Upload Certificate** to select the certificate that you want to upload.
            -   **Access Key ID**: Enter the AccessKey ID of your Alibaba Cloud account.
            -   **Access Key Secret**: Enter the AccessKey secret of your Alibaba Cloud account.
            -   **Username**: Specify the user name used to log on to the local block gateway console.
            -   **Password**: Specify the password used to log on to the local block gateway console.
            -   **Confirm Password**: Confirm the password that you have specified.
            **Note:** You can log on to the [User Management console](https://usercenter.console.aliyun.com/#/manage/ak) to obtain your AccessKey pair.

        4.  After you activate the gateway, log on to the local block gateway console.

## Related operations

On the Gateway Clusters page, you can also perform the following operations.

|Operation|Description|
|---------|-----------|
|Delete a gateway|Find the target block gateway and choose **More** \> **Delete** in the Actions column. **Note:** You can only delete pay-as-you-go block gateways. |
|Rename a gateway|Find the target block gateway and click **Edit** in the Actions column to rename the gateway.|
|Switch pay-as-you-go to subscription|After you create a pay-as-you-go gateway, you can switch the billing method from pay-as-you-go to subscription. Find the target block gateway and choose **More** \> **Switch to Subscription** in the Actions column. You are then redirected to the buy page. Select the specification as needed. For more information, see [Switch the billing method from pay-as-you-go to subscription](/intl.en-US/Pricing/Switch the billing method from pay-as-you-go to subscription.md). |
|Reset the password|After you deploy a gateway in an on-premises data center, you can reset the password in the local gateway console. To reset the password, find the target gateway and choose **More** \> **Reset password**.|

