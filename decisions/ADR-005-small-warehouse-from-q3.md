# ADR-005: Add a small warehouse in month 7; no lake or lakehouse

- **Status:** Accepted
- **Date:** 2026-11-13
- **Decision owner:** Kloud Kart engagement

## Context

By month 7, the reporting copy will not be enough for three things. It cannot keep history the live database overwrites, such as last week’s stock levels or an order’s status changes. It cannot combine Ghana and Nigeria if their data differs. And it cannot give a copy without customer contact details.

The data is 40 GB of tidy records (orders, stock and customers), growing 15–20% a year. The questions are known: revenue, stock and repeat customers. The team is two people. Finance flinched at cloud bills, investors asked about a lakehouse, and the developer wants Snowflake or BigQuery. This choice is the hardest to reverse, so it is made in Q3, once Nigeria’s needs and the revenue definition are known.

## Decision

In month 7, the data engineer sets up an ordinary database run by the hosting company (about 100 GB, fixed monthly price) as a small warehouse. It is filled every night from the reporting copy, with contact details removed (ADR-004). The analytics engineer builds the reports on it using standard database tools.

## Alternatives considered

### Alternative A: A pay-as-you-go cloud warehouse (the developer’s choice)

- **How it would work:** A cloud warehouse such as Snowflake or BigQuery, billed by how much it is used, filled nightly, with the same reports.
- **Why it is attractive:** At 40 GB the bill could be small, there is almost nothing to manage, and it scales far beyond Kloud Kart’s needs. This is the closest call in the plan.
- **Why rejected:** The bill moves with usage, and a new team has not yet learned to control it; a dashboard refreshing every hour that nobody reads is a common first-year surprise. Finance has already flinched. Because the reports use standard database language, moving later takes weeks, not a rebuild.

### Alternative B: A lakehouse

- **How it would work:** Raw files in cheap cloud storage, a table layer on top, and a separate engine to process them.
- **Why it is attractive:** One platform for reports and future machine learning, cheap storage, room for images and website logs, and a name investors recognise.
- **Why rejected:** It is built for very large or messy data and machine-learning teams. 40 GB of tidy records fits in an ordinary database, so the storage savings are tiny. It needs specialist skills neither hire will have, and it would take up one of them for most of a year.

## Consequences

- **What this buys:** History from month 7, Ghana and Nigeria side by side, a reporting copy without contact details, and a fixed bill of USD 60–150 a month that Finance can plan for.
- **What this costs:** One more system to look after, and it must be resized as data grows. It is not suited to images or logs.
- **What it costs the client if I am wrong:** If growth or Nigeria outgrows one database, Nana’s reports slow from seconds to minutes. Moving to a cloud warehouse would then take 4–6 weeks of the data engineer’s time, and new reports would pause for most of a quarter.
- **What would make me revisit this:** Data passing about 500 GB or the nightly copy taking over two hours. Finance accepting a capped pay-as-you-go bill. Year-two forecasting needing cloud tools. Or images and website logs needing analysis.

## What this survives

It survives orders doubling (about 80 GB is still comfortable) and Nigeria becoming a full market, which is what it is for. It survives investor pressure for a lakehouse, because the reasoning and the trigger for changing are written down. If the budget falls to one hire, the warehouse slips a quarter and the reporting copy carries reporting meanwhile. It does not survive data growing tenfold in a year.
