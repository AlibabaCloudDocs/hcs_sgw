# Monitor gateways

This topic describes how to monitor the CPU usage, memory usage, cache IOPS, cache throughput, and network information in the on-premises gateway console.

On-premises file gateways V1.4.0 and later support the log monitoring feature. You can use this feature in the Cloud Storage Gateway \(CSG\) console.

File gateways can monitor the logs of system directories and share directories. The logs are stored in specified Log Services projects and Logstores.

Log data includes information about the network, disks, CPU, and memory. Log data also contain total cache usage, and read and write bandwidth of share directories. This allows you to query information about system directories and share directories.

**Note:** For on-premises gateways, only users in the whitelist can use the log monitoring feature.

## View monitoring information

1.  Open your browser, and in the address bar, enter `https://<IP address of the target file gateway>` to connect to the local file gateway console.

2.  In the dialog box that appears, enter the username and password, and click **OK**.

3.  Click **Monitoring** in the left-side navigation pane. On the Monitoring page, you can monitor the CPU, memory, cache IOPS, cache throughput, and network.


## Log monitoring

If you want to use the log monitoring feature of on-premises gateways, you must navigate to the CSG console. For more information, see [Monitoring](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Monitoring.md).

