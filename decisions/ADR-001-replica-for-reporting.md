# ADR-001: Move all reporting to a reporting copy on the pre-approved second server

- **Status:** Accepted
- **Date:** 2026-11-13
- **Decision owner:**Kloud Kart engagement

## Context

Orders, stock and customer accounts live in one database on the same machine as the website. Monday exports of a few hundred thousand rows run against it, and twice last month one slowed the website to a crawl. That is an estimated GHS 45,000 of orders at risk each time.

A second server is already pre-approved. Neither data hire will start for six to eight weeks, so the first fix has to be something the existing website developer can do.

## Decision

In the first four weeks, the existing developer sets up the second server as a reporting copy of the live database. Every report, export and Finance request moves to the reporting copy. The live database serves only the website and the stock check.

## Alternatives considered

### Alternative A: Buy a cloud warehouse now

- **How it would work:** Data is copied from the live database into a cloud warehouse every night, and all reports run there.
- **Why it is attractive:** It takes reporting off the shop just as well as a reporting copy. There is no server to manage, it scales easily, and the developer has already asked for it.
- **Why rejected:** It is a good second step, not a first one. Until a reporting copy exists, the nightly copy would itself run against the live database. Someone has to model the data before Nana can use it, and that person does not start until month 3. It also puts customer data in a new place while a data-protection complaint is open, on a pay-as-you-go bill Finance has already flinched at. The reporting copy protects the shop in days; this takes a quarter.

### Alternative B: Keep one machine and run exports at 02:00

- **How it would work:** Exports are scheduled for the quietest hour and slowed down so they cannot overload the machine.
- **Why it is attractive:** No new server and nothing new to learn. It could start this week.
- **Why rejected:** 02:00 is the only quiet hour, and the Nigeria pilot will shrink it. Marketing’s ad-hoc exports cannot be scheduled. Reporting stays one heavy report away from slowing the shop, and the second server is already approved, so the saving is close to nothing.

## Consequences

- **What this buys:** Reporting can no longer slow the website. Nana and Finance read the same data from the same place. There is one place to give and remove reporting access.
- **What this costs:** About USD 80–150 a month, one more server to look after, and delay to watch. It is also one more copy of customer data, although deletions reach it automatically because it mirrors the live database.
- **What it costs the client if I am wrong:** The main risk is delay. If anyone points the website’s stock check at the reporting copy, a few seconds’ delay becomes oversold orders: refunds, apologies and lost customers, which cost far more than the server. That is why stock stays on the live database (ADR-003). If the reporting copy just runs slightly behind, reports are a few minutes old, which is annoying but harmless.
- **What would make me revisit this:** Delay above 30 seconds at Monday peak on more than two Mondays. The need, expected in Q3, for history the live database does not keep (ADR-005). Or Nigeria running its own database.

## What this survives

It survives orders doubling and Nigeria joining the same database, because the website’s path is unchanged and reporting grows on its own machine. It survives the budget falling to one hire, because it is done before either hire arrives. It does not survive Nigeria running a separate database: combining two databases needs the warehouse sooner, and a new record would replace this one.
