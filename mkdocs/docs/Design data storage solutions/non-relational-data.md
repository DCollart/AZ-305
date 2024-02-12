# Design for non-relational data

- Consider Azure blob storage: vast amount of unstructured data. Often used for multimedia files.
- Consider Azure files: accessible via SMB/NFS and REST API.
- Consider Azure managed disk: block-level storage for VM.
- Consider Azure queue storage: store message to be processed asynchronously.

## Azure storage account

Types : 

- Standard general purpose v2: blob (+ data lake storage), queue, files, table.
- Premium block blobs: blob (+ data lake storage)
- Premium file shares: files (SMB/NFS)
- Premium page blobs: page blobs (disks, OS, ...)

Consider:

- Location (close increase performance)
- Compliance 
- Costs: no cost for the account itself.
- Replication
- Administrative overhead
- Data sensitivity
- Data isolation

## Redundancy 

- LRS
- (RA)ZRS
- (RA)GRS 
- (RA)ZGRS

Consider :
Primary region replication option for not sensitive data that does not require high durability.
LRS for data that can be easily reconstructed.
ZRS for excellent performance, low latency and resiliency for data.
Secondary region when high durability needed.
Read access requirement for replicated data for high availability.

## Azure blob storage
4 access options : 
Premium blob storage
Hot
Cool 
Archive

|Comparison|	Premium Blob Storage|	Hot access tier	| Cool access tier	| Archive access tier|
|Availability|	99.9%	|99.9%	|99%	|Offline|
|Availability (RA-GRS reads)|	N/A	|99.99%	|99.9%	|Offline|
|Latency (time to first byte)|	Single-digit milliseconds|	milliseconds|	milliseconds|	hours|
|Minimum storage duration|	N/A	|N/A	|30 days	|180 days|
|Usage costs|	Higher storage costs, Lower access & transaction costs	|Higher storage costs, Lower access & transaction costs	|Lower storage costs, Higher access & transaction costs	|Lowest storage costs, Highest access & transaction costs|

Premium: I/O intensive workdload (low and consistent latency). Use SSD. Many small transactions.
Hot: lowest access cost. Optimized for frequent reads and write. Default tier.
Cool: Optimized for large amount infrequently accessed. Intended for data that remain at least 30 days.
Archive: Most cost effective for storing but most expensive for accessing data.

*Immutable storage*

- Business critical data
- WORM state (Write once, Read many)
- Immutability policies applied at blob level
- Audit logs available

2 types of policy: 

- Time based retention policy:
    - During interval: can be created but not modified or deleted.
    - After: can be deleted but not modified.
    - Hot/cool/archive support this mode.
- Legal hold policy:
    - Until explicitly cleared.
    - Premium blob storage.

Consider:

- Avaibility
- Latency
- Cost
- Immutable sotrage

## Azure files

2 modes: 

- Direct mount with SMB/NFS
- Cache Azure file shares on-premises with Azure File Sync: 

Performance: 
- Standard - HDD
    - Transaction optimized: More latency than premium but optmized for heavy worload.
    - Hot: General scenario. Team share
    - Cool: Archive scenario.
- Premium - SSD

Tier:
- Premium: SSD. High performance low latency.

Azure NetApp Files : Fully managed NAS

| Comparison|	Azure Blob Storage|	Azure Files|	Azure NetApp Files|
|-----------|---------------------|------------|----------------------|
|Description|Azure Blob Storage is best suited for large scale read-heavy sequential access workloads where data is ingested once and modified later. Blob Storage offers the lowest total cost of ownership, if there's little or no maintenance.	Azure Files is a highly available service best suited for random access workloads.| For NFS shares, Azure Files provides full POSIX file system support and can easily be used from container platforms like Azure Container Instance (ACI) and Azure Kubernetes Service (AKS) with the built-in CSI driver, in addition to VM-based platforms.	Azure NetApp Files is a fully managed file service in the cloud, powered by NetApp, with advanced management capabilities.| Azure NetApp Files is suited for workloads that require random access and provides broad protocol support and data protection capabilities.|
|Use cases|	Large scale analytical data, Throughput sensitive high-performance computing, Backup and archive, Autonomous driving, Media rendering, or Genomic sequencing|	Shared files, Databases, Home directories, Traditional applications, ERP, CMS, NAS migrations that don't require advanced management, Custom applications that require scale-out file storage|	On-premises enterprise NAS migration that requires rich management capabilities, Latency sensitive workloads like SAP HANA, Latency-sensitive or IOPS intensive high performance compute, Workloads that require simultaneous multi-protocol acces|
|Available protocols|- NFS 3.0 - REST - Data Lake Storage Gen2|- SMB - NFS 4.1 - REST|- NFS 3.0 and 4.1 - SMB|
|Performance (per volume)|	Up to 20,000 IOPS, up to 15 GiB/s throughput| Up to 100,000 IOPS, up to 10 GiB/s throughput| Up to 460,000 IOPS, up to 4.5 GiB/s throughput for regular volumes, up to 10 GiB/s throughput for large volumes|

## Azure managed disk
Maximum capacity: 32 767GB

| Comparison|	Ultra-disk|	Premium SSD|	Standard SSD|	Standard HDD|
|-----------|-------------|------------|----------------|---------------|
|Disk type|	SSD|	SSD|	SSD|	HDD|
|Scenario|	IO-intensive workloads, such as SAP HANA, top tier databases like SQL Server and Oracle, and other transaction-heavy workloads|	Production and performance sensitive workloads|	Web servers, Lightly used enterprise applications, Development and testing|	Backup, Non-critical, Infrequent access|
|Max throughput|	2,000 Mbps|	900 Mbps|	750 Mbps|	500 Mbps|
|Max IOPS|	160,000|	20,000|	6,000|	2,000|

Encryption:

- Azure Disk Encryption (ADE): Disk is only accessible by the VM that owns it.
- Service Side Encrytion (SSE): Also known as "encryption at rest". Performed on the physical disk.
- Encryption at host: The VM manage the encryption.

Consider:

- Scenario/throughput/IOPs
- Data caching: OS disk default "read/write". Data disk default "read only".
- Encryption

## Security 

- Azure security baseline for Azure storage
- Shared access signature
- Firewall policies
- VNet service endpoint
- Secure transfer
- Encryption : Microsoft managed key vs customer managed key

