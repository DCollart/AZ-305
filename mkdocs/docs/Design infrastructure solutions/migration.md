# Design migration

## Cloud adoption framework

![cloud adoption framework](img/cloud-adoption-framework.png)
![migration methodology](img/migrate-methodology.png)

## Azure mgiration framework

4 stages

### Assess

- Identify app/server/services/data in the migration scope.
- Involve stakeholder (IT dep, business).
- Create full inventory and dependency map.
- Estimate your cost (Azure Total Cost of Ownership)
- Identify tools to perform the 4 stages.

*Migration strategy pattern*
5 strategy patterns called 5 Rs of rationalization.

- Rehost (lift and shift): Just move the existing.
- Refactor: Do minimal change so they can connect to PaaS
- Rearchitect: Modifying and extending app. (By example monolith => microservices)
- Rebuilding
- Replace

### Migrate

- Deploy cloud infrastructure target (Azure migrate/Azure database migration service)
- Migrate workload: Better to start with a non critical app.
- Decommission on-prem

### Optimize

- Analyze migration cost (Microsoft Cost Management)
- Review recommendation for reducing your costs
- Identify options for improving performance

### Monitor

## Assess on-prem workload

- Service map of Azure monitor maps communication between app component on Windows or Linux. 
- Azure TCO calculator: Estimation the cost saving.
- Azure migrate: Assess and migrate of VM (hyper-V and VMware), cloud based virtual machine, physical server, ...
- SQL Server Data migration assistant (DMA): Detect compatibility issues that might impact database functionality
- Database migration service: perfoms assessment and migration for different databases
- Azure cosmos DB Data migration tool: Migrates existing DB to Azure Cosmos DB
- Microsoft Cost Management: Monitor/optimize/control ongoing Azure costs
- Azure Advisor: Helps optimize resources for reliability, performance, cost, security and opertional excellence.
- Azure Monitor
- Microsot Sentinel: SIEM

## Select migration tool

- Unified migration platform: Single portal where you can perform migration to Azure and track migration status.
- Assessment and migration tools: Supplies several assessment and migration tools including Server Assessment, Server Migration, ...
- 


## Migrate structure data in databases

### Azure database migration service
Can be used to migration on-prem databases

Online migration: Continuous synchronization of live data. Minimize downtime.
Offline migration: Require shutting down the server at the start of the migration.

3 steps:

- Assess DB
- Migrate schema
- Migrate data and verify

## Migrate unstructured data

### Azure storage migration service

3 steps :

- Inventory servers
- Transfer data
- Cut over (option) 

### Azure file sync

## Migrate offline data

### Azure import/export service

- Only to Azure blob storage
- Can't export data in Azure files
- Bitlocker must be enabled

### Azure Data box