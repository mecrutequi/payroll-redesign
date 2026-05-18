# payroll-redesign
Redesign of the payroll process for 5 BPO clients with a total of 1,800 agents. Functional Business Analysis case study with impact metrics.

# Payroll Process Redesign for 1,800 Agents

**Role:** Functional Business Analyst  
**Client:** Foundever (BPO with 5 accounts and 1,800 agents)  
**Timeline:** 2022-2025  

## 1. Business Problem
Agent attrition had skyrocketed. The main complaint during exit interviews was # Payroll Process Redesign for 1,800 BPO Agents

**Role:** Functional Business Analyst  
**Client:** Foundever (BPO with 5 accounts and 1,800 agents)  
**Timeline:** 2022-2025  

## 1. Business Problem
Agent attrition had skyrocketed. The main complaint during exit interviews was *incorrect pay*. Many agents left right after payday. Operations and Finance were at odds, each defending their own metrics. No one was seeing the full picture.

## 2. Requirements Gathering
I conducted active listening sessions with Operations, Finance, and WFM directors, as well as floor coaches. I discovered the root cause was not human error, but an integration gap: payroll data was pulled exclusively from Kronos (scheduled hours), completely ignoring the actual hours worked and reported in client CRMs.

## 3. Proposed Solution (AS-IS / TO-BE)
- **AS-IS:** Kronos → Payroll (no validation of actual worked hours). Exceptions and adjustments relied on scattered emails and individual goodwill.
- **TO-BE:** Client CRMs + Kronos + Coach Validation → Master Hours Report → OM Validation → Payroll.  
[View AS-IS / TO-BE Diagram]

## 4. Key Artifacts
- **Backlog & Tracking:** JIRA and Confluence.
- **Sample User Story:**
    > **As an** Operations Manager, **I want** a daily report that cross-references Kronos hours with client CRM records, **so that** I can identify discrepancies before they impact the agent's paycheck.
    **Acceptance Criteria:**
    - The report must refresh every 24 hours with the previous day's data.
    - It must highlight in red any variance greater than 5% between Kronos and the CRM.
    - It must be automatically emailed to each account's coaches.

## 5. Business Rules & UAT
The most critical business rule: **"If an agent logs hours in the client CRM, those hours take priority over Kronos for payroll calculation, provided they have coach validation."** During UAT, the finance coordinator and I ran a script covering edge cases: unapproved overtime, agents on leave, last-minute shift swaps, breastfeeding time, internet outages, power outages, one-on-one meetings with the coach.

## 6. Impact Measurement (KPIs)
| KPI | Before | After |
| :--- | :--- | :--- |
| Payroll error complaints | 120/month (avg) | 6/month (95% reduction) |
| Attrition due to payroll dissatisfaction | 15% monthly | <2% monthly |
| Payroll generation time | 5 business days | <1 day (80% reduction) |

## 7. Technologies
JIRA, Confluence, SQL Server, Excel, Client CRM APIs.
