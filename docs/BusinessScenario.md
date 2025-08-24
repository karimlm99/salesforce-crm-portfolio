
# Business Scenario — CRM System (Lead to Opportunity)

## Company Snapshot
**BrightPath Consulting** is a 12-person B2B services firm that sells fixed-fee analytics packages to SMEs. Leads arrive via a web form and cold outreach. Sales is run by the founder and two reps.

---

## Problem Faced by the Business
- Leads are tracked in spreadsheets, causing missed follow-ups and duplicate outreach.  
- No single source of truth for customer communications (emails/meetings live in inboxes).  
- Managers lack pipeline visibility: no reports on forecast or stuck deals.  
- Data quality issues — manual updates lead to inconsistent lead/opportunity records.  
- No repeatable process for new sales reps from **Lead → Opportunity → Closed Won**.

---

## Objectives
1. Centralize leads, accounts, contacts, opportunities, and interactions in Salesforce.  
2. Automate follow-ups and task assignments to reduce manual work.  
3. Provide managers with executive dashboards for pipeline, conversion rates, and SLAs.  
4. Improve data quality through validation rules and required fields.  
5. Standardize the lead conversion process and opportunity stages.

---

## Salesforce Solution Designed
- **Standard Objects Used:** Lead, Account, Contact, Opportunity, Task, Event.  
- **Custom Object:** `Customer_Interaction__c` (fields: Interaction Date, Type, Notes, Contact lookup, Opportunity lookup).  

### Key Features
- **Data Model**  
  - Lead → Conversion → Account, Contact, Opportunity.  
  - Custom object `Customer_Interaction__c` linked to Contact/Opportunity.  

- **Automation (Flows)**  
  - Lead assignment based on source (Inbound vs. Outbound).  
  - Auto-create follow-up tasks for sales reps.  
  - SLA tracking: stamp first response date/time.  
  - Stage-based task creation for Opportunities.  
  - Alerts for Opportunities with no activity after 7 days.  

- **Data Quality**  
  - Validation rules: ensure required fields at key stages.  
  - Picklists for Lead Source, Industry, Opportunity Stage.  
  - Duplicate rules to prevent multiple Leads/Contacts with same email.  

- **UX Enhancements**  
  - Custom Sales Console App.  
  - Lightning record pages with Paths for Leads & Opportunities.  
  - Quick Action: “Log Interaction” to add Customer Interactions.  

- **Reports & Dashboards**  
  - Leads by Source & Status.  
  - Lead-to-Opportunity Conversion Rate.  
  - Opportunity Pipeline by Stage.  
  - Idle Opportunities (No Activity ≥ 7 days).  
  - SLA: First Response within 24h (%).  
  - **Executive Sales Overview Dashboard.**

---

## Business Impact (Measurable Outcomes)
- **Lead response time**: reduced from **36h → 14h** (-61%).  
- **Lead-to-Opportunity conversion rate**: increased from **22% → 35%** (+13 pp).  
- **Manual task creation**: reduced by ~70% through automation.  
- **Forecast confidence**: within ±10% of actuals at month-end.  
- **Stuck deals**: reduced by 45% (Opportunities idle ≥ 7 days).  

---

## Next Steps
- Phase 2: add CPQ/Quote management, contract lifecycle, and email integration.  
- Explore Einstein Activity Capture for automated email/calendar logging.  
