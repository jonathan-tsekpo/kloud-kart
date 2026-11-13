# Improvement Beyond the Brief – Kloud Kart

**Prepared for:** Nana Adjei, Head of Operations\
**Date:** 13 November 2026\
**What was built:** Customer Data Register and Deletion Tracker (`05_customer_data_register_and_deletion_tracker.xlsx`)

## The problem the brief did not ask about

The brief asks Kloud Kart to answer **one** Data Protection Commission complaint within 90 days. It does not ask about four things that will cause Nana trouble if nobody handles them:

1. **The next request.** Each of the ~300,000 people on Marketing's list has the right to be deleted. If this complaint is handled by hand and then forgotten, the work starts from scratch every time.
2. **Proof.** Act 843 gives a defence to a company that can show it took "reasonable care" (s.43(2)) or acted with "due diligence" (s.80(3)). Kloud Kart has no record that would show either.
3. **Backups.** Restoring the database from a backup brings back every customer deleted since that backup was made. This is a common way a "deleted" customer reappears, and nothing in the brief watches for it.
4. **Timing.** The first data hire arrives around week 6–8, but the complaint reply is due before an engineer could automate anything.

## What was built

A working Excel file that Nana can run herself, with no engineer and no new software. It is already filled in with Kloud Kart's known data locations and the complaint checklist, and it calculates as she types.

| Tab | What it does |
|---|---|
| Start here | Plain instructions. It holds customer numbers only, never names or phone numbers, so the file itself does not become another copy |
| Board summary | The numbers for the board pack: places holding customer data, how many have an unknown number of copies, open and overdue requests, and days left on the complaint |
| Copy register | Eleven places customer data lives today or will live under the plan. Each has an owner, how a deletion reaches it, and when it was last checked. Rows turn red when a check is overdue |
| Deletion requests | One row per request, with a column for each place: Done, Not held or Pending. The status and target date fill in automatically, and the row turns red when overdue |
| Open complaint | Enter the date on the Commission's letter to get the deadline, a day-60 target, a countdown and an 11-step checklist with due dates and owners |
| After a restore | If a backup is ever restored, enter its date. Every deletion completed since then is flagged RE-APPLY |
| Settings | Kloud Kart's own targets: 30 days per request, a check every 30 days, and the 90/60-day complaint dates |

## How Nana uses it

- **Day 1:** enter the date on the complaint letter. The deadline and checklist dates appear.
- **Week 2:** fill in the copy register with the developer, writing "Unknown" where nobody knows.
- **Every week, about ten minutes:** update checks that are due and move open requests along.
- **Each board meeting:** copy the Board summary into the pack.

## What it is worth to Nana

| When this happens | Today | With the tracker |
|---|---|---|
| The board asks "how many copies of our customer list exist?" | Nobody can say | A number, plus how many places are still "Unknown" |
| The Commission asks what Kloud Kart did | Pieced together from memory under a deadline | A dated record of every place cleared |
| The developer restores a backup | Deleted customers silently return | A RE-APPLY list in minutes |
| Nana is on leave when a request arrives | Nobody knows the process | Anyone can open the file and see what is next |

**Cost:** nothing to buy; about two hours to set up and ten minutes a week. **Risk reduced:** an enforcement notice that could stop marketing to a 300,000-person list, compensation claims, and Nana being unable to answer her board on data protection weeks after a funding round.

## Limits

- It does not delete anything itself. People delete, and the tracker proves they did. From about month 2, the data engineer automates the deletions, and the tracker remains the record.
- It is only as good as its weekly update.
- It is not legal advice. The 30-day target and the reading of Act 843 should be checked with a qualified Ghanaian privacy adviser.
