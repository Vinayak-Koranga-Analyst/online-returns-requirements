# 06. User Stories: Online Returns

> **Practice case study.** Fernbridge Home is fictional.

Built from the [user story template](https://github.com/Vinayak-Koranga-Analyst/ba-toolkit/blob/main/templates/05-user-story.md). Each story links to a business requirement in the [BRD](05-brd.md). Estimates are left for the delivery team to set.

## Epics

| Epic | Name | Requirements | Stories |
|---|---|---|---|
| EP-01 | Start a return | BR-01 – BR-04 | US-01 – US-04 |
| EP-02 | Track a return | BR-05 – BR-07 | US-05 – US-07 |
| EP-03 | Return in store | BR-08 | US-08 – US-09 |
| EP-04 | Receive and inspect | BR-09 – BR-10 | US-10 – US-11 |
| EP-05 | Refund | BR-11 – BR-12 | US-12 – US-13 |
| EP-06 | Support and reporting | BR-13 – BR-14 | US-14 – US-15 |

---

## EP-01 Start a return

### US-01 Start a return online
**Requirement:** BR-01 | **Priority:** Must

**As a** customer with a delivered online order
**I want** to start a return from my account or with my order number and email address
**So that** I don't have to call or email customer services

- **AC1** Given I am signed in and have an order delivered in the last 30 days, when I open the order, then I see a "Return items" button.
- **AC2** Given I am not signed in, when I enter a valid order number and the email address on the order, then I can start a return for that order.
- **AC3** Given I enter an order number and email that don't match, when I submit, then I see "We can't find that order" and no order details are shown.
- **AC4** Given I select one or more items and confirm, when the return is created, then I see a return number and the return is saved with status Requested.

### US-02 Check eligibility automatically
**Requirement:** BR-02 | **Priority:** Must

**As a** customer
**I want** to know straight away whether an item can be returned
**So that** I don't send back something that will be refused

- **AC1** Given an item was delivered more than 30 days ago, when I view my order, then the item can't be selected and shows "Return window closed on [date]".
- **AC2** Given an item is on the excluded list, when I view my order, then it can't be selected and shows the reason.
- **AC3** Given I think an item has been wrongly refused, when I select "Ask for a review", then a case is created for customer services (see US-14).

### US-03 Give a return reason
**Requirement:** BR-03 | **Priority:** Should

**As a** product manager
**I want** customers to give a reason for every returned item
**So that** I can spot quality and description problems

- **AC1** Given I'm returning an item, when I try to continue without a reason, then I'm asked to choose one.
- **AC2** Given the reason list, then it contains: Too big, Too small, Not as described, Damaged or faulty, Arrived late, Changed my mind, Other (with a free-text box of up to 250 characters).

### US-04 Choose how to send it back
**Requirement:** BR-04 | **Priority:** Must

**As a** customer
**I want** to choose between dropping off a parcel and taking the item to a store
**So that** I can pick whichever suits me

- **AC1** Given I've selected items to return, when I reach the method step, then I can choose "Drop off at a parcel point" or "Return to a store".
- **AC2** Given I choose a parcel point, when I confirm, then I get a QR code by email and on screen, plus a printable label, and the nearest drop-off points are shown.
- **AC3** Given I choose a store, when I confirm, then I see a list of stores and a QR code to show at the till.

---

## EP-02 Track a return

### US-05 Keep one record of each return
**Requirement:** BR-05 | **Priority:** Must

**As an** operations user
**I want** each return held in the OMS with its full status history
**So that** every team sees the same information

- **AC1** Given a return is created, then it has a unique return number linked to the original order.
- **AC2** Given a return's status changes, then the change is recorded with date, time and the user or system that made it.
- **AC3** Given a return, then its status is always one of: Requested, In transit, Received, Approved, Rejected, Refunded, Cancelled.

### US-06 See return status online
**Requirement:** BR-06 | **Priority:** Must

**As a** customer who has started a return
**I want** to see where my return and refund are
**So that** I don't need to call to find out

- **AC1** Given I have a return in progress, when I open "My returns", then I see each return with its current status and the date it changed.
- **AC2** Given my refund has been issued, then I see the amount, the payment method (e.g. "Visa ending 1234") and the date issued.
- **AC3** Given my return was rejected, then I see the reason and how to contact customer services.

### US-07 Get status updates
**Requirement:** BR-07 | **Priority:** Should

**As a** customer
**I want** to be told when my return moves forward
**So that** I don't have to keep checking

- **AC1** Given my return changes to In transit, Received, Approved, Rejected or Refunded, then I get an email within 15 minutes.
- **AC2** Given I've opted in to text messages, then I also get a text for Received and Refunded.
- **AC3** Given I haven't opted in to text messages, then no text is sent.

---

## EP-03 Return in store

### US-08 Find an online order at the till
**Requirement:** BR-08, NFR-02, NFR-03 | **Priority:** Must

**As a** store colleague
**I want** to find a customer's online order at the till
**So that** I can accept their return

- **AC1** Given the customer shows a return QR code, when I scan it, then the return and its items appear within 3 seconds.
- **AC2** Given the customer has no QR code, when I enter the order number and the customer's postcode, then the order appears.
- **AC3** Given an order is found, then I see the order number, items, delivery date and payment method type, but not the customer's full address or card number.

### US-09 Accept a return and refund in store
**Requirement:** BR-08 | **Priority:** Must

**As a** store colleague
**I want** to accept an eligible item and refund it at the till
**So that** the customer leaves with their refund confirmed

- **AC1** Given the item is eligible and in acceptable condition, when I confirm the return, then the refund goes to the original payment method and the return status changes to Refunded.
- **AC2** Given the item is not in acceptable condition, when I select "Can't accept", then I must choose a reason and the customer is given a printed note explaining the next steps.
- **AC3** Given I've accepted an item, then the till prints a returns slip to attach to it for the weekly warehouse collection.

---

## EP-04 Receive and inspect

### US-10 Scan returns on arrival
**Requirement:** BR-09 | **Priority:** Must

**As a** warehouse operative
**I want** to scan a return's label when it arrives
**So that** it's matched to the right order without looking it up by hand

- **AC1** Given a parcel with a return QR label, when I scan it, then the return opens and its status changes to Received.
- **AC2** Given a parcel with no label or an unreadable one, when I search by order number or customer name, then I can match it and mark it Received.
- **AC3** Given a parcel I can't match, when I log it as "Unidentified", then a case is created for customer services.

### US-11 Record the inspection result
**Requirement:** BR-10 | **Priority:** Must

**As a** warehouse operative
**I want** to record whether a returned item is approved and how it's graded
**So that** the refund and restocking happen without further hand-offs

- **AC1** Given a received return, when I record Approved and a grade (A, B or C), then the status changes to Approved and the stock record is updated.
- **AC2** Given a received return, when I record Rejected, then I must choose a reason and add a photo, and the status changes to Rejected.
- **AC3** Given a return with several items, then I can record a different result for each item.

---

## EP-05 Refund

### US-12 Refund approved returns automatically
**Requirement:** BR-11, NFR-06 | **Priority:** Must

**As a** customer
**I want** my refund issued as soon as my return is approved
**So that** I get my money back quickly

- **AC1** Given a return is Approved and the refund is £250 or less, and the customer isn't flagged, then the refund is sent to the original payment method within 1 hour and the status changes to Refunded.
- **AC2** Given the payment provider rejects the refund, then the return is flagged for finance and the customer isn't told it's refunded.
- **AC3** Given an approved return hasn't been refunded within 10 days of receipt, then finance is alerted (so the 14-day legal limit isn't missed).

### US-13 Approve high-value or flagged refunds
**Requirement:** BR-12 | **Priority:** Must

**As a** finance refunds analyst
**I want** to review refunds over £250 or for flagged customers before they are issued
**So that** we control fraud and errors

- **AC1** Given an approved return over £250, or from a flagged customer, then it appears in my "Refunds to approve" queue instead of being refunded automatically.
- **AC2** Given I approve it, then the refund is sent and the status changes to Refunded.
- **AC3** Given I hold it, then I must enter a reason, and customer services can see that reason.

---

## EP-06 Support and reporting

### US-14 Handle exceptions in one place
**Requirement:** BR-13 | **Priority:** Must

**As a** customer services adviser
**I want** to see a return's full history and any open cases on one screen
**So that** I can answer the customer without asking other teams

- **AC1** Given I search by order number, return number or customer email, then I see all returns for that customer with status history.
- **AC2** Given an eligibility review, an unidentified parcel or a held refund, then it appears in my exceptions queue with its age.
- **AC3** Given I resolve an eligibility review as accepted, then the customer can continue their return and is emailed a link.

### US-15 Returns report
**Requirement:** BR-14 | **Priority:** Should

**As an** operations manager
**I want** a daily returns report
**So that** I can see volumes, delays and backlog

- **AC1** Given the report, then it shows returns by status, reason, method (post / store) and week.
- **AC2** Given the report, then it shows average days for each stage (request → received → approved → refunded).
- **AC3** Given the report, then it lists returns waiting for inspection for more than 1 working day.
