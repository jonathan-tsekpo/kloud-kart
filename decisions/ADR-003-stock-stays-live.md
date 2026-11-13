# ADR-003: Keep stock checks on the live database, never on a copy

- **Status:** Accepted
- **Date:** 2026-11-13
- **Decision owner:** Kloud Kart engagement

## Context

The brief says stock counts cannot go stale, because that is how Kloud Kart oversells. Today stock counts are kept up to date through occasional manual checks, so the number a customer sees can fall behind the shelf, and the shop oversells (an estimated 40 orders a month). ADR-001 moves reporting to a reporting copy, which creates a temptation to point everything there, including stock.

## Decision

The existing developer changes the website so that each item is taken off the stock count in the live database the moment it is ordered, and the count is checked before a sale is accepted. The website’s stock check, and any stock screen used to sell or reorder, read from the live database only, never from the reporting copy or the warehouse. This rule is written into the developer’s handbook.

## Alternatives considered

### Alternative A: Read stock from the reporting copy

- **How it would work:** The website and stock screens read stock counts from the reporting copy, like every other report.
- **Why it is attractive:** One simple rule (“all reading happens on the reporting copy”), and it takes even the small stock reads off the shop’s machine.
- **Why rejected:** A reporting copy is usually a few seconds behind and can fall minutes behind when busy, which is exactly when stock moves fastest. A stale count is how overselling happens. Stock checks are tiny, quick lookups, so moving them saves almost nothing.

### Alternative B: A streaming service that feeds a live stock board

- **How it would work:** Every stock change is sent to a streaming service run by an outside vendor, and a live stock board and the website read from it.
- **Why it is attractive:** It answers the board’s wish for a live dashboard, and it could serve future channels such as a marketplace or a Nigeria warehouse.
- **Why rejected:** At about three orders a minute, updating the count in the live database at the moment of each sale gives the same result. A streaming service would add an always-on system and someone to look after it, just to produce a number the live database can already give.

## Consequences

- **What this buys:** Stock is correct at the moment each customer buys, with no new systems. Oversold orders should fall from about 40 a month to almost none.
- **What this costs:** A few weeks of the developer’s time, and the shop’s machine keeps doing the stock checks, which is a small amount of work. The rule depends on people following it, so it must be written down.
- **What it costs the client if I am wrong:** If a stock screen is ever pointed at a copy, or the shelf and the system drift apart because stock-taking slips, Kloud Kart keeps overselling. Each oversold order costs a refund, a payment reversal fee, an apology call and often the customer.
- **What would make me revisit this:** Two sales channels or countries selling from the same stock at the same time, because they would need to stay in step live. Or stock checks becoming a noticeable share of the live database’s load.

## What this survives

It survives orders doubling, because stock lookups stay small. It survives pressure to move everything away from the live database: protecting the website does not mean moving the one live decision onto a delayed copy. It does not survive a shared stock pool across countries or channels; that would need a new record.
