# salesforce-crm-portfolio
Portfolio-ready Salesforce CRM project built in Trailhead (docs, data, screenshots).
# Salesforce CRM Portfolio — Lead to Opportunity

A portfolio-ready CRM built in a Trailhead Playground.

## Problem
Leads scattered in spreadsheets, missed follow-ups, and no pipeline visibility.

## Solution
- Standard objects (Lead, Account, Contact, Opportunity)
- Optional custom object `Customer_Interaction__c`
- Record-Triggered Flows for lead assignment & stage tasks
- Validation rules and executive dashboard

## Impact Targets
- Lead response time: 36h → 14h (‑61%)
- Lead→Opp conversion: 22% → 35% (+13 pp)
- Manual task creation: ~70% reduction

## Docs & Data
- [Business Scenario](./docs/BusinessScenario.md)
- [Build Guide](./docs/BuildGuide.md)
- Sample data in `/data` (CSV) for imports

## Screenshots
Add flows, validation rules, and dashboards under `/images`.

Text-Based Diagram

flowchart LR
    A[Lead Created] -->|Flow A assigns + creates Task| B[Lead Owner / Queue]
    B -->|Rep makes first call| C[Flow B logs First Response Date]
    C -->|Lead Qualified| D[Convert Lead]
    D --> E[Account Created]
    D --> F[Contact Created]
    D --> G[Opportunity Created]

    G -->|Flow C sets SLA Start Date| H[SLA Tracking]
    H -->|Idle > 7 Days| I[Flow C creates Follow-up Task]

    subgraph Validation Rules & Data Quality
        V1[Lead must have Email/Phone]
        V2[Prevent duplicate Leads/Contacts]
        V3[Opportunity in Proposal must have Amount + Close Date]
    end

    A --> V1
    A --> V2
    G --> V3
