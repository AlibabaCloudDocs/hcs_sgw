# Update gateway versions

This topic describes how to update block gateways in the Cloud Storage Gateway console. This topic also describes the CIDR blocks supported by block gateways deployed on Alibaba Cloud.

## Description

Block gateways V1.0.32 and later deployed on Alibaba Cloud support multiple CIDR blocks included in a VPC. The following table lists the CIDR blocks supported by block gateways.

|Update path|Supported CIDR block before the update|Supported CIDR block after the update|
|-----------|--------------------------------------|-------------------------------------|
|From version 1.0.30 or 1.0.31 to version 1.0.32 and later.|192.168.0.0/16|192.168.0.0/16 172.16.0.0/12 |
|172.16.0.0/12|192.168.0.0/16 172.16.0.0/12 |
|10.0.0.0/8|172.16.0.0/12 10.0.0.0/8 |

## Procedure

1.  Log on to the [CSG console](https://sgwnew.console.aliyun.com/).

2.  On the Gateway Clusters page, find the block gateway to be updated and click **Upgrade** in the Actions column.

    **Note:** Services may be interrupted during the upgrade process.


