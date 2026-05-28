# Mane & Steel -- ChemistryRx Fulfillment Incident Report
**Prepared by:** Tim Blackburn, Mane & Steel Operations
**Date:** May 28, 2026
**Sent to:** ChemistryRx Leadership

---

## Our Position

ChemistryRx has indicated that nothing is coming through from our system. That is not accurate.
We have three independent sources of evidence that contradict it: our Shopify store data, our
backend server database, and our email outreach record. This document presents all three.

Our backend database contains **85 orders with LifeFile order IDs dating back to September 2025.**
LifeFile only generates an order ID when it accepts a submission. Every one of these IDs is a
receipt from ChemistryRx's own platform confirming that our system successfully transmitted the
order. This is not a new or untested integration -- it has been running and processing orders
for 8 months.

We are not writing this to assign blame. We are writing this because we have 13 patients
waiting on medication, we have made 12 documented contact attempts in 7 days with no
substantive response, and we need ChemistryRx to engage with the actual data.

---

## Section 1 -- Orders That Went Through (Proof of Transmission)

The following 9 orders were successfully received, compounded, and shipped by ChemistryRx
in May 2026. Every row has a USPS tracking number pulled directly from the Shopify Admin API
and a matching `lifefile_processed` record in our backend MongoDB database.

**If nothing is coming through our system, these 9 orders cannot exist.**

| Order | Customer | Order Date | Fulfilled | Tracking Number | Delivery Status |
|---|---|---|---|---|---|
| #1117 | Ethan Pridgen | May 1 | May 7 | 9400136208303502238632 | Delivered |
| #1119 | Nathan Santos | May 3 | May 7 | 9400136208303502238250 | Delivered |
| #1124 | Colton Simmons | May 15 | May 19 | 9400136208303511384481 | Delivered |
| #1125 | Jeremy Monahan | May 16 | May 26 | 9400136208303516151118 | In Transit |
| #1126 | Thomas Vawter | May 18 | May 19 | 9400136208303511381312 | Delivered |
| #1127 | Esteban Kaulia | May 18 | May 19 | 9400136208303511381176 | Delivered |
| #1128 | James Appich | May 18 | May 19 | 9400136208303511384993 | Delivered |
| #1131 | Bryan Miller | May 19 | May 22 | 9400136208303514359813 | Delivered |
| #1132 | Ian Barno | May 19 | May 26 | 9400136208303516151484 | In Transit |

---

## Section 2 -- Orders Transmitted But Never Acknowledged

These 6 orders show `lifefile_processed` in our backend -- our system sent them -- but
ChemistryRx has not returned tracking numbers. These patients are still waiting.

| Order | Customer | Order Date | Days Waiting | Backend Status | LifeFile Order ID |
|---|---|---|---|---|---|
| #1118 | Christian Kim | May 3 | 25 days | lifefile_processed | 103973089 |
| #1120 | Luis Tapia | May 5 | 23 days | lifefile_processed | 103462479 |
| #1121 | Arne Gerhard | May 9 | 19 days | lifefile_processed | 103973092 |
| #1123 | Tonatiuh Kent | May 12 | 16 days | lifefile_processed | 103973096 |
| #1129 | Zahra Baradaran | May 18 | 10 days | lifefile_processed | 103973101 |
| #1134 | Luke Multz | May 24 | 4 days | lifefile_processed | 104040382 |

Note on #1118 (Christian Kim): ChemistryRx flagged as duplicate therapy -- a pharmacy-side
compliance decision never communicated to us directly.

---

## Section 3 -- The Break Point: May 21

Orders May 1-19 transmitted and fulfilled normally. Around May 21, tracking numbers stopped
coming back from ChemistryRx. Our server continued running and logging transmissions throughout.

7 additional orders are stuck before transmission -- no matching backend record found:

| Order | Customer | Order Date | Days Waiting |
|---|---|---|---|
| #1122 | Vincent Derafelo | May 9 | 19 days |
| #1133 | Wyatt Smith | May 20 | 8 days |
| #1135 | Vincent Petrera | May 26 | 2 days |
| #1136 | Oscar Hinojosa | May 26 | 2 days |
| #1137 | Martin Lassen | May 26 | 2 days |
| #1138 | Nihaar Narayan | May 27 | 1 day |
| #1139 | Jacob Aguirre | May 28 | 0 days |

---

## Section 4 -- 12 Contact Attempts in 7 Days, Zero Substantive Response

### Direct emails to ChemistryRx

| Date | From | To | Response |
|---|---|---|---|
| May 22 | Tim Blackburn | Houry Lepedjian + Jonathan | None. Houry replied to Chris about an unrelated matter (Christian Kim). Did not address Tim's email. |
| May 26 | Tim Blackburn | Taylor Zane + Carlos Orozco | None |
| May 26 | Chris Kite | Houry + Taylor | None |
| May 27 | Chris Kite | Taylor Zane + Jessica Keenan | None |

### LifeFile escalation (ChemistryRx was unreachable -- had to go through a third party)

| Date | From/To | Notes |
|---|---|---|
| May 27 | Tim to Stefan Leon (LifeFile) | Only available channel to reach ChemistryRx |
| May 27 | Stefan to Tim | "Call the pharmacy directly" |
| May 27 | Tim to Stefan | Pushed back -- needed real resolution |
| May 27 | Stefan to Houry (CC) | Stefan asked Houry directly to respond |
| May 27 | Tim to Stefan | Followed up. No movement. |

### Voicemails

Tim Blackburn: 1-2 voicemails. Chris Kite: ~3 voicemails. Zero callbacks.

**Total: 12 contact attempts. 5 ChemistryRx staff contacted. Zero substantive replies to Tim Blackburn in 7 days.**

---

## Section 5 -- 8-Month Transmission History

85 LifeFile order IDs in our database since September 2025. Each ID = ChemistryRx's own
platform confirming receipt. This is not a new or broken integration.

| Period | Orders | First ID | Last ID |
|---|---|---|---|
| Sep-Oct 2025 | 12 | 97836421 | 98466396 |
| Nov-Dec 2025 | 14 | 98543229 | 99792828 |
| Jan-Feb 2026 | 16 | 99971151 | 101345781 |
| Mar-Apr 2026 | 18 | 101451636 | 103175691 |
| May 1-20 2026 | 15 | 103368233 | 103973101 |
| **Total** | **85** | | |

---

## Section 6 -- What We Need

1. **Confirmation of receipt** for the 6 orders in Section 2 (LifeFile IDs listed)
2. **Explanation** for why tracking stopped after May 19
3. **A named technical contact** who responds when the integration breaks
4. **Clear requirements** from ChemistryRx if anything needs fixing on our end -- "nothing is coming through" is not actionable

---

## Data Sources

- Shopify Admin API (pulled May 28, 2026)
- MongoDB production database on DigitalOcean (pulled May 28, 2026)
- Email records: tim@maneandsteel.com and chris@maneandsteel.com
- MDI Integrations Slack thread (Ramin, May 2026)
