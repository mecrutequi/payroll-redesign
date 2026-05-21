# UAT Script: Payroll Validation Process

**Project:** Payroll Process Redesign
**Role:** Functional Business Analyst
**Date:** 2024

## Test Case 1: Happy Path – Standard Agent with Matching Hours

| Step | Action | Expected Result | Pass/Fail |
|:---|:---|:---|:---|
| 1 | Agent works 40 hours in week 1. Kronos shows 40. CRM shows 40. | Master Report shows 40 hours. No discrepancy flagged. | ✅ Pass |
| 2 | Payroll processes the report. | Agent is paid for 40 hours. No complaint filed. | ✅ Pass |

## Test Case 2: Edge Case – CRM Hours Take Priority Over Kronos

| Step | Action | Expected Result | Pass/Fail |
|:---|:---|:---|:---|
| 1 | Agent works 45 hours in week 2. Kronos shows 40 (scheduled). CRM shows 45 (actual). | Master Report flags discrepancy. CRM hours (45) take priority per business rule. | ✅ Pass |
| 2 | Coach validates the 5 extra hours. | Report updates to 45 validated hours. | ✅ Pass |
| 3 | Payroll processes the report. | Agent is paid for 45 hours. No complaint filed. | ✅ Pass |

## Test Case 3: Edge Case – Unapproved Overtime

| Step | Action | Expected Result | Pass/Fail |
|:---|:---|:---|:---|
| 1 | Agent works 50 hours. CRM shows 50. Kronos shows 40. | Master Report flags 10-hour discrepancy. | ✅ Pass |
| 2 | Coach does NOT validate the extra hours. | Report keeps 40 hours as final. | ✅ Pass |
| 3 | Payroll processes. | Agent is paid for 40 hours. Overtime not approved. | ✅ Pass |

## Test Case 4: Edge Case – Agent on Leave

| Step | Action | Expected Result | Pass/Fail |
|:---|:---|:---|:---|
| 1 | Agent is on vacation all week. Kronos shows 0. CRM shows 0. | Master Report shows 0 hours. No discrepancy. | ✅ Pass |
| 2 | Payroll processes. | Agent receives vacation pay (not hourly). No complaint. | ✅ Pass |

## Test Case 5: Edge Case – Daylight Saving Time

| Step | Action | Expected Result | Pass/Fail |
|:---|:---|:---|:---|
| 1 | Clock changes. Agent works 9 hours but Kronos shows 8 due to time shift. | Master Report flags 1-hour discrepancy. CRM data validates the 9 hours. | ✅ Pass |
| 2 | Payroll processes. | Agent is paid for 9 hours. No complaint. | ✅ Pass |

## UAT Summary

| Total Test Cases | Passed | Failed | Blocked |
|:---|:---|:---|:---|
| 5 | 5 | 0 | 0 |

All defects were documented in JIRA with screenshots and followed up until closure.
