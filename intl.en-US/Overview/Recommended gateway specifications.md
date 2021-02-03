# Recommended gateway specifications

This topic describes the recommended specifications and features of gateways in different scenarios.

## File gateways

-   Specifications

    The following table lists the features and scenarios supported by different gateway specifications.

    |Feature|Basic|Standard|Enhanced|Advanced|
    |-------|-----|--------|--------|--------|
    |Archive storage|Not supported|Supported|Supported|Supported|
    |Express synchronization|Not supported|Supported|Supported|Supported|
    |Bandwidth|1 Gbps|2 Gbps~2.5 Gbps|4.5 Gbps~5 Gbps|10 Gbps|
    |Capacity|64 TB|128 TB|256 TB|256 TB|
    |Recommended cache disks|Ultra disks, SSD, and Enhanced SSD|SSD and Enhanced SSD|SSD and Enhanced SSD|SSD and Enhanced SSD|
    |Recommended scenarios|Sharing and storage of a small volume of logs and data. Small websites and user-created FTP sites.|Sharing and storage of logs and data. Sharing data across multiple regions. Share directories, user-created FTP sites, small-sized websites, data archives, and data warehouses.|Unified storage of data and logs. Archiving of large amounts of data. Data sharing among multiple regions. Medium-sized websites, virtual desktop infrastructure \(VDI\)-based share directories, code libraries, and data warehouses.|Unified storage of data and logs. Archiving of large amounts of data. Data sharing among multiple regions. Large-sized websites, VDI-based share directories, code libraries, and data warehouses.|
    |Recommended number of active agents|≤ 5|≤ 20|≤ 50|≤ 150|

-   Features

    The following table lists the specifications of the express synchronization and remote sync features. You can select the features based on your business requirements.

    |Features|Number of files|Metadata synchronization rate|File synchronization frequency|Monthly cost|
    |--------|---------------|-----------------------------|------------------------------|------------|
    |Express synchronization|\> 5,000,000|Maximum synchronization rate: 1,000 incremental files per second.|Less than one second. The maximum update interval is the refresh interval of the NFS/SMB client cache.|Fixed. If the number of API calls is less than 20,000,000 per month \(30 days\), the cost is calculated by using the following formula: \(2+0.5 × number of shares\) × 30.|
    |Remote sync|< 5,000,000|The synchronization rate depends on the time consumed for data scanning and matching.|More than 15 seconds. The maximum update interval is two times the remote sync interval.|Costs are based on the scanning interval and total number of files.|


## Block gateways

The following table lists the features and scenarios supported by different block gateways.

|Feature|Basic|Standard|Enhanced|Advanced|
|-------|-----|--------|--------|--------|
|Bandwidth|1 Gbps|2 Gbps~2.5 Gbps|4.5 Gbps~5 Gbps|10 Gbps|
|Recommended cache disks|Ultra disks, SSD, and Enhanced SSD|SSD and Enhanced SSD|SSD and Enhanced SSD|SSD and Enhanced SSD|
|Recommended scenarios|Large data disks \(larger than 32 TB\) and data backup volumes|Large data disks \(larger than 32 TB\), SMB volumes, and user-created FTP sites.|Large data disks \(larger than 32 TB\), medium-sized websites, DFS volumes, code libraries, and user-created FTP sites.|Large data disks \(larger than 32 TB\), medium-sized websites, DFS volumes, code libraries, and user-created FTP sites.|
|Recommended number of active volumes|≤ 2|≤ 4|≤ 8|≤ 16|

