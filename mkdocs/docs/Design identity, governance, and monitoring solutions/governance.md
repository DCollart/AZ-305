# Core architectural components

## Management group

Things to consider
- Design management groups with governance in mind
- Keep the management group hierarchy reasonably flat
- Consider a top-level management group
- Consider an organizational or departmental structure
- Consider a geographical structure
- Consider a production management group
- Consider a sandbox management group
- Consider isolating sensitive information in a separate management group

## Subscription

- Treat subscriptions as a democratized unit of management
- Group subscriptions together under management groups
- Consider a dedicated shared services subscription
- Consider subscription scale limits
- Consider administrative management
- Consider how to assign Azure policies
- Consider network topologies
- Consider making subscription owners aware of their roles and responsibilities

## Resource groups

- Consider group by type
- Consider group by app
- Consider group by department, group by location (region), and group by billing (cost center)
- Consider a combination of organizational strategies
- Consider resource life cycle
- Consider administration overhead
- Consider resource access control
- Consider compliance requirements

## Tags

- Consider your organization's taxonomy
- Consider whether you need IT-aligned or business-aligned tagging
- Consider the type of tagging required
   - Functional
   - Classification
   - Accounting
   - Partnership
   - Purpose
- Consider starting with a few tags and then scale out
- Consider using Azure policy to apply tags and enforce tagging rules and conventions
- Consider which resources require tagging

## Policy
- Consider using the Azure Policy compliance dashboard
- Consider when Azure Policy evaluates resources
   - A resource is created, deleted, or updated in scope with a policy assignment.
   - A policy or an initiative is newly assigned to a scope.
   - An assigned policy or initiative for a scope is updated.
   - The standard compliance evaluation cycle (occurs once every 24 hours)
- Consider how to handle a noncompliant resource
   - Deny changes to the resource.
   - Log changes to the resource.
   - Alter the resource before or after the change.
   - Deploy related compliant resources.
- Consider when to automatically remediate noncompliant resources
- Consider how Azure Policy is different from role-based access control (RBAC)

## RBAC

- Consider the highest scope level for each requirement
- Consider the access needs for each user
- Consider assigning roles to groups, and not users
- Consider when to use Azure policies
- Consider when to create a custom role
- Consider how to resolve overlapping role assignments

## Landing zone

- Consider including landing zones in your design
- Consider creating landing zones through code
- Consider using the Azure landing zone accelerator
- Consider focusing on your applications
- Consider Azure-native design and aligning with the platform
- Consider scoping for both migrations and green field situations
- Consider transitioning existing architectures to Azure landing zones