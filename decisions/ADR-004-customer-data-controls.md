# ADR-004: Control customer-data copies, track every deletion, and keep contact details out of reporting

- **Status:** Accepted
- **Date:** 2026-11-13
- **Decision owner:** Kloud Kart engagement

## Context

Marketing exports a list of about 300,000 customers with no record of how many copies exist. Kloud Kart has 90 days to answer a Data Protection Commission complaint about a deleted customer’s data.

Under Act 843, a deletion must reach every copy in a way that prevents reconstruction (s.24, s.33), copies must be kept secure (s.28), and marketing needs the customer’s consent (s.40). Every copy is a place a deletion request must reach. Reports need a customer number to count repeat buyers, but never a name or phone number.

## Decision

Stop customer-list downloads to laptops. Marketing lists come from one controlled source. Keep a register of every place customer data lives, and a tracker showing each deletion request reached each place. When data is copied for reporting, names, phone numbers, emails, addresses and notes typed in by staff are removed; only a customer number and region remain. The complaint is answered by day 60.

## Alternatives considered

### Alternative A: Copy everything, including contact details, and hide them from analysts

- **How it would work:** All tables, including customer details, are copied into the reporting system as they are. Analysts see versions with the personal fields hidden.
- **Why it is attractive:** It is the quickest to set up. Nothing is lost if a field is needed later, and Marketing could build customer segments there.
- **Why rejected:** The reporting system would become a second full copy of 300,000 people’s details, and every deletion would have to reach it during an open complaint. Hidden fields stop being hidden the first day someone is given full access.

### Alternative B: Build a central customer-data platform now

- **How it would work:** Bring all customer information into one dedicated platform and handle access and deletion requests from there.
- **Why it is attractive:** One place for all customer data, and a base for future customer analysis.
- **Why rejected:** It costs money and months that Kloud Kart does not have before the complaint deadline. Moving data into a new platform does not remove the copies already on laptops, in email and with Marketing. The urgent gap is knowing where copies are, not where they should end up.

## Consequences

- **What this buys:** Kloud Kart can say where its customer data is and prove each deletion. The reporting copy holds no contact details, so it is the least dangerous copy.
- **What this costs:** Staff time to keep the register up to date (about ten minutes a week), and Marketing loses free downloads. Analysts cannot look up a named customer in reports. A customer number is still personal data in law, so the reporting copy stays on the register.
- **What it costs the client if I am wrong:** If a hidden copy is missed, or a phone number is buried in a notes field we did not remove, Kloud Kart could tell the Commission a copy is gone when it is not. That damages its credibility at the worst moment and means a clean-up.
- **What would make me revisit this:** Marketing needing customer segments with recorded consent, money for stronger access controls in year two, guidance from the Commission, or Nigerian law requiring something different.

## What this survives

It survives more deletion requests and a second complaint: the register and tracker are the evidence of “reasonable care” that Act 843 accepts as a defence (s.43(2)). It survives pressure to “just centralise everything”, because the problem today is not knowing where copies are. A register does not delete data by itself or make Kloud Kart compliant on its own, so the process should be checked by a qualified Ghanaian privacy adviser.
