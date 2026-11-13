# Data Strategy Recommendation – Kloud Kart

**Prepared for:** Nana Adjei and the Kloud Kart board\
**Date:** 13 November 2026

## 1. Executive recommendation

Kloud Kart should do four things, in this order: protect the website, lock down customer data, agree one set of numbers, and then build up history for future analysis. Each step fixes a problem the company has today, and none needs a large new platform.

The pre-approved second server becomes a reporting copy of the database: a read replica that updates itself within seconds. All reporting moves to it, so Monday reports can no longer slow the website. Customer lists stop being downloaded to laptops, every copy of customer data is recorded, and every deletion request is tracked, so the open Data Protection Commission complaint is answered with evidence by day 60. Operations and Finance agree one written definition of revenue and use one automatic daily report, so they quote the same figure at the board meeting in month 5. From month 7, a small warehouse keeps the history the shop database overwrites and shows Ghana and Nigeria side by side.

Stock is read from the live database at the moment of each sale, so the website stops showing items that have sold out. Everything else refreshes once a day. Kloud Kart does not need a lakehouse, company-wide real-time dashboards or machine learning this year. Tools cost about USD 110–370 a month, or roughly GHS 20,000–42,000 for the whole year. That is less than a single bad Monday currently costs in lost orders.

## 2. Proposed architecture

The live database keeps running the website and the stock checks. Everything else, including reports, exports, and Finance and Marketing requests, moves to the reporting copy on the second server. From month 7, a small warehouse is filled from the reporting copy every night, with names, phone numbers, emails and addresses removed.

I chose the reporting copy first because it is already approved, can be set up in days by the existing developer, and uses skills he already has. A cloud warehouse would take reporting off the shop just as well, with almost nothing to manage. But it needs someone to organise the data before Nana can use it, and that person does not start until month 3. It would also move customer data to a new place while a complaint is open, on a pay-as-you-go bill Finance has already flinched at. It stays a sensible later step if Finance accepts a capped bill or the data passes about 500 GB.

The small warehouse comes in month 7 because by then the reporting copy will not be enough. The reporting copy cannot keep history the shop overwrites, it cannot combine Ghana and Nigeria cleanly, and it cannot give a copy without contact details. It is an ordinary database run by the hosting company, with a fixed monthly bill Finance can plan for. A data lake, which is cheap storage for raw files of any kind, is not needed: Kloud Kart’s data is 40 GB of tidy records. A lakehouse, a single platform for reports and machine learning on very large data, is not needed either. It is built for huge data and machine-learning teams, and it would need skills neither hire will have.

## 3. Processing recommendation

Reports refresh once a day, overnight, and show when they were last updated. Revenue, marketing and finance decisions do not change if a number is a day old rather than ten seconds old. Stock is the one exception. A stale stock count is how Kloud Kart oversells. Today stock is kept up to date through occasional manual checks, so the existing developer changes the website to take each item off the count in the live database the moment it is ordered, and to check that count before accepting a sale. Stock is never read from a copy. I do not recommend a “streaming” system, which updates every number second by second. At about three orders a minute, it would need someone on call day and night to produce a number the live database can already give, and two hires cannot staff that.

## 4. Hiring plan

The first hire should be a Data Engineer, the person who builds and looks after the data systems. Recruiting starts on day 1, and they should be in post around weeks 6–8. In their first 90 days, they:

- take over the reporting copy and set up backups with a tested restore;
- build the routine that deletes customers from every copy, and finish the complaint actions;
- replace laptop exports with one controlled marketing list;
- set up the nightly refresh and failure alerts.

The second hire should be an Analytics Engineer, the person who turns raw data into agreed, trusted reports, in post around month 3. They:

- sit with Nana and Finance to rebuild how each calculated last month’s revenue;
- write the one-page definition and get both to sign it;
- run the new daily report alongside Nana’s spreadsheet for four weeks until the totals match, then retire the spreadsheet.

The engineer comes first because the urgent problems, the slow website and the complaint deadline, are engineering problems. We are not hiring a Data Scientist and not building ML demand forecasting this year. Forecasting on top of contested historical revenue numbers yields contested predictions. We will revisit ML only after 12 months of clean, undisputed historical data is established.

## 5. Running costs

The reporting copy on the second server costs an estimated USD 80–150 a month from month 1. Backups stored away from the main machine add USD 10–30 from month 2. A free reporting tool with an automatic nightly refresh, running on one small server, adds USD 20–40 from month 3. The small warehouse adds USD 60–150 from month 7. In total, that is about USD 110–220 a month for the first six months and USD 170–370 a month after that. These are estimates to be confirmed with suppliers. Staffing is the two salaries already approved.

## 6. Answers to the investors’ questions

If the board asks why there are no real-time dashboards, Nana can answer that stock will be checked live at the moment of each sale, and nothing else changes a decision within seconds. If it asks about a lakehouse or Snowflake, the answer is that our data is only 40 GB, a lakehouse is built for huge data, and a cloud warehouse is a later step with a written trigger. If it asks when AI forecasting arrives, the answer is that the decision is at month 12, because until we agree what we sold last month, a forecast would only automate the argument. If it asks whether we comply with the Data Protection Act, the honest answer is not provably today, but the complaint is answered with evidence by day 60 and every copy of customer data is on a register by month 3.

## 7. When to reconsider

The warehouse moves forward to Q2 if Nigeria turns out to use a separate database. A cloud warehouse replaces the small one if Finance accepts a capped pay-as-you-go bill or the data passes about 500 GB. Stock would only need its own live system if one stock pool were sold across several countries or sales channels. If the budget falls to one hire, the data engineer alone still delivers the first quarter and the daily report, and the warehouse slips by a quarter.
