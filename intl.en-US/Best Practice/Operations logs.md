Operations logs 
====================================

Cloud Storage Gateway (CSG) is integrated with ActionTrail. You can view and retrieve behavioral logs, and deliver these logs to a Logstore or specified OSS bucket by using ActionTrail. This meets the requirements of real-time audit and error backtracking analysis.
**Note**

You can query operations logs generated after November 28, 2020.

View operations logs 
-----------------------------------------

1. Log on to the [CSG console](https://sgwnew.console.aliyun.com).

   

2. In the left-side navigation pane, click **Operation Audit** .

   

3. On the Operation Audit page, click the Add icon on the left of the operations log that you want to view.

   




CSG operations logs recorded in ActionTrail 
----------------------------------------------------------------

CSG operations logs record API events. The value of the eventType parameter for OpenAPI events is set to ApiCall in ActionTrail. For more information, see [Cloud Storage Gateway APIs](https://help.aliyun.com/document_detail/170253.html?spm=a2c4g.11174283.6.662.722e4b55T0Ed9w).

The following table lists the API events that are not included in the preceding topic.


| Event type |          Event name           |                       Description                        |
|------------|-------------------------------|----------------------------------------------------------|
| ApiCall    | StartElasticGateway           | Starts an elastic gateway.                               |
| ApiCall    | StopElasticGateway            | Stops an elastic gateway.                                |
| ApiCall    | SetElasticGatewayDataPolicy   | Configures a data policy for an elastic gateway.         |
| ApiCall    | ModifyGatewayStorageTarget    | Modifies the storage target of an elastic gateway.       |
| ApiCall    | ModifyElasticGatewaySpec      | Modifies the maximum throughput of an elastic gateway.   |
| ApiCall    | DescribeGatewayStorageTargets | Describes the storage target of an elastic gateway.      |
| ApiCall    | DeleteGatewayStorageTarget    | Deletes the storage target of an elastic gateway.        |
| ApiCall    | CreateGatewayStorageTarget    | Create the storage target of an elastic gateway.         |
| ApiCall    | CreateElasticGateway          | Creates an elastic gateway.                              |
| ApiCall    | DescribeGatewayMonitorData    | Describes the performance metrics of an elastic gateway. |



Example 
----------------------------

The following example shows an operations log entry recorded in ActionTrail. This log entry contains the details of the process in which you call the CreateGateway operation to create a gateway:

    {
        "eventId":"D334EC86-****-****-****-34D49A613994",
        "eventVersion":"1",
        "responseElements":{ // The response elements of the CreateGateway operation.
            "RequestId":"D334EC86-****-****-****-34D49A613994",
            "Message":"successful",
            "GatewayId":"gw-0001**********rk08",
            "Code":"200",
            "Success":true
        },
        "eventSource":"sgw.cn-hangzhou.aliyuncs.com",
        "requestParameters":{ // The request parameters of the CreateGateway operation.
            "AcsHost":"sgw.cn-hangzhou.aliyuncs.com",
            "Category":"Aliyun",
            "PublicNetworkBandwidth":5,
            "RequestId":"D334EC86-****-****-****-34D49A613994",
            "VSwitchId":"vsw-bp1c********ea7",
            "StorageBundleId":"sb-000a**********wrb2",
            "HostId":"sgw.cn-hangzhou.aliyuncs.com",
            "GatewayClass":"Basic",
            "Name":"test",
            "Type":"File",
            "ReleaseAfterExpiration":false,
            "AcsProduct":"sgw",
            "AcceptLanguage":"zh-CN",
            "PostPaid":true,
            "RegionId":"cn-hangzhou",
            " charset":"UTF-8",
            "Location":"Cloud"
        },
        "sourceIpAddress":"192.168.1.1" ,// The source IP address of the event.
        "userAgent":"sgwnew.console.aliyun.com",
        "eventType":"ApiCall",
        "referencedResources": { // The list of resources involved in the event.
            "ACS::CloudStorageGateway::Gateway":[
                "gw-0001**********rk08"
            ]
        },
        "userIdentity":{ // The user information.
            "sessionContext":{
                "attributes":{
                    "mfaAuthenticated":"false"
                }
            },
            "accountId":"106 ********* 811", // The ID of the Alibaba Cloud account.
            "principalId":"106 ********* 811" ,// The user ID.
            "type":"root-account" ,// The Alibaba Cloud account.
            "userName":"root"
        },
        "serviceName":"CloudStorageGateway", // The name of the cloud service in the event.
        "additionalEventData":{
            "Scheme":"https"
        },
        "apiVersion":"2018-05-11",
        "requestId":"D334EC86-****-****-****-34D49A613994",
        "eventTime":"2020-11-18T11:14:05Z", // The time when the event occurs. The time must be in UTC.
        "acsRegion":"cn-hangzhou", // The Alibaba Cloud region.
        "eventName":"CreateGateway" // The name of the event. 
    }



