# Specifications

This topic describes the specifications of cloud file gateways, on-premises file gateways, in-cloud block gateways, and on-premises block gateways.

## File gateways

File gateways are classified into cloud file gateways and on-premises file gateways. The following tables describe their specifications.

|Item|Basic|Standard|Enhanced|Advanced|
|----|-----|--------|--------|--------|
|Storage protocol|SMB|NFSv3, NFSv4.0, NFSv4.1, and SMB|NFSv3, NFSv4.0, NFSv4.1, and SMB|NFSv3, NFSv4.0, NFSv4.1, and SMB|
|Maximum number of files|10 million|50 million|100 million|500 million|
|Maximum capacity of file sharing systems \(recommended\)|128 TB|256 TB|512 TB|1 P|
|Maximum number of file share directories|NFS: 4, SMB: 4|NFS: 8, SMB: 8|NFS: 15, SMB: 15|NFS: 15, SMB: 15|
|Maximum number of agents concurrently connected to a gateway|NFS: 1,024, SMB: 1,024|NFS: 1,024, SMB: 1,024|NFS: 1,024, SMB: 1,024|NFS: 1,024, SMB: 1,024|
|Maximum bandwidth for OSS-based synchronization|1 Gbps|2 Gbps|5 Gbps|10 Gbps|
|Encrypted transmission to OSS|Supported|Supported|Supported|Supported|
|Minimum cache capacity|40 GB|40 GB|40 GB|40 GB|
|Maximum cache capacity|1 TB|2 TB|32 TB|32 TB|
|Maximum gateway read bandwidth|1 Gbps|2.5 Gbps|5 Gbps|10 Gbps|
|Maximum gateway write bandwidth|1 Gbps|2 Gbps|3 Gbps|5 Gbps|

|Recommended VM configurations|4 Core/8 GB|8 Core/16 GB|16 Core/32 GB|
|-----------------------------|-----------|------------|-------------|
|Storage protocol|NFSv3, NFSv4, and SMB|NFSv3, NFSv4, and SMB|NFSv3, NFSv4, and SMB|
|Maximum number of files|50 million|50 million|50 million|
|Maximum capacity of file sharing systems \(recommended\)|128 TB|128 TB|128 TB|
|Maximum number of active file share directories \(recommended\)|NFS: 2, SMB: 2|NFS: 4, SMB: 4|NFS: 8, SMB: 8|
|Maximum number of file share directories|NFS: 16, SMB: 16|NFS: 16, SMB: 16|NFS: 16, SMB: 16|
|Maximum number of agents concurrently connected to a gateway|NFS: 1,024, SMB: 1,024|NFS: 1,024, SMB: 1,024|NFS: 1,024, SMB: 1,024|
|Maximum bandwidth for OSS-based synchronization|10 Gbps|10 Gbps|10 Gbps|
|Encrypted transmission to OSS|Supported|Supported|Supported|
|Minimum cache disk capacity|40 GB|40 GB|40 GB|
|Image format|OVA/VHD/QCOW2|OVA/VHD/QCOW2|OVA/VHD/QCOW2|

## Block gateways

Block gateways are classified into cloud block gateways and on-premises block gateways. The following tables describe their specifications.

|Item|Basic|Standard|Enhanced|Advanced|
|----|-----|--------|--------|--------|
|Storage protocol|iSCSI|iSCSI|iSCSI|iSCSI|
|Maximum number of on-premises data volumes|4|8|16|16|
|Maximum volume capacity|256 TB|256 TB|256 TB|256 TB|
|Maximum number of agents concurrently connected to a gateway|Unlimited|Unlimited|Unlimited|Unlimited|
|Maximum bandwidth for OSS-based synchronization|1 Gbps|2 Gbps|5 Gbps|10 Gbps|
|Encrypted transmission to OSS|Supported|Supported|Supported|Supported|
|Cache settings|Pass-through and cache|Pass-through and cache|Pass-through and cache|Pass-through and cache|
|Maximum cache capacity|1 TB|2 TB|32 TB|32 TB|
|Maximum gateway read bandwidth|1 Gbps|2.5 Gbps|5 Gbps|10 Gbps|
|Maximum gateway write bandwidth|1 Gbps|2 Gbps|3 Gbps|5 Gbps|

|Recommended VM specifications|4 Core/8 GB|8 Core/16 GB|16 Core/32 GB|
|-----------------------------|-----------|------------|-------------|
|Storage protocol|iSCSI|iSCSI|iSCSI|
|Maximum volume capacity|256 TB|256 TB|256 TB|
|Recommended number of data volumes|16|64|128|
|Maximum number of data volumes|128|128|128|
|Maximum number of agents concurrently connected to a gateway|Unlimited|Unlimited|Unlimited|
|Encrypted transmission to OSS|Supported|Supported|Supported|
|Minimum cache disk capacity|20 GB|20 GB|20 GB|
|Image format|OVA/VHD/QCOW2|OVA/VHD/QCOW2|OVA/VHD/QCOW2|

