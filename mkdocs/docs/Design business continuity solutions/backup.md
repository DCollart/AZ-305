# Backup

- Workload: distinct capability or task that is logically separated from other tasks.  Each workload probably has different requirements for availability, scalability, data consistency, and disaster recovery.
- Usage pattern: can determine your requirements. Critical vs non-critical periods.
- Availaibility metrics:
    - MTTR (mean time to recovery)
    - MTBF (mean time between failure).
- Recovery metrics: 
    - RTO (recovery time objective)
    - RPO (recovery point object)
    - RLO (recovery level objective): Granularity of recovery.

## Azure backup

On premise
- Files/folders/system state: MARS agent (Microsoft Azure Recovery Service)
- VM: System Center Data Protection Manager (DPM)
- VM: MABS: Microsoft Azure Backup Server

Azure VM:
- Backup extension
- MARS agent

Azure Files 
- To a storage account

Vaults: Stores backup copies, recovery points and backup policies.

Two type of vaults:
- Azure Backup: Azure database, Azure blobs and Azure disks
- Azure recovery services: Azure VM, File share. MARS/MABS/DPM.

- Consider vault organization. One vault by subscription ? Use separate vaults for Azure Backup and ASR.
- Azure policy for consistency.
- RBAC.
- Redundancy 

# Azure blob

- Backup stored in source Azure storage account instead of vault
- Continuous backup (no schedule)
- Retained for a specified period of time and restorable from a selected point in time.
- Soft delete (blob and container).
- Retention for deleted blob/container between 1 and 365 days. Default is 7 days.
- Blob versioning.
- Point in time restore
- Resource lock

# Azure files
Can take snapshots of file shares. 
- Stored in vault
- Automated with Azure Backup and backup policies
- Apply at root level 
- Retrieval is at individual file level
- Snapshot are incremental
- Snapshot can be read/copied/delete but not modified
- Can't delete a share that has share snapshots
- Azure backup keeps snapshot metada in Recovery Services vault
- When Azure backup is enable the soft delete feature is also enabled.
- Can configure for daily/weekly/monthly/yearly retention.

- Instant restore : Azure file share backup uses file share snapshot.
- Alert  and reporting for backup/restore failures.
- Self-service restore: Azure backup uses server endpoint Windows Volume Shadow Copy Service (VSS) snapshot.
- On-demand backup
- File share organization
- Take snapshot before deploying application code.

# Azure VM

- Two phases 
    - First a VM snapshot is taken
    - Second the snapshot is transferred to a Recovery Services Vault.
- Snapshot backup supports different levels of consistency : Application, system and crash.
- Backup are encrypted at rest with Storage Service Encryption (SSE).

- Backup schedule (during non peak production application time)
- Backup frequency: both short term and long term.
- Backup policies. Single backup policy for a group of VM requiring the same schedule/retention settings.
- Practice restore run. 
- Throttling during restore. ?
- Cross Region Restore (CRR) to restore VM in a secondy region.

## Azure SQL

- Full backup (everything in the database and the transactions logs) every week.
- Differential backup (every change since the last full backup) every 12/24h.
- Transactional backup every 5/10 minutes.

- Restore to an existing database to a point in time in the past. Restore on the same server but use different name.
- Restore a deleted database to the time of deletion. Same server only.
- Restore a database to another region. 
- Restore a database from a specific long term backup.

- Automatic backup remain available up to 35 days.
- Can use long term retention (LTR).
- LTR will store Azure DB backup in RA-GRS blob for up to 10 years.

## Azure site recovery

Business continuity and disaster recovery (BCDR) solution.

- Replicate server/VM (Azure or on prem)