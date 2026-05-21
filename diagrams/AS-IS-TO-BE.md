# Summary

## Process Description: AS-IS vs TO-BE

### AS-IS (Current State)

The current process for integrating worked hours into payroll is highly manual and decentralized. It operates on a 14-day cycle and involves three departments: Finance, WFM, and Operations.

**How it works today:**

1. **Finance** initiates the process every 14 days by requesting worked hours from WFM.
2. **WFM** retrieves raw data from Kronos (punch in/out records) and sends it to Operations for validation.
3. **Operations** manually validates whether the Kronos data matches the client's CRM records (hours on the phone).
   - If the data is accurate, Operations sends an approval via email.
   - If inaccurate, Operations sends adjustments via email.
4. **WFM** must manually search their personal email inbox for adjustments, apply corrections, and update the report.
5. The final report is sent to Finance as an email attachment.

**Key issues:**
- Information is scattered across personal email inboxes.
- No integration between Kronos, CRM, and email.
- WFM operators manually search for adjustment emails.
- No standardized format for adjustment emails → risk of errors.
- No traceability of who made adjustments or when.
- Finance receives reports as unstructured email attachments.

---

### TO-BE (Future State)

The proposed future state eliminates email-based communication and centralizes all data in a structured, automated workflow.

**How it will work:**

1. **Operations** records worked hours in Kronos and, if needed, adjusts hours using **Forms** (structured system for compliance and corrections).
2. Adjustments are automatically sent from Operations to WFM via a sequence flow (no email).
3. **WFM** updates the consolidated **Worked Hours Report** by pulling data directly from:
   - Kronos (actual worked hours)
   - CRM (billable client hours)
   - Forms (adjustments and compliance data)
4. A **XOR gateway** validates if *Kronos = CRM*:
   - **Yes**: The report is updated and continues to the 14-day check.
   - **No**: Adjustments are processed via Forms, and the report is updated again.
5. After 14 days, the final report is sent directly to Finance via a sequence flow (no email attachment).
6. **Finance** receives the report and processes payroll directly from the **Worked Hours Report**.

**Key benefits:**
- ✅ Centralized Worked Hours Report (single source of truth).
- ✅ Automated flow of adjustments (no manual email search).
- ✅ Full traceability of all adjustments and approvals.
- ✅ Standardized data entry via Forms.
- ✅ No email attachments → direct system-to-system flow.
- ✅ Clear decision logic with XOR gateway.

---

### Summary of Improvements

| Aspect | AS-IS | TO-BE |
|--------|-------|-------|
| Communication | Manual emails | Automated sequence flows |
| Data repository | Personal email inboxes | Centralized Worked Hours Report |
| Adjustments | Manual search by WFM | Automated from Ops to WFM |
| Format | Unstructured emails | Structured Forms |
| Traceability | None | Full (Forms + Report) |
| Report delivery | Email attachment | Direct sequence flow |
| Validation | Human judgment | XOR gateway decision |


The TO-BE eliminates emails, centralizes all information in the **Worked Hours Report**, and automates the flow of adjustments and validations.

| # | AS-IS Pain Point | TO-BE Solution |
|---|------------------|----------------|
| 1 | Information scattered across personal email inboxes – no central repository | Centralized **Worked Hours Report** in WFM (single Data Store) |
| 2 | No integration between Kronos and email – manual data transfer required | Direct data associations between Kronos, CRM, Forms, and the consolidated report |
| 3 | WFM operator must manually search emails for adjustments – no automated trigger | Automated flow from *Send the adjustments to WFM* → *Receive the adjustments from Ops* → *Update the report* |
| 4 | No standardized format for adjustment emails – risk of misinterpretation and errors | **Forms** as a structured system for recording adjustments (no loose emails) |
| 5 | No traceability – who approved or adjusted what, and when, is not recorded | Forms logs every adjustment. **Worked Hours Report** consolidates with full traceability |
| 6 | Report reaches Finance as an email attachment – no shared system or audit trail | *Send the final report* → direct sequence flow to Finance (no email) |
| 7 | Manual corrections without a system | *Adjust hours using Forms* → structured task embedded in the process |
| 8 | Validation without clear criteria | XOR gateway *Kronos = CRM?* → automated decision |

# Diagrams
AS-IS and TO-BE process diagrams for the payroll redesign project.

# Worked hours Integration to Payroll – AS-IS Process

## Process overview
Current state process for payroll integration between Finance, WFM, and Operations. Payroll runs every 14 days.

## Pain points
- Information scattered across personal email inboxes – no central repository for adjustments or approvals.
- No integration between Kronos and email – manual data transfer required.
- WFM operator must manually search emails for adjustments – no automated trigger.
- No standardized format for adjustment emails – risk of misinterpretation and errors.
- No traceability – who approved or adjusted what, and when, is not recorded.
- Report reaches Finance as an email attachment – no shared system or audit trail.


# Worked Hours Integration to Payroll – TO-BE Process

## Process overview
Proposed future state process for payroll integration between Finance, WFM, and Operations.  
Payroll runs every 14 days based on a consolidated report generated by WFM.

## Solutions (vs AS-IS)
- Centralized Worked Hours Report in WFM (single Data Store).
- Direct data associations between Kronos, CRM, Forms, and the consolidated report.
- Automated flow from *Send the adjustments to WFM* → *Receive the adjustments from Ops* → *Update the report*.
- Forms as a structured system for recording adjustments (no loose emails).
- Forms logs every adjustment. Worked Hours Report consolidates with full traceability.
- *Send the final report* → direct sequence flow to Finance.
- *Adjust hours using Forms* → structured task embedded in the process.
- XOR gateway *Kronos = CRM?* → automated decision.

## Key improvements
- ✅ Eliminates manual email-based communication.
- ✅ Centralizes all adjustment and approval data.
- ✅ Enables full traceability of corrections.
- ✅ Automates the validation and reporting cycle.
- ✅ Removes dependency on personal email inboxes.
