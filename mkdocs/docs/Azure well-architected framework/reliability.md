# Reliability

## Identify reliability targets

- Quantify success by setting targets on indicateds for individual components/system/flow/system as a whole
- Metrics quantify expectations
- Target values indicate an ideal state

Understand platform commitments

- Understand guaranteed reliability metrics provided by cloud platform
- Consider limits/quota/capacity constraints
- SLA vary by service

Determine dependencies and their effect on resiliency

- Document all dependencies (internal or external)
- Identify how malfunctions may affect your flows

## Design for resilience

Determine failure risks

- Identify potential failure points
- Determine effects on user and flows
- Analyze the failure case, blast radius and intensity of fault for each potential failure point.

Implement self-preservation mechanism

- Build self-preservation capabilities
- Prevent a problem from affecting downstream components to minimize blast radius

Build comprehensive redundancy and resiliency

- Aim for redundancy in physical utilities and immediate data replication
- Redundancy helps minimize SPOF
- Adding intermediaries prevents direct dependency between components and improves buffering
- Failure mode analysis

## Design for recovery

Be prepared for disasters 

- Have structured, tested and documented recovery plans aligned with the recovery targets
- Plans must cover all components 

Address stateful data

- Ensure you can repair data of all statefull components
- Backup
- Immutable and transactionnaly consistent backup ensure data can't be altered or corrupted

 Implement automated self-healing capabilities
 
 - Allow component to automatically resolve issues by recovering affected components if needed or failing over to redundant infrastructure.

## Design for operations

Implement robust monitoring

- Build observable systems that can correlate telemetry

Predict potential malfunctions and anomalous behavior

- Make active reliability failures visible by using prioritized and actionable alerts

Test for reliability risks

- Simulate failures and run tests in production and pre-production environements

## Keep it simple

Minimize the workload components 

- Add components only if they help achieve target business values
- Keep critical path lean

Standardize your software developement lifecycle

- Establish standards in code implementation/deployment/processes and document them
- Identify opportunities to enforce those standards by using automated validations

Minimize your operations and developement burden

- Take advantage of platform-provided features and prebuilt assets 
