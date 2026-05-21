# Payroll Process Redesign for 1,800 BPO Agents

**Role:** Functional Business Analyst  
**Client:** BPO, 5 accounts, 1,800 agents 
**Timeline:** 2022–2025  
**Impact:** 95% reduction in payroll complaints | $87.5M MXN/month saved

---

## 📌 Executive Summary

Agents were leaving in droves due to incorrect pay. The root cause was not human error, but an integration gap: payroll data was pulled from Kronos (scheduled hours), ignoring actual hours worked in client CRMs. I redesigned the validation workflow, eliminated email-based adjustments, and centralized all data in a single Worked Hours Report.

**Result:** Payroll complaints dropped 95%, attrition due to pay issues fell from 15% to <2%, and the operation saved $87.5M MXN/month in avoided replacement costs.

---

## 📂 Repository Structure

| Folder / File | Description |
|---|---|
| [`/payroll-redesign/Business-case.md`](payroll-redesign/Business-case.md) | Full business case (9 sections: problem, requirements, solution, KPIs, financial impact, etc.) |
| [`/payroll-redesign/UAT-payroll.md`](payroll-redesign/UAT-payroll.md) | UAT script with 5 test cases (happy path + edge cases) |
| [`[/payroll-redesign/diagrams](https://github.com/mecrutequi/payroll-redesign/tree/main/diagrams)`](payroll-redesign/diagrams/) | AS-IS and TO-BE process diagrams (PNG) + detailed process description (MD) |

---

## 🧩 Key Artifacts

- **User Story (sample):** *"As an Operations Manager, I want a daily report cross-referencing Kronos and CRM hours, so I can identify discrepancies before they impact payroll."*
- **Business Rule (critical):** *"If an agent logs hours in the client CRM, those hours take priority over Kronos for payroll calculation, provided they have coach validation."*
- **UAT Edge Cases:** Daylight Saving Time, unapproved overtime, agent on leave, CRM vs. Kronos priority.

---

## 📈 Impact Metrics

| KPI | Before | After |
|---|---|---|
| Payroll complaints (monthly) | 120 | 6 (↓95%) |
| Attrition due to pay issues | 15% monthly | <2% monthly |
| Payroll processing time | 5 days | <1 day (↓80%) |
| Monthly replacement cost avoided | — | $87.5M MXN |

---

## 🛠️ Technologies

JIRA · Confluence · SQL Server · Excel · BPMN 2.0 (Bizagi) · Client CRM APIs · Google Forms · Kronos API

---

## 👤 Author

**Meztli Cruz** – Senior Business Analyst | [LinkedIn](https://linkedin.com/in/mecrutequi) | [GitHub](https://github.com/mecrutequi)

---

*Case study last updated: May 2026*
