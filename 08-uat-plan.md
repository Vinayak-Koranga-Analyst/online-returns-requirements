# 08. UAT Plan and Test Scripts: Online Returns

> **Practice case study.** Fernbridge Home is fictional.

Built from the [UAT template](https://github.com/Vinayak-Koranga-Analyst/ba-toolkit/blob/main/templates/07-uat-plan-and-script.md). Test cases are written from the acceptance criteria in the [user stories](06-user-stories.md) and traced in the [RTM](07-rtm.md).

---

## Part A: UAT plan

### 1. Purpose

To confirm, with the people who will use it, that the new returns process works end to end for customers, stores, the warehouse, finance and customer services, and meets the Must-have requirements in the [BRD](05-brd.md).

### 2. Scope

| In scope | Out of scope |
|---|---|
| End-to-end posted returns and store returns | Availability and load (NFR-01), covered by performance testing |
| Refunds, automatic and finance-approved | Carrier systems beyond label creation and scan |
| Customer services exceptions queue and returns report | Exchanges (BR-15, phase 2) |
| Accessibility check of customer pages (NFR-04) | Large furniture returns |

### 3. Approach

- **Environment:** UAT environment with OMS, website, till software and payment provider in test mode
- **Test data:** synthetic customers and orders created for UAT; no live customer data
- **Testers:** two CS advisers (S04), one CS team leader (S03), two store colleagues from the pilot stores (S08), one warehouse operative (S05's team), one finance refunds analyst (S06)
- **Duration:** two weeks, with a 15-minute defect triage each morning (BA, test lead, dev lead)
- **Tracking:** test cases and defects in Jira, linked to user stories

### 4. Entry criteria

- [ ] System and integration testing complete, with no open Critical defects
- [ ] UAT environment working end to end, including payment provider test mode and carrier label API
- [ ] Test data loaded: 40 orders across the scenarios in the tracker below
- [ ] Testers trained (1 hour) and have access
- [ ] Test scripts reviewed by CS lead, warehouse manager and finance

### 5. Exit criteria

- [ ] 100% of Must test cases run, 95% or more passed
- [ ] No open Critical or High defects
- [ ] Medium / Low defects logged with fix dates or agreed workarounds
- [ ] Sign-off from product owner (S02), finance (S06) and store operations (S07)

### 6. Defect severity

| Severity | Definition | Example in this project |
|---|---|---|
| Critical | Process can't be completed; no workaround | Refund not sent after approval |
| High | Wrong result; workaround is difficult | Refund sent to wrong payment method |
| Medium | Works with a reasonable workaround | Status email shows wrong item name |
| Low | Cosmetic | Typo on returns page |

---

## Part B: Test scripts (selected)

Full scripts are shown for the six highest-risk test cases. The rest follow the same format and are listed in the tracker in Part C.

### TC-01 Signed-in customer starts a posted return

| Field | Value |
|---|---|
| Requirement / story | BR-01, BR-04 / US-01, US-04 |
| Priority | Must |
| Preconditions | Test customer A signed in; order FH-10001 delivered 5 days ago with 2 items |
| Tester | CS adviser |

| Step | Action | Expected result |
|---|---|---|
| 1 | Open order FH-10001 in "My orders" | "Return items" button is shown |
| 2 | Select 1 item, reason "Too small", continue | Method step is shown |
| 3 | Choose "Drop off at a parcel point" and confirm | Return number shown; QR code on screen; nearest drop-off points listed |
| 4 | Check customer A's email inbox | Email with return number and QR code received |
| 5 | Open the return in the OMS as a CS user | Return exists, linked to FH-10001, status Requested, reason "Too small" |

### TC-03 Ineligible items can't be returned

| Field | Value |
|---|---|
| Requirement / story | BR-02 / US-02 |
| Priority | Must |
| Preconditions | Order FH-10003 delivered 35 days ago; order FH-10004 contains a made-to-order sofa cushion (excluded) |

| Step | Action | Expected result |
|---|---|---|
| 1 | Open order FH-10003 | Items can't be selected; message "Return window closed on [date]" |
| 2 | Open order FH-10004 | Excluded item can't be selected; reason shown |
| 3 | Select "Ask for a review" on FH-10004 | Confirmation shown; case appears in CS exceptions queue (check as CS user) |

### TC-09 Store colleague finds an online order at the till

| Field | Value |
|---|---|
| Requirement / story | BR-08, NFR-02, NFR-03 / US-08 |
| Priority | Must |
| Preconditions | Customer B has a store return QR code for order FH-10010; customer C has order FH-10011 with no QR code |
| Tester | Store colleague |

| Step | Action | Expected result |
|---|---|---|
| 1 | Scan customer B's QR code at the till | Return and items appear within 3 seconds (time with stopwatch, 5 attempts) |
| 2 | Check what is shown | Order number, items, delivery date and payment method type only. **No** full address or card number |
| 3 | Search for FH-10011 using order number and postcode | Order appears |
| 4 | Search for FH-10011 with the wrong postcode | "No matching order"; no details shown |

### TC-10 Store colleague accepts a return and refunds at the till

| Field | Value |
|---|---|
| Requirement / story | BR-08 / US-09 |
| Priority | Must |
| Preconditions | Customer B's return found (TC-09); item in good condition; paid by card |

| Step | Action | Expected result |
|---|---|---|
| 1 | Confirm the item is in acceptable condition and accept the return | Refund sent to original card in payment provider test portal |
| 2 | Check return status in the OMS | Status Refunded; history shows store and colleague ID |
| 3 | Check till printer | Returns slip printed with return number and barcode |
| 4 | Repeat with a damaged item; select "Can't accept", reason "Damaged by customer" | No refund; reason required; customer note printed |

### TC-13 Approved posted return is refunded automatically

| Field | Value |
|---|---|
| Requirement / story | BR-11, NFR-06 / US-12 |
| Priority | Must |
| Preconditions | Return from TC-01 scanned as Received (TC-11); item value £45 |
| Tester | Warehouse operative, then finance analyst to check |

| Step | Action | Expected result |
|---|---|---|
| 1 | Record inspection result Approved, grade A | Status changes to Approved |
| 2 | Wait up to 1 hour; check payment provider test portal | £45 refund to original payment method |
| 3 | Check the OMS and customer A's email | Status Refunded; refund email received with amount and payment method |
| 4 | Set the payment provider test mode to decline the next refund, then repeat steps 1–2 with a second return | Return flagged for finance; customer **not** told it's refunded |

### TC-14 Refund over £250 needs finance approval

| Field | Value |
|---|---|
| Requirement / story | BR-12 / US-13 |
| Priority | Must |
| Preconditions | Order FH-10020: one item at £320, return Received |
| Tester | Warehouse operative, then finance analyst |

| Step | Action | Expected result |
|---|---|---|
| 1 | Record inspection result Approved | Status Approved; **no** refund sent |
| 2 | As finance, open "Refunds to approve" | FH-10020 return listed with value £320 |
| 3 | Hold the refund without a reason | Not allowed: reason required |
| 4 | Hold with reason "Checking with supplier" | Status unchanged; reason visible to CS user |
| 5 | Approve the refund | Refund sent; status Refunded |

---

## Part C: Test tracker

| TC | Title | Story | Priority | Tester | Status |
|---|---|---|---|---|---|
| TC-01 | Signed-in customer starts a posted return | US-01, US-04 | Must | CS adviser | Not run |
| TC-02 | Guest starts a return with order number and email | US-01 | Must | CS adviser | Not run |
| TC-03 | Ineligible items can't be returned | US-02 | Must | CS adviser | Not run |
| TC-04 | Return reason is required | US-03 | Should | CS adviser | Not run |
| TC-05 | Parcel-point QR label issued | US-04 | Must | CS adviser | Not run |
| TC-06 | Store return QR code issued | US-04 | Must | CS adviser | Not run |
| TC-07 | Status history recorded and shown online | US-05, US-06 | Must | CS team leader | Not run |
| TC-08 | Email and text notifications | US-07 | Should | CS adviser | Not run |
| TC-09 | Till order look-up and data shown | US-08 | Must | Store colleague | Not run |
| TC-10 | Accept return and refund at the till | US-09 | Must | Store colleague | Not run |
| TC-11 | Scan return on arrival, including unlabelled parcels | US-10 | Must | Warehouse operative | Not run |
| TC-12 | Record inspection result and grade | US-11 | Must | Warehouse operative | Not run |
| TC-13 | Automatic refund on approval | US-12 | Must | Warehouse / finance | Not run |
| TC-14 | Finance approval over £250 | US-13 | Must | Finance analyst | Not run |
| TC-15 | CS exceptions queue | US-14 | Must | CS team leader | Not run |
| TC-16 | Returns report figures match test data | US-15 | Should | CS team leader | Not run |
| TC-17 | Accessibility check of returns pages (keyboard and screen reader) | US-01 – US-07 | Must | Accessibility tester | Not run |
| TC-18 | Audit log of status changes and refunds | US-05, US-12 | Must | Finance analyst | Not run |

## Sign-off

| Role | Decision | Date |
|---|---|---|
| Product owner (S02) | | |
| Finance (S06) | | |
| Store operations (S07) | | |
