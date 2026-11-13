# Situation Diagnosis – Kloud Kart

**Prepared for:** Nana Adjei, Head of Operations\
**Date:** 13 November 2026

Kloud Kart does not have a technology problem. The website works and the database works. The problem is that one database is doing three jobs at once. It takes customer orders, it feeds the Monday reports that people rebuild by hand, and it is the source of the customer lists that Marketing hands around. Nothing separates these jobs, nobody has written down what the numbers mean, and nobody keeps track of where customer data goes.

Five root causes sit behind the symptoms described in the brief. I have ranked them by the risk each one poses to Nana's next board conversation, which is not always the same as the problem that costs the most money today.

## Findings, ranked by risk

### 1: Customer data is copied with no record of where it goes — Severity: Critical

Marketing and Nana can pull customer data straight out of the live database into files, and nothing records who pulled what, where it went or whether it was ever deleted. When a customer asks to be deleted, the request reaches the database but not the copies. The brief shows the result: Marketing exports a list of about 300,000 people with no record of how many copies exist, and Kloud Kart now has 90 days to answer a Data Protection Commission complaint about a deleted customer's data. Customer data currently sits in at least eight kinds of place: the live database, its backups, the Monday CSV exports, Nana’s and Finance’s spreadsheets, Marketing’s exported lists, the marketing tool, and email and shared drives. How many copies exist in total is unknown, and that is the finding.

The fines under Ghana’s Data Protection Act (Act 843) are modest. Ignoring an enforcement notice carries up to 150 penalty units, about GHS 1,800 (s.80), and the general penalty is up to 5,000 penalty units, about GHS 60,000 (s.95). The real costs are larger. The Commission could order Kloud Kart to stop using its customer list for marketing until the problem is fixed (s.75). The complainant could claim compensation (s.43). And Nana would have to explain to a board that has just invested why a regulator’s question could not be answered. Every future deletion request would also mean another manual search through laptops and inboxes.

### 2: Nobody owns a written definition of revenue — Severity: High

Nana and Finance start from the same orders but apply different rules in separate spreadsheets. The most likely differences are when an order counts (when it is placed, paid or delivered) and how refunds, cancellations, delivery fees and VAT are treated. Neither rule is written down, so neither person can prove they are right. This is a consistency problem, not an accuracy problem since both may be calculating correctly by their own rules.

The effect is that the board receives two revenue figures, and anything built on top of them inherits the disagreement, including the machine-learning forecasts the investors have asked about. I estimate the argument costs about eight hours of senior time each week, roughly 400 hours a year, spent rebuilding, reconciling and debating the numbers. The bigger cost is trust, a disputed revenue figure only weeks after a funding round.

### 3: Reporting and the shop compete for one machine — Severity: High

The website and the reports run on the same server, which has a fixed amount of processing power, memory and disk. When a Monday export of a few hundred thousand rows runs, it takes capacity away from customers trying to check out and this has slowed the website twice in the last month. The cause is two jobs sharing one machine.

Using some working assumptions, I estimate each slowdown puts about GHS 45,000 of orders at risk. That figure assumes a two-hour slowdown, about 250 orders an hour, 30% of customers giving up, and an average order of GHS 300. At last month’s rate of two incidents, that is about GHS 90,000 of revenue at risk each month. If between 10% and 50% of customers give up, the range is GHS 15,000 to GHS 75,000 per incident. This is revenue at risk, not profit, and the real figures should be measured.

This problem ranks third, even though it costs the most money today, because the fix is already approved and can be in place within weeks. The pre-approved second server becomes a reporting copy of the database: a read-only copy that updates itself within seconds. All reporting moves to it. Stock checks stay on the live database. The reporting copy can fall behind and must be watched. It is also one more copy of customer data, although deletions reach it automatically.

### 4: People do the data work by hand — Severity: Medium

Every step after a customer places an order depends on a person. Nana triggers the export, two people apply their own formulas, and Finance spots the mismatch. There is no schedule, no automatic check and no warning when a number is wrong. As a result, errors are found in meetings rather than before them, and if Nana is away on a Monday there are no weekly numbers at all.

### 5: Stock counts can go out of date, so the shop oversells — Severity: Medium

The brief says stock counts must never go stale, because that is how Kloud Kart oversells. When the stock count is out of date, items that have already sold out still show as available on the website, and a customer pays for something Kloud Kart does not have. This happens because stock is kept up to date through occasional manual checks rather than being read from the live database at the moment of each sale, so the number a customer sees can fall behind what is actually on the shelf. The brief confirms that this happens but not how often.

Every oversold order costs Kloud Kart in three ways: a refund to the customer, the payment provider’s fee for reversing the payment, and staff time spent apologising and sorting it out. Some of those customers do not come back. It also damages the brand at a sensitive moment, both in Accra and in the new Nigeria pilot, where first impressions count. Assuming about 40 oversold orders a month at around GHS 100 each, that is roughly GHS 4,000 a month, or GHS 48,000 a year, before counting the customers who never return.

## Questions I would ask Nana

Nana is unavailable for follow-up, so each question is answered with an assumption, listed in the table below.

1. When does an order count as revenue: when it is placed, paid or delivered? And how are refunds, delivery fees and VAT treated?
2. How are stock counts kept up to date, and when did the shop last oversell?
3. Does the Nigeria pilot use the same database, and how big could it get?
4. What exactly does the complaint say, and when does the 90-day deadline end?
5. What monthly running cost will Finance approve without a board vote?
6. How long does the Monday report take, and how will you know the Monday problem is solved?

## Assumptions

| # | Assumption | Used for | If it is wrong |
|--------|-------------------------------------------------------------------------------------------------------------|-----------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| A1     | The average order is about GHS 300                                                                          | Cost of each website slowdown                       | The cost estimate changes; the ranking does not                                                                                                           |
| A2     | Daytime orders run at about 250 an hour; a slowdown lasts about 2 hours, and about 30% of customers give up | Slowdown cost of about GHS 45,000 per incident      | The cost estimate changes; the ranking does not                                                                                                           |
| A3     | About 40 orders a month are oversold, costing about GHS 100 each                                            | Overselling cost of about GHS 48,000 a year         | The cost estimate changes; the ranking does not                                                                                                           |
| A4     | Reconciling revenue takes about 8 senior hours a week                                                       | Cost of the revenue dispute, about 400 hours a year | The cost estimate changes; the ranking does not                                                                                                           |
| A5     | USD 1 is about GHS 12, and one penalty unit is GHS 12                                                       | Currency conversions and fine amounts               | Figures change slightly                                                                                                                                   |
| A6     | Operations counts orders when they are placed; Finance counts payments after refunds and VAT                | How the revenue gap is fixed                        | If the gap is duplicates or a cut-off time, it is a data fix rather than a new definition                                                                 |
| A7     | Stock is updated through occasional manual checks, not at the moment of each sale                           | The overselling problem                             | If the website already reads stock live, overselling comes from the shelf and the system disagreeing, which better stock-taking fixes                     |
| A8     | Nigeria uses the same database and adds less than 15% of orders this year                                   | Timing of the warehouse                             | If Nigeria has its own database, the warehouse moves forward from Q3 to Q2                                                                                |
| A9     | The complaint is about a deleted customer still receiving marketing, and about 75 days remain               | Focus and timing of the complaint reply             | If the data came back through a backup restore, the focus moves to backups. If fewer than 45 days remain, the reply goes out before the first hire starts |
| A10    | Finance will accept up to about USD 500 a month, as a fixed bill                                            | Choice of warehouse                                 | If Finance accepts a capped pay-as-you-go bill, a cloud warehouse becomes the better choice                                                               |
| A11    | The Monday report takes 3–4 hours; success means a finished report at 08:00 that matches Finance’s figure   | What the first automatic report must deliver        | Changes the report’s contents, not the plan                                                                                                               |
| A12    | Hiring takes 6–8 weeks, and the existing developer can set up the reporting copy with guidance              | Timing of the first quarter                         | If the developer cannot, the reporting copy waits for the first hire, around week 8                                                                       |
