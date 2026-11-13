# ADR-002: Refresh all reporting once a day; no streaming system

- **Status:** Accepted
- **Date:** 2026-11-13
- **Decision owner:** Kloud Kart engagement

## Context

The board asked forreal-time dashboards, after seeing one at another company. The brief says stock counts cannot go stale but everything else can refresh daily.

Kloud Kart takes about 4,000 orders a day, roughly three a minute. The team will be two data hires. The test used: what decision changes if this number is ten seconds old instead of a day old? For revenue, marketing and finance, the answer is none.

## Decision

All reports refresh once a night automatically and show when they were last updated. We will not build a streaming system. Stock is handled separately, live on the shop’s database (ADR-003).

## Alternatives considered

### Alternative A: Stream all business data in real time

- **How it would work:** Every order, payment and customer action is sent as it happens to a streaming service, which keeps dashboards updated within seconds.
- **Why it is attractive:** It gives the board exactly what it asked for. Numbers are always fresh, and it would support quick decisions if Kloud Kart ever needed them.
- **Why rejected:** No revenue, marketing or finance decision at Kloud Kart changes within seconds. A streaming system runs all day and night, needs someone to notice when it stops, and is harder to fix because you cannot simply rerun yesterday. That would take a large share of one hire’s year for no change in any decision.

### Alternative B: Refresh every 15–30 minutes

- **How it would work:** The automatic job runs many times a day instead of once.
- **Why it is attractive:** Fresher numbers without a streaming system, using the same tools.
- **Why rejected:** Nobody has named a decision that needs numbers fresher than this morning. Running the refresh all day adds strain on the reporting copy and more failures to watch. It is easy to switch on later if a real need appears.

## Consequences

- **What this buys:** A simple job with a clear start and end. It is easy to rerun before Nana opens the report, and nobody needs to be on call.
- **What this costs:** Revenue and marketing reports are up to a day old, and some board members will not like that.
- **What it costs the client if I am wrong:** If Marketing starts running flash sales where spending changes within the hour, day-old numbers could waste a day’s advertising budget.
- **What would make me revisit this:** A named decision that changes within the day, such as flash sales or hourly price changes. Or the nightly refresh taking more than two hours.

## What this survives

It survives harder board pressure for “real-time”, because the one number that needs to be live, stock, is read live at the moment of each sale (ADR-003). Any other request must name the decision that changes within seconds. It survives orders doubling, because a nightly job simply takes a little longer. If a genuine time-sensitive need appears, only that one flow gets a faster refresh; the rest stay daily.
