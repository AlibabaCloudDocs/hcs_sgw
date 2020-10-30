Service linked roles for CSG 
=================================================

This topic describes the following service linked roles of Cloud Storage Gateway (CSG): AliyunServiceRoleForHCSSGW and AliyunServiceRoleForHCSSGWLogMonitor. It also describes how to delete the roles.

Background information 
-------------------------------------------

Resource Access Management (RAM) provides the following service linked roles for CSG: AliyunServiceRoleForHCSSGW and AliyunServiceRoleForHCSSGWLogMonitor. These roles allow CSG to access the resources of other cloud resources. For more information, see [Service linked roles](https://help.aliyun.com/document_detail/160674.html#concept-2448621).

In some scenarios, you may need to use CSG to create an elastic network interface, topics, queues, or subscriptions and use Key Management Service (KMS) to encrypt data. You may also need to use CSG to access, upload, download, and manage data in Object Storage Service (OSS) buckets. To do so, you can use the AliyunServiceRoleForHCSSGW service linked role to authorize CSG to access ECS resources, virtual private cloud (VPC) resources, KMS resources, and OSS resources.

In some scenarios, you may need to use CSG to obtain and push gateway logs. To do so, you can use the AliyunServiceRoleForHCSSGWLogMonitor service linked role to authorize CSG to access Log Service resources.

AliyunServiceRoleForHCSSGW 
-----------------------------------------------

**Note**

AliyunServiceRoleForHCSSGW can be assigned only to a RAM user that has the AliyunHCSSGWFullAccess permission.

AliyunServiceRoleForHCSSGW can access the following cloud service:

* Elastic Network Interface and the relevant security groups

  




CSG must have the following permissions to provide a mount protocol by using ENI and the relevant permission groups:

    {
          "Action": [
            "ecs:CreateNetworkInterface",
            "ecs:DeleteNetworkInterface",
            "ecs:DescribeNetworkInterfaces",
            "ecs:CreateNetworkInterfacePermission",
            "ecs:DescribeNetworkInterfacePermissions",
            "ecs:DeleteNetworkInterfacePermission",
            "ecs:CreateSecurityGroup",
            "ecs:DescribeSecurityGroups",
            "ecs:AuthorizeSecurityGroup",
            "ecs:DeleteSecurityGroup",
            "ecs:JoinSecurityGroup"
          ],
          "Resource": "*",
          "Effect": "Allow"
        }



* VPC

  




CSG must have the following permissions to access your VPC resources:

    {
          "Action": [
            "vpc:DescribeVpcs",
            "vpc:DescribeVSwitches"
          ],
          "Resource": "*",
          "Effect": "Allow"
        }



* OSS

  




CSG must have the following permissions to upload, download, and manage OSS resources:

    {
          "Action": [
            "oss:ListBuckets",
            "oss:ListObjects",
            "oss:GetObject",
            "oss:PutObject",
            "oss:DeleteObject",
            "oss:HeadObject",
            "oss:CopyObject",
            "oss:InitiateMultipartUpload",
            "oss:UploadPart",
            "oss:UploadPartCopy",
            "oss:CompleteMultipartUpload",
            "oss:AbortMultipartUpload",
            "oss:ListMultipartUploads",
            "oss:ListParts",
            "oss:GetBucketStat",
            "oss:GetBucketWebsite",
            "oss:GetBucketInfo",
            "oss:GetBucketEncryption",
            "oss:PutBucketEncryption",
            "oss:DeleteBucketEncryption",
            "oss:RestoreObject",
            "oss:PutObjectTagging",
            "oss:GetObjectTagging",
            "oss:DeleteObjectTagging"
          ],
          "Resource": "*",
          "Effect": "Allow"
        }



* KMS

  




CSG must have the following permissions to perform server-side encryption or client-side encryption on data:

    {
          "Action": [
            "kms:DescribeKey",
            "kms:Encrypt",
            "kms:Decrypt",
            "kms:GenerateDataKey"
          ],
          "Resource": "*",
          "Effect": "Allow"
        }



* Message Service

  




CSG must have the following permissions to configure express synchronization for gateways:

    {
          "Action": [
            "mns:SendMessage",
            "mns:ReceiveMessage",
            "mns:PublishMessage",
            "mns:DeleteMessage",
            "mns:GetQueueAttributes",
            "mns:GetTopicAttributes",
            "mns:CreateTopic",
            "mns:DeleteTopic",
            "mns:CreateQueue",
            "mns:DeleteQueue",
            "mns:PutEventNotifications",
            "mns:DeleteEventNotifications",
            "mns:UpdateEventNotifications",
            "mns:GetEvent",
            "mns:Subscribe",
            "mns:Unsubscribe",
            "mns:ListTopic",
            "mns:ListQueue",
            "mns:ListSubscriptionByTopic"
          ],
          "Resource": "*",
          "Effect": "Allow"
        }



* BSS

  




CSG must have the following permissions to collect and display the billing information of gateways:

    {
          "Action": [
            "bss:DescribePrice"
          ],
          "Resource": "*",
          "Effect": "Allow"
        }



AliyunServiceRoleForHCSSGWLogMonitor 
---------------------------------------------------------

**Note**

AliyunServiceRoleForHCSSGWLogMonitor can be assigned only to a RAM user that has the AliyunHCSSGWFullAccess permission.

AliyunServiceRoleForHCSSGWLogMonitor can access the following cloud services:

* Log Service

  




CSG must have the following permissions to configure log monitoring for gateways:

    {
          "Action": [
            "log:PostLogStoreLogs",
            "log:GetLogStore"
          ],
          "Resource": "*",
          "Effect": "Allow"
        }



Delete the service linked roles 
----------------------------------------------------

Before you delete the AAliyunServiceRoleForHCSSGW or AliyunServiceRoleForHCSSGWLogMonitor service linked role, you must delete all gateways in the CSG console.

For more information, see [Delete a service linked role](https://help.aliyun.com/document_detail/160674.html#section-b9f-8dv-b5q).

