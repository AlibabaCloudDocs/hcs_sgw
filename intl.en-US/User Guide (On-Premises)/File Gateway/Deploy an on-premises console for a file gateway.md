# Deploy an on-premises console for a file gateway

This topic describes how to deploy an on-premises console for a file gateway by using an image. You must download and install the image. Then, you must configure network settings and activate the file gateway.

1.  An Alibaba Cloud account is created and the real-name verification is completed. For more information, see [Create an Alibaba Cloud account](https://www.alibabacloud.com/help/zh/doc-detail/50482.html).

    **Note:** We recommend that you log on to the CSG console as a RAM user. For more information, see [Use RAM to implement account-based access control](/intl.en-US/Best Practice/Use RAM to implement account-based access control.md).

2.  CSG is activated.

    When you log on to the for the first time, activate the CSG service as prompted.

3.  An Alibaba Cloud AccessKey pair is created. You can log on to the [User Management console](https://usercenter.console.aliyun.com/#/manage/ak) to obtain your AccessKey pair.

Cloud Storage Gateway \(CSG\) can be deployed in data centers. You can deploy an on-premises console for a file gateway on the following platforms: VMware vSphere, Hyper-V, and Kernel-based Virtual Machine \(KVM\). Before the deployment, you can download the corresponding gateway images in the CSG console to your computer.

**Note:**

-   OVA images V1.0.30 and later can be deployed only on web clients of vCenter V6.0 and later.
-   Images downloaded from the CSG console cannot be imported to ECS instances.

## Hardware requirements for virtual machines

The virtual machine where the on-premises file gateway is deployed must meet the following requirements:

-   The virtual machine has four vCPUs.
-   The virtual machine has at least 8 GB of memory resources.
-   The virtual machine has at least 100 GB of disk space. The disk space is used to install a CSG image and store system data.
-   We recommend that you use thick-provisioned cache disks on the virtual machine to optimize I/O performance. The size of each cache disk must be 40 GB or larger.

## Installation methods

Installation methods and installation files vary depending on the hypervisor. You can obtain an installation file when you create an on-premises file gateway.

|Hypervisor|Supported installation method|Installation file format|
|----------|-----------------------------|------------------------|
|VMware vSphere|Import an OVA image to VMware.|ova|
|KVM|Open the virt-manager and use the QCOW2 file.|qcow2|
|Hyper-V|Import a VHD file to Hyper-V.|vhd|

## Step 1: Download an image

1.  Log on to the [CSG console](https://sgwnew.console.aliyun.com/).

2.  Select the region where you want to create a file gateway.

3.  In the left-side navigation pane, click Gateways. On the Current Gateway Cluster page, select the gateway cluster, and then click **Create**.

    If you have not created a gateway cluster, click **Create Gateway Cluster** on the Overview page to create a gateway cluster.

4.  On the **Basic Information** page, set the following parameters and click **Next**.

    |Parameter|Description|
    |---------|-----------|
    |**Name**|Specify a name for the gateway. The name must be 1 to 60 characters in length and can contain letters, digits, periods \(.\), underscores \(\_\), and hyphens \(-\). It must start with a letter. |
    |**Location**|Select a place where you want to deploy the gateway. In this example, select **On-premises**.|
    |**Category**|Select the category of the gateway. In this example, select **Storage Gateway**.|
    |**Type**|Select the type of the gateway. In this example, select **File Gateway**.|

5.  In the **Billing Information** step, set the required parameters, and then click **Next**. The following table describes the parameters.

    |Parameter|Description|
    |---------|-----------|
    |**Billing Method**|The method that the system uses to calculate fees for the gateway. Valid values: **Pay-as-you-go** and **Subscription**. For more information, see [Billable items and billing methods](/intl.en-US/Pricing/Billable items and billing methods.md). If you select **Subscription**, after you create the file gateway, you are redirected to the Cloud Storage Gateway \(Subscription\) page. Then, you must complete the payment as prompted. For more information, see [Purchase a subscription gateway](/intl.en-US/Pricing/Subscription/Purchase a subscription gateway.md). |
    |**Expiration Policy**|Select an expiration policy for the gateway. Valid values: **Switch to Pay-as-you-go** and **Release**.|

6.  On the Image Download tab, download the required image to your on-premises machine.


## Step 2: Install the image

After you download the image, you can use it to deploy an on-premises console for the file gateway.

## Step 3: Configure network settings

After you install the gateway image, you can configure the gateway IP address in the command-line interface \(CLI\) of the gateway.

1.  Start the on-premises console of the file gateway, and open the Linux terminal of the virtual machine.

2.  Enter your username and password to log on to the gateway CLI.

    The default username is root and the default password is Alibaba\#sgw\#1030.

3.  Select a language.

    The virtual machine may not support Chinese characters. We recommend that you select English for further configurations.

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2712027951/p58052.png)

4.  Select **Configure the Network** to configure network settings.

    ![Configure the Network](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2712027951/p58053.png)

    1.  Select **use static ip address** and configure the IP address.

        **Note:** Valid values of Netmask: 1 to 32. For example, if the subnet mask is 255.255.255.0, enter 24.

        ![Configure the IP address](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2712027951/p58054.png)

    2.  Select **config dns** and enter the Domain Name System \(DNS\) server IP address.

        ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2712027951/p58055.png)

    3.  Select **network test** and check the network configuration result.

        The following message indicates that the network settings have been configured.

        ![Test results](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2712027951/p58058.png)

5.  Select **Configure the Date/time** and configure the Network Time Protocol \(NTP\) server.

    By default, the Alibaba Cloud NTP server at ntp.aliyun.com is used. You can also select **manual input time**. The time must be synchronized with that of Alibaba Cloud.

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2712027951/p58063.png)


## Step 4: Activate the gateway

1.  Log on to the [CSG console](https://sgwnew.console.aliyun.com/).

2.  Activate the file gateway.

    -   \(Recommended\) Method 1
        1.  Find the file gateway that you want to activate, and click **Activate Gateway** in the Actions column.
        2.  In the Activate Gateway dialog box, set the following parameters, and click **Activate**.
            -   **Gateway IP address**: Enter the IP address of the file gateway.

                **Note:**

                -   Make sure that your browser can connect to the gateway IP address.
                -   The gateway IP address can be the private IP address of your data center.
                -   The gateway IP address does not require Internet access.
            -   **Username**: Specify the username used to log on to the on-premises console of the file gateway.
            -   **Password**: Specify the password used to log on to the on-premises console of the file gateway.
            -   **Confirm Password**: Confirm the password that you have specified.
        3.  Open your browser, and enter `https://<IP address of the target file gateway>` in the address bar to visit the on-premises console of the file gateway.
        4.  In the dialog box that appears, enter your username and password.

            **Note:** If this is your first time to log on to the on-premises console of the file gateway, you must enter the AccessKey pair of your Alibaba Cloud account. You can log on to the [User Management console](https://usercenter.console.aliyun.com/#/manage/ak) to obtain your AccessKey pair.

    -   Method 2
        1.  Find the file gateway that you want to activate. Click **Download Certificate** in the Actions column to download the certificate to your computer.
        2.  Open your browser, and enter `https://<IP address of the target file gateway>` in the address bar to connect to the on-premises console of the file gateway.
        3.  On the Cloud Storage Gateway Register page, set the following parameters, and click **OK**.

            -   **Upload Certificate**: Click **Upload Certificate** to select the certificate that you want to upload.
            -   **Access Key ID**: Enter the AccessKey ID of your Alibaba Cloud account.
            -   **Access Key Secret**: Enter the AccessKey secret of your Alibaba Cloud account.
            -   **Username**: Specify the username used to log on to the on-premises console of the file gateway.
            -   **Password**: Specify the password used to log on to the on-premises console of the file gateway.
            -   **Confirm Password**: Confirm the password that you have specified.
            **Note:** You can log on to the [User Management console](https://usercenter.console.aliyun.com/#/manage/ak) to obtain your AccessKey pair.

        4.  After you activate the file gateway, log on to the on-premises console of the file gateway.

## Related operations

On the Gateway Clusters page of the on-premises console of the file gateway, you can also perform the following operations.

|Operation|Description|
|---------|-----------|
|**Delete a gateway**|Find the file gateway and choose **More** \> **Delete** in the Actions column. **Note:** You can delete only pay-as-you-go file gateways. |
|**Rename a file gateway**|Find the file gateway and click **Edit** in the Actions column to rename the gateway.|
|**Switch to subscription**|After you create a pay-as-you-go gateway, you can switch the billing method from pay-as-you-go to subscription. Find the file gateway and choose **More** \> **Switch to Subscription** in the Actions column. You are then redirected to the buy page. Select the specification as needed. For more information, see [Switch the billing method from pay-as-you-go to subscription](/intl.en-US/Pricing/Switch the billing method from pay-as-you-go to subscription.md). |
|**Reset the password**|After you deploy the on-premises console of the file gateway, you can reset the password in the console. To reset the password, find the file gateway and choose **More** \> **Reset password**.|

