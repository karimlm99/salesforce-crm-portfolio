# Build Guide — CRM System (Lead to Opportunity)

This guide describes the exact steps taken to build the CRM portfolio project in a Salesforce Trailhead Playground.

---

## 1. Data Model Setup
- **Standard Objects Used:** Lead, Account, Contact, Opportunity, Task, Event.
- **Custom Object Created:** `Customer_Interaction__c`
  - Fields:
    - `Interaction_Type__c` (Picklist: Call, Email, Meeting)
    - `Interaction_Date__c` (Date)
    - `Notes__c` (Long Text Area)
    - `Contact__c` (Lookup → Contact)
    - `Opportunity__c` (Lookup → Opportunity, optional)

---

## 2. Automation (Flows)
1. **Lead Nurture & Assignment (Record-Triggered Flow)**
   - When a Lead is created:
     - If Source = "Web" → assign to Inbound Queue.
     - Else → round-robin assignment to Sales reps.
     - Auto-create Task: "Call new lead" due next business day.
     - Send auto-response email.

2. **First Response SLA (Flow + Formula Field)**
   - Capture first completed Task date as `First_Response_Date__c`.
   - Formula field calculates hours between Lead creation and first response.
   - Report tracks % of Leads responded to within 24 hours.

3. **Opportunity Stage Follow-Up (Record-Triggered Flow)**
   - On Stage change:
     - Auto-create stage-specific tasks (Discovery call, Proposal, Negotiation).
     - If no Activity for 7 days → auto-create "Nudge" Task + send notification.

---

## 3. Data Quality Controls
- **Validation Rules**
  - On Opportunity: If Stage = Proposal, then Amount + Close Date required.
  - On Lead: If Status = Qualified, then Company + Email required.
- **Picklist Standardization**
  - Lead Source, Industry, Opportunity Stage.
- **Duplicate Rules**
  - Block duplicate Leads/Contacts by Email.

---

## 4. Lightning App & UX
- Custom **Sales Console App**.
- **Record Pages**
  - Lead: Path (Status), Activity Timeline, Related Lists.
  - Opportunity: Path (Stage), Key Fields, Related Contacts.
- **Quick Action**
  - "Log Interaction" to create a Customer Interaction record.

---

## 5. Reports
- Leads by Source & Status.
- Lead-to-Opportunity Conversion Rate.
- Opportunity Pipeline by Stage & Owner.
- Idle Opportunities (No Activity ≥ 7 days).
- SLA Compliance (% responded within 24h).

---

## 6. Dashboards
- **Executive Sales Overview**
  - Total Pipeline
  - Won this Month
  - Conversion Rate
  - SLA Compliance %
  - Top Opportunities
  - Follow-ups Due Today

---

## 7. Demo Data
Import dummy dataset (CSV files provided in `/data` folder):
- Leads.csv
- Accounts.csv
- Contacts.csv
- Opportunities.csv
- Customer_Interactions.csv

Use the **Data Import Wizard** to load them into your Trailhead Playground.

---

## 8. Screenshots to Capture
For portfolio presentation, add screenshots under `/images`:
- Flow: Lead Nurture & Assignment.
- Flow: Opportunity Stage Follow-Up.
- Validation Rules.
- Lead & Opportunity Path UI.
- Executive Dashboard.
