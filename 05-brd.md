# 05. Business Requirements Document: Online Returns

> **Practice case study.** Fernbridge Home is fictional and all figures are illustrative.

**Version:** 1.0 (baselined) | **Author:** Business Analyst | **Sponsor:** Director of Customer Operations (S01) | **Product owner:** Head of Ecommerce (S02)

Built from the [BRD template](https://github.com/Vinayak-Koranga-Analyst/ba-toolkit/blob/main/templates/03-brd.md).

## Document control

| Version | Change | Approved by |
|---|---|---|
| 0.1 | First draft after workshops 1–3 | – |
| 0.2 | Added store returns and refund approval rules after workshop 4 | – |
| 1.0 | Baselined for build | Sponsor, product owner |

## 1. Executive summary

Fernbridge Home handles around 1,800 online returns a month through email, phone and a shared spreadsheet. Refunds take an average of 12 days, and about a third of customer services calls are customers chasing a return. This document sets out the business requirements for a self-service returns process: customers start and track returns online, can drop them off by post or in any store, and get refunds automatically once the item is checked. The target is to cut average refund time to 5 days or fewer and halve return-related calls within six months of go-live.

## 2. Problem statement

> *The problem of* a manual, email-based returns process *affects* online customers, customer services, the returns warehouse and finance, *and results in* slow refunds, high call volumes and poor visibility of returned stock. *A good solution would* let customers start and track a return themselves, and pass each return between teams automatically.

Evidence and root causes are in the [project brief](01-project-brief.md) and the [as-is process](03-as-is-process.md).

## 3. Objectives

| ID | Objective | Baseline | Target (6 months after go-live) |
|---|---|---|---|
| OBJ-01 | Refund customers faster | 12 days average | 5 days or fewer |
| OBJ-02 | Reduce avoidable contact | 33% of calls about returns | 15% or less |
| OBJ-03 | Let customers return online orders in store | 0 of 40 stores | 40 of 40 stores |
| OBJ-04 | Know where every returned item is | Spreadsheet only | 100% of returns tracked in the OMS |

## 4. Scope

See the [project brief](01-project-brief.md#5-scope). In short: parcel-delivered online orders, self-service returns, prepaid labels, store returns, tracking and automatic refunds are in scope. Large furniture, exchanges, marketplace orders and changes to the 30-day policy are out of scope.

## 5. Stakeholders

See the [stakeholder register and RACI](02-stakeholders.md). The product owner (S02) is accountable for this document. Finance (S06) is accountable for refund rules and the Data Protection Officer (S10) for the DPIA.

## 6. Business requirements

Priority uses MoSCoW. Sources are the four requirements workshops (W1–W4) and the as-is pain points (P1–P8).

### 6.1 Starting a return

| ID | Requirement | Rationale | Priority | Source | Objective |
|---|---|---|---|---|---|
| BR-01 | Customers need to start a return online for items from an online order, without contacting customer services. | Removes the email/phone step and 1.5 days of waiting | M | P1, W1 | OBJ-01, OBJ-02 |
| BR-02 | The business needs eligibility checked automatically at the point of request: within 30 days of delivery, and not an excluded item (e.g. made-to-order, opened bedding). | Stops ineligible returns early and removes a manual check | M | W1 | OBJ-01 |
| BR-03 | The business needs to capture a return reason for every item, from a fixed list. | Feeds product and supplier quality reporting | S | W1, W3 | OBJ-04 |
| BR-04 | Customers need a choice of return method: drop off a parcel at a carrier point using a prepaid QR label, or take the item to any store. | Removes the cost and effort of posting; addresses store turn-aways | M | P5, P8, W2 | OBJ-01, OBJ-03 |

### 6.2 Tracking

| ID | Requirement | Rationale | Priority | Source | Objective |
|---|---|---|---|---|---|
| BR-05 | The business needs each return held as a single record in the OMS, with a full status history (Requested, In transit, Received, Approved / Rejected, Refunded). | One source of truth for all teams; replaces the spreadsheet | M | P3, W2 | OBJ-04 |
| BR-06 | Customers need to see the status of each return and refund online. | Removes the main reason customers call | M | P2, W1 | OBJ-02 |
| BR-07 | Customers need to be told by email when a return's status changes, and by text message if they have opted in. | Customers don't have to check or chase | S | P2, W1 | OBJ-02 |

### 6.3 Store returns

| ID | Requirement | Rationale | Priority | Source | Objective |
|---|---|---|---|---|---|
| BR-08 | Store colleagues need to look up an online order at the till, accept a return for eligible items and issue the refund there, once they have checked the item's condition. | Lets customers return in store and get money back straight away | M | P8, W4 | OBJ-03, OBJ-01 |

### 6.4 Warehouse

| ID | Requirement | Rationale | Priority | Source | Objective |
|---|---|---|---|---|---|
| BR-09 | Warehouse staff need to scan a return's QR label on arrival, which updates the return to Received. | Removes manual matching and the daily spreadsheet update | M | P5, P6, W3 | OBJ-01, OBJ-04 |
| BR-10 | Warehouse staff need to record the inspection result (Approved / Rejected) and the grade (A: resell, B: outlet, C: write off) against the return. | Triggers the refund and the restock decision | M | W3 | OBJ-01, OBJ-04 |

### 6.5 Refunds

| ID | Requirement | Rationale | Priority | Source | Objective |
|---|---|---|---|---|---|
| BR-11 | The business needs refunds issued automatically to the original payment method when a return is approved, unless BR-12 applies. | Removes manual keying and the email to finance | M | P4, P7, W4 | OBJ-01 |
| BR-12 | Finance needs to approve refunds over £250, or for customers flagged for unusual return patterns, before they are issued. | Controls refund fraud and errors | M | W4 | OBJ-01 |

### 6.6 Customer services and reporting

| ID | Requirement | Rationale | Priority | Source | Objective |
|---|---|---|---|---|---|
| BR-13 | Customer services need to see a return's full history and handle exceptions (eligibility reviews, lost parcels, disputes) in the OMS. | Advisers can answer any query from one screen | M | P2, W2 | OBJ-02 |
| BR-14 | Operations managers need a returns report showing volumes, reasons, cycle time by stage and the backlog awaiting inspection. | Lets the business see and manage the process | S | W3 | OBJ-04 |
| BR-15 | Customers could start an exchange for a different size or colour instead of a refund. | Keeps revenue | W (phase 2) | W1 | – |

## 7. Non-functional requirements

| ID | Category | Requirement | Priority |
|---|---|---|---|
| NFR-01 | Availability | The online returns journey is available 99.5% of the time, measured monthly, excluding planned maintenance overnight | M |
| NFR-02 | Performance | Order look-up at the till returns a result within 3 seconds | M |
| NFR-03 | Data protection | Store colleagues see only the data needed to process the return (order number, items, delivery date, payment method type), not the customer's full address or card details | M |
| NFR-04 | Accessibility | Customer-facing pages meet WCAG 2.2 AA | M |
| NFR-05 | Audit | Every status change and refund is logged with user, date and time, and kept for 7 years | M |
| NFR-06 | Legal | Refunds are issued within 14 days of receiving the goods back, in line with the Consumer Contracts Regulations 2013 | M |

## 8. Data requirements

| Data item | Source | Owner | Personal data? | Retention |
|---|---|---|---|---|
| Return record (items, reason, status history) | OMS | Head of Ecommerce | Yes (linked to customer) | 7 years (finance audit) |
| Return label / tracking number | Carrier API | Logistics manager | No | 2 years |
| Inspection result and grade | OMS (warehouse) | Warehouse manager | No | 7 years |
| Refund transaction | Payment provider | Finance systems lead | Yes | 7 years |
| Customer contact preferences (email / text) | Customer account | Head of Ecommerce | Yes | While account active |

## 9. Assumptions, constraints and dependencies

See the [project brief](01-project-brief.md#6-assumptions). One assumption was added during the workshops:

| ID | Assumption |
|---|---|
| A-05 | Stores have space to hold returned online items until the weekly collection to the warehouse |

## 10. Risks

| ID | Risk | Likelihood | Impact | Mitigation | Owner |
|---|---|---|---|---|---|
| R-01 | Store colleagues not trained before the January peak | M | H | Two-store pilot in November; store champions; one-page till guide | Store ops (S07) |
| R-02 | Refunds issued for items that don't arrive or are wrong | M | M | Posted returns are refunded only after the warehouse scans and inspects them; finance approval over £250 | Finance (S06) |
| R-03 | OMS configuration takes longer than planned | M | H | Technical spike in sprint 1; agreed fallback scope (BR-03, BR-07 and BR-14 can move to a later release) | Retail IT (S09) |
| R-04 | Customers abuse free returns | L | M | Track return rate per customer; flag unusual patterns under BR-12 | Finance (S06) |

## 11. Open questions

| # | Question | Owner | Due |
|---|---|---|---|
| Q1 | Should low-value posted returns (e.g. under £20) be refunded at drop-off, before inspection? | Finance (S06) | Before sprint 3 |
| Q2 | Can stores refund to the original card if the customer doesn't have it with them? | Finance (S06) / Retail IT (S09) | Before store pilot |
| Q3 | Who pays for the prepaid label: always free, or deducted from the refund for "changed my mind" returns? | Sponsor (S01) | Before go-live |

## 12. Glossary

| Term | Meaning |
|---|---|
| OMS | Order management system: holds orders and, after this change, returns |
| QR label | Prepaid return label with a QR code that the carrier and warehouse scan |
| Grade A / B / C | Inspection result: resell as new / sell through outlet / write off |
| DPIA | Data protection impact assessment |

## 13. Sign-off

| Role | Decision |
|---|---|
| Sponsor (S01) | Approved |
| Product owner (S02) | Approved |
| Finance (S06) | Approved with Q1–Q2 to be resolved before sprint 3 |
| Data Protection Officer (S10) | Approved subject to DPIA screening of NFR-03 |
