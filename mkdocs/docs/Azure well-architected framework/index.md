# Introduction to Azure well architected framework

## Pillars
5 pillars:

-   Cost optimization
-   Operational excellence:
- Faster development and deployment cycles
- Good monitoring. Detect dailure.
- Automatisation is a key aspect of this pillar.
-   Performance efficiency
-   Reliability
-   Security

Design principles:

- Enable architectural evolution
- Use data to make decisions
- Educate and enable
- Automate

## Cost optimization
Owning equipement is capital expense (capex)
Cloud is operating expense (opex)
PaaS typically cost less than IaaS and reduce operational costs.

## Operational excellence
Devops and CI/CD
Monitoring and analytics
Automation
Test

## Performance efficiency
Scale up => Adding more resources to a single instance (vertical scaling)
Scale out => Adding more instances (horizontal scaling)
Autoscaling: Dynamically allocating resources to match requirements.

## Reliability

Clustering replace a single VM with a set of coordinated VMs.
Load balancing spread request across many instances.

Recovery point objective (RPO): Maximum duration of acceptable data loss.
Recovery time objective (RTO): Maximum duration of acceptable downtime.

## Security
Defense in depth (with example):

- Data: Exposing encryption key...
- Applications: Malicious code injection (SQL injection or XSS).
- VM/Compute: Malware
- Networking: Leaving some ports open
- Perimeter: DoS
- Policies and access: Authentication/Authorization
- Physical security: Unauthorized acess to facilities.