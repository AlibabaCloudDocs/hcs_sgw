# Monitoring

This topic describes how to monitor file gateways in the Cloud Storage Gateway \(CSG\) console by using the log monitoring feature and monitoring metrics. Monitoring metrics include CPU usage, memory usage, IOPS of cache disks, the read and write speed of cache disks, and network throughput.

File gateways version 1.0.39 and later support the log monitoring feature. You can use this feature in the CSG console.

File gateways can monitor the logs of system directories and share directories. The logs are stored in specified Log Services projects and Logstores.

-   Audit logs record business operations performed on Alibaba Cloud, including the upload, rename, and delete operations. This helps you check the operation status and response time.
-   Monitoring logs consist of the information of the network, disks, CPU, memory, amount of data downloaded from and uploaded to OSS, cached data, and OSS data. Monitoring logs also show the read and write bandwidth of share directories and OSS health check status.

**Note:** For on-premises gateways, only users in the whitelist can use the log monitoring feature.

## View monitoring information

1.  Log on to the [CSG console](https://sgwnew.console.aliyun.com/).

2.  On the Gateway Clusters page, find and click the target file gateway.

3.  Navigate to the Details page to view the monitoring information.

    |Metric|Description|
    |------|-----------|
    |**CPU**|CPU usage, including User CPU and System CPU.|
    |**Memory**|Includes Used Memory and Free Memory.|
    |**Cache Disk IOPS**|The number of read and write operations of the cache disk per second, including Read IOPS and Write IOPS.|
    |**Cache Disk Read/write**|Includes Disk Read and Disk Write.|
    |**Network I/O**|Includes Data Receive Rate and Data Send Rate.|


## Configure the log monitoring feature

1.  Log on to the [CSG console](https://sgwnew.console.aliyun.com/).

2.  On the Gateway Clusters page, find and click the target file gateway.

3.  Click Details to go to the Details page.

4.  In the Log Monitoring section, click **Create**.

5.  In the Create Log Monitoring dialog box, set the required parameters.

    If you do not have an available project or Logstore, create a project or Logstore first. For more information, see [Create a project](/intl.en-US/Data Collection/Preparation/Manage a project.md) and [Create a Logstore](/intl.en-US/Data Collection/Preparation/Manage a Logstore.md).

6.  Click **OK**.

    Wait 10 minutes, and then log on to the [Log Service console](https://sls.console.aliyun.com/) to view the log data of the file gateway.

    **Note:** You can view the synchronization list of gateway files in the Log Service console. For more information, see [How do I view the synchronization list of gateway files in the Log Service console?](/intl.en-US/FAQs/Usage of file gateway/How do I view the synchronization list of gateway files in the Log Service console?.md).


## What to do next

In the **Log Monitoring** section, you can also perform the following operations.

|Operation|Description|
|---------|-----------|
|Delete a log monitoring project|If you no longer need to use the log monitoring feature, click **Delete**.|
|Disable log monitoring|If you need to temporarily disable the log monitoring feature, click **Disable**.|

