# Online Returns: Requirements Pack

> **Practice case study.** Fernbridge Home is a fictional retailer and all figures are illustrative. This repo shows how I would approach a requirements piece of this kind. It is not based on client work.

A requirements pack for moving a UK homeware retailer's returns process from email and phone to a self-service online journey. It follows the documents in my [BA toolkit](https://github.com/Vinayak-Koranga-Analyst/ba-toolkit), from stakeholder analysis through to UAT.

**Case study on my website:** a shorter write-up of this project is at [vinayakkoranga.com](https://vinayakkoranga.com/case-studies/online-returns-requirements/).

## The business problem

Fernbridge Home sells furniture and homeware through 40 stores and its website. Customers who want to return an online order must email or phone customer services. Returns are tracked in a shared spreadsheet, warehouse and finance teams pass updates by email, and refunds are issued by hand.

As a result:

- refunds take an average of **12 days** from the customer asking to the money arriving
- around **1 in 3 calls** to customer services are customers chasing a return or refund
- stores can't accept returns of online orders, so customers are sent away
- nobody can say how many returned items are sitting in the warehouse waiting to be checked

## What's in the pack

| # | Document | Status |
|---|---|---|
| 01 | [Project brief](01-project-brief.md): problem, objectives, scope, assumptions | Done |
| 02 | [Stakeholder register, power/interest map and RACI](02-stakeholders.md) | Done |
| 03 | [As-is process map and pain-point log](03-as-is-process.md) | Done |
| 04 | [To-be process map and change summary](04-to-be-process.md) | Done |
| 05 | [Business Requirements Document (BRD)](05-brd.md) | Done |
| 06 | [User stories with acceptance criteria](06-user-stories.md) | Done |
| 07 | [Requirements traceability matrix](07-rtm.md) ([CSV](07-rtm.csv)) | Done |
| 08 | [UAT plan and test scripts](08-uat-plan.md) | Done |

## Key outcomes of the analysis

- **8 pain points** traced to 3 root causes: no single record of a return, hand-offs by email, and a process built around posting.
- **15 business requirements**, each traced to its source (pain point or workshop), plus 6 non-functional requirements.
- **15 user stories** across 6 epics, with 45 acceptance criteria.
- **18 UAT test cases**, with full scripts for the 6 highest-risk ones.
- Estimated refund time falls from **12 days to about 5**, because most of the current delay is waiting between teams, not the parcel in transit.

## Approach

1. Frame the problem and agree scope with the sponsor.
2. Identify stakeholders and agree decision rights (RACI).
3. Map the current process with the people who run it and log pain points.
4. Design the future process and write business requirements against each pain point.
5. Break requirements into user stories with testable acceptance criteria.
6. Trace everything in an RTM and plan UAT from the acceptance criteria.

## Tools

Markdown and Mermaid (process maps render directly on GitHub), CSV for the RTM. The same content can be converted to Word with Pandoc or redrawn in Visio/Lucidchart for formal BPMN sign-off.
