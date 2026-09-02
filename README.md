# Autism Assessment Waiting Lists in England

A Tableau dashboard built on NHS England's published autism waiting time statistics, covering April 2025 to June 2026.

**Dashboard:** [[View on Tableau Public](ADD_YOUR_LINK_HERE)](https://public.tableau.com/views/AutismAssesmentWaitingTimesinEngland/Dashboard1?:language=en-GB&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)
<img width="940" height="524" alt="image" src="https://github.com/user-attachments/assets/96dad729-08a5-4c5c-96fc-3125f5abf422" />

## The question

How long are people waiting for an autism assessment in England, and is it getting better or worse?

## Data source

NHS England, Autism Statistics, July 2025 to June 2026 (published by NHS England Digital).

Source: https://digital.nhs.uk/data-and-information/publications/statistical/autism-statistics

Open data, published monthly. I used the England-level files from two publication periods:

- April 2025 to March 2026
- April 2026 to June 2026

<img width="940" height="338" alt="image" src="https://github.com/user-attachments/assets/f4acd267-d8ec-47ba-9339-6ef47345812b" />

<img width="940" height="341" alt="image" src="https://github.com/user-attachments/assets/562395db-6c38-456c-b09e-b4bbcb55ba80" />



## Files in this repository

| File | What it is |
|---|---|
| `autism_england.csv` | The cleaned dataset used by the dashboard. 90 rows. |
| `autism_england_working.xlsx` | Working file, including the lookup table and formulas used to build the labels. |
| `autism_waiting_lists.twbx` | The Tableau workbook. |

## What I did to the data

The raw files contained around 4,700 rows. Preparing them took five steps.

1. **Filtered to England only.** The source stacks four population breakdowns in one column: England, age group, gender and ethnicity. All four describe the same people. Charting the file as it comes would count everyone four times.
2. **Filtered to six metrics out of fifty-four.** ASD12 (new referrals), ASD13 (closed referrals), ASD16 (people waiting), ASD16a (waiting over 13 weeks), ASD16b (children waiting), ASD16d (adults waiting).
3. **Joined two publication periods.** The current release covers only three months. Three points is not a trend, so I appended the previous release to get fifteen months.
4. **Relabelled the metric codes.** The original metric names run to around twenty words, which will not fit on a chart axis. I built a small lookup table and used XLOOKUP to map each code to a short label, then pasted the result as values so the file does not depend on the lookup table.
5. **Checked the output.** Row count verified at 90 (six metrics across fifteen months), with no duplicated or missing months.

Result: 4,700 rows reduced to 90 rows that answer one question.

<img width="940" height="331" alt="image" src="https://github.com/user-attachments/assets/701b04e9-a6d9-4af2-bc27-f1a64806c25a" />


## What the dashboard shows

- **294,792 people** had an open referral for a suspected autism assessment in June 2026.
- **256,017 of them (around 87%)** had already waited longer than the 13 weeks NICE recommends.
- The number waiting **rose over the period**, from 246,321 in April 2025, peaking above 310,000 in May 2026.
- **New referrals exceeded closed referrals in every month of the series.** In June 2026, 17,509 referrals came in and 13,492 closed. The list grows month on month.

The last point is the most important. This is not a backlog clearing. More people join the waiting list than leave it, so waiting is a long, open-ended state rather than a short gap before assessment.

<img width="940" height="524" alt="image" src="https://github.com/user-attachments/assets/6d07b21a-2f38-4104-8bea-d3355a2cba59" />


## Limitations

Both of these are documented in the NHS publication's data quality notes and both affect how the charts should be read.

1. **The June 2026 fall is a data gap, not an improvement.** One provider did not submit data for that month, which removed around 22,900 people from the England total. Nobody came off the waiting list.
2. **The figures cover mental health services only.** Autism assessments carried out by community paediatric services are not currently identifiable in the dataset, so children seen by those teams are not counted. The true number waiting is higher than shown.

The data also says nothing about what people experience or need while they wait. It establishes the scale and direction of the problem, not the nature of it.

## Tools

Excel for data preparation, Tableau Public for the dashboard.

## About

Built as part of a Level 3 Data Technician Skills Bootcamp.
