# 07. Requirements Traceability Matrix: Online Returns

> **Practice case study.** Fernbridge Home is fictional.

Built from the [RTM template](https://github.com/Vinayak-Koranga-Analyst/ba-toolkit/blob/main/templates/06-rtm.md). The same matrix is in [`07-rtm.csv`](07-rtm.csv) for Excel or Jira import.

Traces each requirement from its source (pain point P1–P8 or workshop W1–W4) to the objective it supports, the user stories that deliver it and the UAT test cases that prove it. Test status is "Not run" because this is the version baselined before UAT.

## Matrix

| Req ID | Requirement | Priority | Objective | Source | User stories | Test cases | Status |
|---|---|---|---|---|---|---|---|
| BR-01 | Start a return online | M | OBJ-01; OBJ-02 | P1; W1 | US-01 | TC-01; TC-02 | Agreed |
| BR-02 | Automatic eligibility check | M | OBJ-01 | W1 | US-02 | TC-03 | Agreed |
| BR-03 | Capture return reason | S | OBJ-04 | W1; W3 | US-03 | TC-04 | Agreed |
| BR-04 | Choice of return method (QR label or store) | M | OBJ-01; OBJ-03 | P5; P8; W2 | US-04 | TC-05; TC-06 | Agreed |
| BR-05 | Single return record with status history | M | OBJ-04 | P3; W2 | US-05 | TC-07; TC-18 | Agreed |
| BR-06 | Customer sees status online | M | OBJ-02 | P2; W1 | US-06 | TC-07 | Agreed |
| BR-07 | Status notifications by email / text | S | OBJ-02 | P2; W1 | US-07 | TC-08 | Agreed |
| BR-08 | Store look-up, accept and refund | M | OBJ-03; OBJ-01 | P8; W4 | US-08; US-09 | TC-09; TC-10 | Agreed |
| BR-09 | Scan label on arrival | M | OBJ-01; OBJ-04 | P5; P6; W3 | US-10 | TC-11 | Agreed |
| BR-10 | Record inspection result and grade | M | OBJ-01; OBJ-04 | W3 | US-11 | TC-12 | Agreed |
| BR-11 | Automatic refund on approval | M | OBJ-01 | P4; P7; W4 | US-12 | TC-13 | Agreed |
| BR-12 | Finance approval over £250 or flagged | M | OBJ-01 | W4 | US-13 | TC-14 | Agreed |
| BR-13 | CS full history and exceptions queue | M | OBJ-02 | P2; W2 | US-14 | TC-15 | Agreed |
| BR-14 | Returns report | S | OBJ-04 | W3 | US-15 | TC-16 | Agreed |
| BR-15 | Exchanges | W | – | W1 | – | – | Deferred (phase 2) |
| NFR-01 | 99.5% availability | M | – | W2 | – | PT-01 (performance test, not UAT) | Agreed |
| NFR-02 | Till look-up within 3 seconds | M | OBJ-03 | W4 | US-08 | TC-09 | Agreed |
| NFR-03 | Minimal customer data at till | M | – | DPO review | US-08 | TC-09 | Agreed |
| NFR-04 | WCAG 2.2 AA | M | – | Policy | US-01 – US-07 | TC-17 | Agreed |
| NFR-05 | Audit log of status changes and refunds | M | – | Finance | US-05; US-12 | TC-18 | Agreed |
| NFR-06 | Refund within 14 days of receipt | M | OBJ-01 | Legal | US-12 | TC-13 | Agreed |

## Coverage checks (at baseline)

| Check | Result |
|---|---|
| Must / Should requirements with no linked story | None |
| Must / Should requirements with no linked test | None (NFR-01 is covered by performance testing, not UAT) |
| Stories with no linked requirement | None: US-01 to US-15 all trace to a BR |
| Pain points (P1–P8) not addressed by any requirement | None |
| Objectives with no linked requirement | None |
| Won't-have items | BR-15 (exchanges), deferred to phase 2 |

## Pain point → requirement view

| Pain point | Requirements |
|---|---|
| P1 No self-service | BR-01 |
| P2 Customers chase | BR-06, BR-07, BR-13 |
| P3 Spreadsheet tracking | BR-05 |
| P4 Email to finance | BR-11 |
| P5 Manual matching | BR-04, BR-09 |
| P6 Daily spreadsheet update | BR-09 |
| P7 Refunds keyed by hand | BR-11 |
| P8 Stores turn customers away | BR-04, BR-08 |

## Change log

| Version | Req ID | Change | Reason | Approved by |
|---|---|---|---|---|
| 0.2 | BR-08 | Added refund at the till for store returns | Workshop 4: customers expect the refund straight away in store | Product owner, Finance |
| 0.2 | BR-12 | Added £250 approval limit | Workshop 4: refund fraud control | Finance |
| 1.0 | BR-15 | Exchanges moved from Could to Won't (phase 2) | OMS capacity in this release | Product owner |
