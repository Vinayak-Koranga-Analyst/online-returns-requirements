# 01. Project Brief: Online Returns

> **Practice case study.** Fernbridge Home is fictional and all figures are illustrative.

**Version:** 1.0 | **Author:** Business Analyst | **Sponsor:** Director of Customer Operations

## 1. Background

Fernbridge Home is a UK homeware and furniture retailer with 40 stores and a website. Online sales have grown to around 35% of revenue, and online returns have grown with them, to around 1,800 returns a month.

The returns process was designed when online sales were small. It relies on email, phone calls and a shared spreadsheet, and has not kept up with volume.

## 2. Problem statement

> *The problem of* a manual, email-based returns process *affects* online customers, customer services, the returns warehouse and finance, *and results in* slow refunds, high call volumes and poor visibility of returned stock. *A good solution would* let customers start and track a return themselves, and pass each return between teams automatically.

## 3. Evidence

| Measure | Current value | Source |
|---|---|---|
| Online returns per month | ~1,800 | Returns spreadsheet, last 6 months |
| Average time from return request to refund | 12 days | Sample of 200 returns |
| Share of customer services calls about returns / refunds | ~33% | Call reason codes, last quarter |
| Returns needing at least one customer chase | ~40% | Sample of 200 returns |
| Online orders customers tried to return in store and were turned away | Not recorded | Store manager feedback |

## 4. Objectives

| ID | Objective | Measure | Baseline | Target (6 months after go-live) |
|---|---|---|---|---|
| OBJ-01 | Refund customers faster | Average days from request to refund | 12 | 5 or fewer |
| OBJ-02 | Reduce avoidable contact | Share of calls about returns / refunds | 33% | 15% or less |
| OBJ-03 | Let customers return online orders in store | Stores able to accept online returns | 0 of 40 | 40 of 40 |
| OBJ-04 | Know where every returned item is | Returns with a tracked status | Spreadsheet only | 100% in the order management system |

## 5. Scope

| In scope | Out of scope |
|---|---|
| Online orders delivered by parcel carrier | Large furniture collected by two-person crews (separate project) |
| Self-service return request on website and app | Exchanges (phase 2) |
| Prepaid return label and drop-off options | Changes to the returns policy itself (30 days) |
| In-store returns of online orders | Marketplace / third-party seller orders |
| Return status tracking for customers and staff | Replacing the payment provider |
| Automatic refund once warehouse approves | Faulty-goods claims needing engineer inspection |
| Returns reporting for operations | |

## 6. Assumptions

| ID | Assumption |
|---|---|
| A-01 | The current order management system (OMS) can hold return status, with configuration rather than a rebuild |
| A-02 | The payment provider supports refunds triggered through its API |
| A-03 | The carrier can generate prepaid return labels and QR codes |
| A-04 | Store tills can look up online orders by order number |

## 7. Constraints

| ID | Constraint |
|---|---|
| C-01 | Must go live before the January sales peak |
| C-02 | Must meet UK GDPR for any customer data shown in store |
| C-03 | Customer-facing pages must meet WCAG 2.2 AA |
| C-04 | Refunds must stay within the 14-day limit in the Consumer Contracts Regulations |

## 8. Dependencies

| ID | Dependency | Owner |
|---|---|---|
| D-01 | Carrier API access for return labels | Logistics manager |
| D-02 | Payment provider refund API enabled | Finance systems lead |
| D-03 | Till software update for order look-up | Retail IT |

## 9. Initial risks

| ID | Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|---|
| R-01 | Store colleagues not trained in time for peak | M | H | Train store champions first; short guide at the till |
| R-02 | Automatic refunds issued for items that don't arrive | M | M | Refund only after warehouse scan, or at drop-off for low-value items (to be agreed) |
| R-03 | OMS configuration takes longer than expected | M | H | Early technical spike; agree a fallback scope |
