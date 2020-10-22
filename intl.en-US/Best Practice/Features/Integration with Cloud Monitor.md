# Integration with Cloud Monitor

This topic describes how to query the monitoring data of file and block gateways in the CloudMonitor console.

You have created a gateway in the Cloud Storage Gateway \(CSG\) console. For more information, see [Manage a file gateway in the CSG console](/intl.en-US/Quick Start/Manage a file gateway in the CSG console.md).

Beginning with version 1.3.0, CSG is integrated with CloudMonitor. CSG data can be monitored by CloudMonitor and displayed in the CloudMonitor console.

-   Monitoring data of file gateways includes: the gateway CPU usage in the user mode, the cache usage of each share, the memory usage of the gateway, the metadata disk usage of each share, the write and read speeds of each share, the throttling status of each share, and the upload rate of each share.
-   Monitoring data of block gateways includes: the gateway CPU usage in the user mode, the memory usage of the gateway, and the cache usage of each volume.

**Note:** CloudMonitor can only monitor gateways that are deployed on Alibaba Cloud.

## View monitoring data

1.  Log on to the [CloudMonitor console](https://account.aliyun.com/login/login.htm?oauth_callback=https%3A%2F%2Fcloudmonitor.console.aliyun.com%2F%3Fspm%3Da2c4g.11186623.2.18.6dde963ba0QyU6).

2.  In the left-side navigation pane, choose **Dashboard** \> **Dashboards**.

3.  On the Dashboards page, select the region and ID of the target gateway. The monitoring data is displayed in different charts.


## Related operations

To meet the requirements of different scenarios, you can select or specify a time range to filter monitoring data.

|Parameter|Description|
|---------|-----------|
|Time range|Supports 1 hour, 3 hours, 6 hours, 12 hours, 1 day, 3 days, 7 days, and 14 days.|
|Custom time range|CloudMonitor provides monitoring data of the last 30 days. The monitoring data is accurate to the minute. The time range of a query can span up to seven consecutive days.|

