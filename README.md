# NadiPath: Smart River-Port Logistics Network

A Complex Engineering Project in Software Engineering and Information System Design, designed and authored by Md. Abdullah Al Afif.

Academic coursework project, CSE 345: Information System Design & Software Engineering, Summer 2026.

---

## About This Repository

This repository showcases my work on a Complex Engineering Project (CEP), which I completed as coursework for CSE 345. It is an academic project, and I am its sole author. The requirements analysis, stakeholder analysis, prioritisation framework, UML designs, technology choices, methodology and project timeline are all my own work.

The aim is to document how I approached a deliberately open-ended problem: not just what I designed, but why, with every decision traced back to a specific detail of the scenario.

## The Problem

Bangladesh's inland waterway freight network serves over 700 rivers and connects 11 major river-port terminals across 7 districts. It has long depended on manual, paper-based processes for vessel scheduling, cargo documentation, regulatory clearance and workforce coordination. After Cyclone Mahaan in October 2025 made 38 road bridges unsafe for heavy cargo, the inland network became the main logistics corridor for about 60 percent of inter-district freight, exposing these failures.

NadiPath Multimodal Logistics Ltd. is a public-private consortium (BIWTA, three private shipping conglomerates, the Department of Disaster Management and a sovereign investment fund), co-financed by the World Bank with USD 120 million conditional on an ISO-auditable digital platform. The problem spans engineering, economics, law, human behaviour and public administration.

The hard constraints in the scenario:

- Four terminals have intermittent network connectivity.
- A 2009-era vessel registration system cannot be replaced within the timeline.
- NBR, BIWTA and BSTI run disconnected legacy platforms.
- Private operators resist sharing data with competitors, small informal traders fear regulatory exposure, and dock workers derailed two earlier BIWTA digitisation attempts.
- Phase 1 must be delivered within 14 months on a budget of USD 8.5 million.

## What I Did

**Task 1: Requirements engineering and stakeholder analysis.** I structured the scenario into 10 functional, 7 non-functional and 4 organisational/regulatory requirements, and analysed eight stakeholder groups by interest, influence and main conflict. I prioritised using a combined MoSCoW and Criticality–Feasibility method, and worked through five trade-offs where stakeholder needs cannot all be met.

**Task 2: Structured software design using UML.** I produced use case, class, sequence and activity diagrams, each with written commentary on the decisions made, the alternatives rejected and the scenario details behind them. The design is an offline-first, adapter-based architecture.

**Task 3: Tools, platforms, technologies and methodology.** I recommended a hybrid Agile methodology and a full technology stack, and mapped each choice to the scenario constraint it answers, including the risk it introduces or mitigates. I also stated the uncertainties and trade-offs openly.

**Project timeline.** I produced a 14-month Phase 1 Gantt chart showing how the trade-offs translate into sequencing.

## Highlights

**Prioritisation.** MoSCoW alone cannot show why one Must should be built before another, so every Must requirement was also scored for Criticality and Feasibility from 1 to 5. High-criticality, high-feasibility items (for example vessel registration, digital manifests, clearance routing, offline operation and legacy integration) went into Phase 1, while items such as full dock workforce automation were scheduled later.

**Trade-offs analysed.**
- Transparency versus privacy: regulators see compliance-relevant fields only, not full commercial data.
- Formal compliance versus informal trader participation: a simplified, lower-friction registration tier in Phase 1.
- Speed versus worker trust: part of the schedule is spent on visible worker benefits.
- Central control versus terminal autonomy: an offline-first design with local autonomy during outages.
- Audit completeness versus legacy constraints: an adapter-based integration layer that keeps legacy systems running while producing a unified audit trail.

**Design decisions.**
- Actors are split by real conflict of interest, so small informal traders are kept separate from vessel operators.
- Offline queueing and legacy adapters are part of the core domain model, because they solve two of the scenario's hardest constraints.
- Centralising translation in one Legacy Adapter service means only one component changes if a regulator updates its system.

**Methodology.** Short two-to-three-week Scrum sprints combined with fixed regulatory and stakeholder review gates, since sign-off from NBR, BIWTA and BSTI and World Bank audit checkpoints cannot be treated as flexible backlog items. Pure Scrum and pure Waterfall were both considered and rejected.

**Timeline.** Trust-building with dock workers and traders runs from month 1, a 2-terminal pilot comes before the rollout to the remaining 9 terminals, and the World Bank compliance audit sits at month 14 after an ISO-audit readiness review.

## How Constraints Shaped the Design

| Scenario constraint | Design response |
|---|---|
| Budget of USD 8.5M and 14 months | Open-source backend, database and messaging stack; phased rollout instead of all 11 terminals at once |
| Intermittent connectivity at 4 terminals | Offline-first edge nodes with local storage and queued sync |
| 2009 legacy registry | Read-only API wrapper instead of replacement |
| Disconnected NBR, BIWTA and BSTI platforms | Dedicated legacy adapters per agency |
| Private operators resist data sharing | Role-based data segregation |
| Dock worker resistance | Phased rollout, visible workforce benefits first, training built into the schedule |
| Small trader fear of regulatory exposure | Simplified low-friction registration tier in Phase 1 |

## Technology Choices

| Layer | Choice |
|---|---|
| Edge / terminal client | Progressive Web App and lightweight Android app with local SQLite storage |
| Low-literacy access | SMS / USSD gateway |
| Core backend | Java (Spring Boot) or Node.js microservices |
| Central database | PostgreSQL |
| Offline sync | Queue-based sync with conflict-resolution rules |
| Integration layer | Adapter microservices with a message queue (for example RabbitMQ) |
| Hosting | Government-approved local data center with cloud burst capability |
| Security and audit | Role-based access control, encryption in transit and at rest, immutable audit logging |

## Using This Work

I am happy for this repository to help others learn.

- Read it, learn from the reasoning, and use it as a reference for how to justify decisions against a scenario.
- Credit the author if you cite, quote or build on it: Md. Abdullah Al Afif, "NadiPath: Smart River-Port Logistics Network", academic CEP, 2026.
- Do not submit this work, or a lightly edited version, as your own academic assignment.

You may share and adapt the report text and diagrams as long as you give appropriate credit to the author.

## Author

Md. Abdullah Al Afif, Dhaka, Bangladesh
