# Usage notes

Before you run Cloud Storage Gateway \(CSG\) instances, read the following usage notes.

## File gateways

-   We recommend that you do not frequently interrupt the upload of large files to Network File System \(NFS\) or Server Message Block \(SMB\) shares. The system uploads files by using multipart uploads. If you interrupt the upload of large files, file fragments are generated in the associated Object Storage Service \(OSS\) bucket. These fragments occupy the capacity of the OSS bucket. Therefore, the storage usage of the OSS bucket is slightly higher than the total file size. You can use the automatic fragment deletion policy supported by OSS to manage file fragments. For more information, see [Manage parts](/intl.en-US/Console User Guide/Upload, download, and manage objects/Manage parts.md).
-   The cache capacity for file sharing is calculated based on the following formula: Recommended local cache capacity = \[Application bandwidth \(MB/s\) - Backend bandwidth of a gateway \(MB/s\)\] × Write duration \(seconds\) × 1.2.

    To ensure a high I/O throughput when you use an on-premises cache disk, you can estimate the total amount of hot data. Compare the total amount of hot data with the recommended on-premises cache capacity, and select the higher value as the capacity of the on-premises cache disk.

-   To write large files by using a file gateway, the size of each file must be smaller than 30% of the cache disk capacity. You cannot write multiple large files at the same time. Otherwise, the cache disk space will be exhausted.
-   File gateways version 1.0.37 and earlier support files of up to 1.2 TB. Files larger than 1.2 TB cannot be uploaded to OSS. File gateways version 1.0.38 and later support files of up to 30 TB. If you upload a file larger than 2 TB, we recommend that you use an Internet bandwidth of 500 MB/s or higher, or connect to Alibaba Cloud over an Express Connect circuit. Otherwise, a timeout error may occur.
-   File gateways support sparse files. If a sparse file fails to be uploaded to a file gateway, run the following command to convert the format of the sparse file:

    ```
    dd if=<sparse file name> of=<sparse file name> conv=notrunc bs=1M
    ```

    The size of the sparse file cannot exceed the available capacity of the cache disk.

-   The names of file gateways and directories must be encoded in UTF-8. File gateways support only file names and directory names that are encoded in UTF-8. Other formats are not supported. For example, if you mount an NFS share of a file gateway on a Windows-based CSG agent, the files and directories that have Chinese names cannot be created. In this case, a 0x8007045D error is reported.
-   If the size of a file in a file gateway exceeds 256 MB, we recommend that you disable versioning for the associated OSS bucket. Otherwise, a timeout error may occur when the gateway uploads metadata to the associated bucket. This degrades the performance of the gateway.
-   File gateways implement permission isolation on Windows Active Directory \(AD\) based on POSIX Access Control Lists \(ACLs\). File gateways do not allow you to authorize multiple AD users across directories. Assume that the AA/BB/CC directory belongs to User 1. If you authorize User 2 to access only the CC directory, User 2 cannot access the data in the CC directory by using the AA/BB/CC directory. You must authorize User 2 to access the AA and BB directories.
-   If you rename a file after you enable the ignore deletions feature for a file gateway, a copy of the file is generated in the OSS bucket. The copy has the new name. Both the file and the copy exist in the OSS bucket. This is because the rename operation in OSS is divided into the copy operation and the delete operation. If you enable the ignore deletions feature, all delete operations are prohibited.

## File gateways deployed on Alibaba Cloud

-   The CSG console uses the HTTPS protocol. Network storage protocols such as NFS and SMB require special ports. Therefore, you must configure a firewall or security group rules for the CSG console to support these ports.
    -   CSG supports AD and LDAP domains. Therefore, you must configure specific ports to support the following protocols: Lightweight Directory Access Protocol \(LDAP\), AD, Domain Name System \(DNS\), and Kerberos. To configure security group rules, you must specify CIDR blocks and security groups. For more information, see [Add security group rules](/intl.en-US/Security/Security groups/Add security group rules.md).

        In a virtual private cloud \(VPC\) network, if a gateway and a domain server belong to different security groups of an Alibaba Cloud account, you can configure security group rules. For example, you can authorize connections between these two security groups. Then, you must add TCP 53/636 and UDP 53/636 as rules to the security group of the domain server.

    -   To support NFS and SMB, configure the corresponding service ports listed in the following table in the inbound rule of the security group of CSG. After you create a file gateway in the CSG console, these ports are configured for the security group by default. Configure ports for LDAP and AD in the inbound rules of the security group on the domain server.

        |Protocol|Port|
        |--------|----|
        |HTTPS|443 and 8080|
        |NFS|111 \(UDP and TCP\), 875 \(UDP and TCP\), 892 \(UDP and TCP\), 2049 \(UDP and TCP\), 32887 \(UDP and TCP\), 32888 \(UDP and TCP\), and 32889 \(UDP and TCP\)|
        |SMB|137 \(UDP\), 138 \(UDP\), 139 \(TCP\), 389 \(TCP\), 445 \(TCP\), and 901 \(TCP\)|
        |SSH|22|
        |LDAP|389 \(UDP and TCP\) and 636 \(UDP\)|
        |AD|445 \(UDP and TCP\)|
        |DNS|53 \(UDP and TCP\)|
        |Kerberos|88 \(UDP and TCP\)|

-   The synchronization bandwidth of a file gateway is determined by the OSS bandwidth. OSS provides an access bandwidth of up to 10 Gbit/s for a single user. The bandwidth slightly varies among clusters in different regions. For more information, contact the technical support of OSS in the region where your OSS buckets reside.
-   After you create a file gateway on Alibaba Cloud, the gateway has a security group prefixed with Cloud\_Storage\_Gateway\_Usage configured by default. Do not use this security group when you create ECS instances.
-   When OSS stores more than one million files, we recommend that you set the interval of remote sync to longer than 3,600 seconds.
-   A Multipurpose Internet Mail Extensions \(MIME\) is automatically specified in the OSS metadata based on the file suffix for file gateways version 1.0.36 and later.
-   If remote sync is enabled, empty on-premises directories that are not uploaded to Alibaba Cloud may be deleted by remote sync during a scan cycle. You can create the directories again to address this issue.
-   By default, the upload bandwidth of gateways deployed on Alibaba Cloud is 1 Mbit/s. These gateways access OSS buckets across regions over the Internet. As a result, the data transmission performance may be unstable.

## On-premises file gateways

-   To use file gateways deployed in data centers, you must open the following ports in the firewall of your CSG agent.

    |Protocol|Port|
    |--------|----|
    |HTTPS|443|
    |NFS|111 \(UDP and TCP\), 875 \(UDP and TCP\), 892 \(UDP and TCP\), 2049 \(UDP and TCP\), 32887 \(UDP and TCP\), 32888 \(UDP and TCP\), and 32889 \(UDP and TCP\)|
    |SMB|137 \(UDP\), 138 \(UDP\), 139 \(TCP\), 389 \(TCP\), 445 \(TCP\), and 901 \(TCP\)|
    |SSH|22|
    |LDAP|389 \(UDP and TCP\) and 636 \(UDP\)|
    |AD|445 \(UDP and TCP\)|
    |DNS|53 \(UDP and TCP\)|
    |Kerberos|88 \(UDP and TCP\)|


## Block gateways

-   The cache capacity of Internet Small Computer Systems Interface \(iSCSI\) volumes is calculated based on the following formula: Recommended on-premises cache capacity = \[Application bandwidth \(MB/s\) - Backend bandwidth of the gateway \(MB/s\)\] × Write duration \(seconds\) × 1.2.

    To ensure a high I/O throughput when you use an on-premises cache disk, you can estimate the total amount of hot data. Compare the total amount of hot data with the recommended on-premises cache capacity, and select the higher value as the capacity of the on-premises cache disk.

-   The synchronization bandwidth of a block gateway is determined by the OSS bandwidth. OSS supports a maximum bandwidth of 10 Gbit/s. The bandwidth slightly varies among clusters in different regions. For more information, contact the technical support of OSS in the region where your OSS buckets reside.
-   The default input/output operations per second \(IOPS\) are determined by the backend disk capacity. An ultra disk supports a maximum bandwidth of 110 MB/s. An SSD disk supports a maximum bandwidth of 230 MB/s.
-   To use block gateways, you must open the following ports in the firewall of your CSG agent.
    -   Block gateways deployed on Alibaba Cloud

        |Protocol|Port|
        |--------|----|
        |iSCSI|860 \(TCP\) and 3260 \(TCP\)|

    -   Block gateways deployed in data centers

        |Protocol|Port|
        |--------|----|
        |HTTPS|443|
        |iSCSI|860 \(TCP\) and 3260 \(TCP\)|


