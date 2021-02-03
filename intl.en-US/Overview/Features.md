# Features

Cloud Storage Gateway \(CSG\) provides two types of gateways: file gateway and block gateway. Each type of gateway has multiple specifications. This topic describes the features supported by different specifications of these gateways.

## File gateways

File gateways support two network transmission protocols: Network File System \(NFS\) and Server Message Block \(SMB\). You can use both protocols to transfer files over LAN.

-   NFS allows you to access file systems in UNIX, such as AIX, HP-UX, and other Linux-based operating systems.
-   SMB allows you to access file systems in Windows.

|Feature|Basic|Standard|Enhanced|Advanced|Documentation|
|-------|-----|--------|--------|--------|-------------|
|Basic features|Cache disks|✓|✓|✓|✓|[Manage cache disks](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Manage cache disks.md)|
|NFS and CIFS services|✓|✓|✓|✓|[Manage shares](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Manage shares.md)|
|AD and LDAP domains|✓|✓|✓|✓|[Configure AD, LDAP, and DNS](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Configure AD, LDAP, and DNS.md)|
|Operations|Modify gateways|✓|✓|✓|✓|[Other supported operations](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Manage file gateways.md)|
|Configure tags|✓|✓|✓|✓|[Manage tags](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Manage tags.md)|
|Back up gateways|×|✓|✓|×|[Back up file gateways](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Back up file gateways.md)|
|Update gateway versions|✓|✓|✓|✓|[Upgrade](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Upgrade.md)|
|Upgrade gateways|✓|✓|✓|✓|[Upgrade a file gateway](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Upgrade a file gateway.md)|
|Upgrade the network bandwidth|✓|✓|✓|✓|[Upgrade the public bandwidth](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Upgrade the public bandwidth.md)|
|Upload logs|✓|✓|✓|✓|[Log management](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Log management.md)|
|Advanced features|Associate a share with multiple OSS buckets|×|×|✓|✓|[Associate a share with multiple OSS buckets](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Associate a share with multiple OSS buckets.md)|
|Remote sync|✓|✓|✓|✓|[Manage shares](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Manage shares.md)|
|Express synchronization|×|✓|✓|✓|[Express synchronization](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Express synchronization.md)|
|Transfer acceleration|✓|✓|✓|✓|[Enable transfer acceleration](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Enable transfer acceleration.md)|
|Server-side encryption|✓|✓|✓|✓|[Create a share](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Manage shares.md)|
|Gateway-side encryption|×|×|✓|✓|[Enable gateway encryption](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Enable gateway encryption.md)|
|Intelligent archiving|×|✓|✓|✓|[Manage shares](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Manage shares.md)|
|Intelligent caching|✓|✓|✓|✓|N/A|
|Intelligent replication|✓|✓|✓|✓|[Replicate data](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Replicate data.md)|
|Ignore deletion|✓|✓|✓|✓|[Manage shares](/intl.en-US/User Guide (Alibaba Cloud)/File Gateway/Manage shares.md)|
|MIME support|✓|✓|✓|✓|N/A|

**Note:** In the preceding table, the check sign \(✓\) indicates that the feature is supported, and the cross sign \(×\) indicates that the feature is not supported.

## Block gateways

Block gateways provide data access services by using the Internet Small Computer System Interface \(iSCSI\) protocol. iSCSI is a storage technology based on the Internet and SCSI-3 protocols. iSCSI can be used to access Windows and UNIX operating systems.

|Feature|Basic|Standard|Enhanced|Advanced|Documentation|
|-------|-----|--------|--------|--------|-------------|
|Basic features|Cache disks|✓|✓|✓|✓|[Manage cache disks](/intl.en-US/User Guide (Alibaba Cloud)/Block Gateway/Manage cache disks.md)|
|iSCSI service|✓|✓|✓|✓|[Manage iSCSI volumes](/intl.en-US/User Guide (Alibaba Cloud)/Block Gateway/Manage iSCSI volumes.md)|
|Operations|Modify gateways|✓|✓|✓|✓|[What to do next](/intl.en-US/User Guide (Alibaba Cloud)/Block Gateway/Manage a block gateway.md)|
|Configure tags|✓|✓|✓|✓|[Manage tags](/intl.en-US/User Guide (Alibaba Cloud)/Block Gateway/Manage tags.md)|
|Update gateway versions|✓|✓|✓|✓|[Update gateway versions](/intl.en-US/User Guide (Alibaba Cloud)/Block Gateway/Update gateway versions.md)|
|Upgrade gateways|✓|✓|✓|✓|[Upgrade a block gateway](/intl.en-US/User Guide (Alibaba Cloud)/Block Gateway/Upgrade a block gateway.md)|
|Configure the network bandwidth|✓|✓|✓|✓|[Upgrade the public bandwidth](/intl.en-US/User Guide (Alibaba Cloud)/Block Gateway/Upgrade the public bandwidth.md)|
|Upload logs|✓|✓|✓|✓|[Log management](/intl.en-US/User Guide (Alibaba Cloud)/Block Gateway/Log management.md)|
|Advanced features|CHAP support|✓|✓|✓|✓|[Create an iSCSI volume](/intl.en-US/User Guide (Alibaba Cloud)/Block Gateway/Manage iSCSI volumes.mdsection_oac_lbk_wdg)|

**Note:** In the preceding table, the check sign \(✓\) indicates that the feature is supported, and the cross sign \(×\) indicates that the feature is not supported.

