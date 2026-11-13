# ADR-006: Hire a data engineer first and an analytics engineer second; no data scientist this year

- **Status:** Accepted
- **Date:** 2026-11-13
- **Decision owner:** Kloud Kart engagement

## Context

The board approved two data hires, not three. There is one website developer, and nobody has run a warehouse or written Python professionally. Investors mentioned machine learning for demand forecasting.

The first-quarter problems are engineering and access problems: the slow website, the complaint deadline and uncontrolled copies. The second-quarter problem, two revenue numbers, is a definition problem. Hiring takes six to eight weeks.

## Decision

Start recruiting a data engineer on day 1: someone who knows databases and servers, can automate routine jobs, and can take charge of access and security. Start recruiting an analytics engineer in month 2, to join around month 3: someone strong at building reports, with the patience to get Finance and Operations to sign one definition. No data scientist this year.

## Alternatives considered

### Alternative A: Hire the analytics engineer first

- **How it would work:** The analytics engineer arrives first to fix the revenue definition and the Monday report; the engineer follows.
- **Why it is attractive:** The revenue argument is Nana’s most visible pain, so this would be the quicker win with the board. The existing developer can set up the reporting copy anyway.
- **Why rejected:** Everything after the reporting copy is engineering work: backups, deleting customers from every copy, access control and scheduled refreshes. The complaint deadline falls in Q1. An analytics engineer hired first would spend months acting as a database administrator, and the definition work would slip anyway.

### Alternative B: A data engineer and a data scientist

- **How it would work:** The engineer builds the data flows; the scientist builds forecasting.
- **Why it is attractive:** It answers the investors’ machine-learning question directly.
- **Why rejected:** A forecast learns from history, and Kloud Kart’s history is disputed, so the forecast would inherit the argument. The scientist would spend most of the year doing an analytics engineer’s job, at a higher salary.

## Consequences

- **What this buys:** Clear owners. The data engineer is responsible for the website’s safety, access and data movement; the analytics engineer for what the numbers mean. Each problem is tackled in the order it hurts.
- **What this costs:** No machine learning this year. One engineer is a single point of failure, so these records and written procedures matter. The first “one number” win waits until month 5.
- **What it costs the client if I am wrong:** If the data engineer takes longer than eight weeks to find, the complaint work falls on the developer and Nana, which is why the deletion tracker is built for Nana to run alone. If the board reads “no data scientist” as being ignored, Nana faces a harder meeting; the dated month-12 decision is her answer.
- **What would make me revisit this:** No suitable engineer found within ten weeks (use a contractor for Q1), the board funding a third hire, or a year of agreed history existing.

## What this survives

It survives the budget falling to one hire: the data engineer alone still delivers Q1 and the daily report. It survives heavier investor pressure for machine learning, because there is a dated decision point. It survives orders doubling, because the architecture does not need more people.
