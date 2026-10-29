# Maldives Crime Statistics: A Three-Year Exploratory Analysis (2024–2026)

An independent exploratory data analysis of reported crime statistics from the Maldives Police Service, covering 12 categories across 2024, 2025 and 2026 (to October). The project looks at how recorded cases changed between years, which categories moved most, and what the data can and cannot support.

**Full report:** [Maldives_Crime_Statistics_2024-2026.docx](Maldives_Crime_Statistics_2024-2026.docx)

## Key findings

- **Total recorded cases fell 4.2%** from 2024 to 2025 (12,641 → 12,113).
- **Drugs is the one consistent increase:** 1,670 → 2,066 → 2,128 cases (2026 to October). That is about 139, 172 and 213 cases a month, and drugs grew from 13.2% to 20.9% of all cases.
- **Traffic accidents peaked in 2025** at 3,079 cases, 6.8% above 2024. Whether 2026 is lower depends on the cut-off month of the 2026 data.
- **All ten other categories fell from 2024 to 2025.** Sexual offences, robbery and counterfeit and forgery kept falling in 2026 under either cut-off.
- **These are recorded cases, not proof that crime itself changed.** The annual data cannot show whether the Prevention of Gang and Other Serious Offences Act (2025) or the Land Transport Act (ratified August 2026) affected the counts.

![Cases by category](images/fig1_cases_by_category.png)

## An important data caveat

The 2026 figures cover only about ten months (the source notes say "up to Oct"), while 2024 and 2025 are full years. Raw 2026 totals are therefore biased downward. To handle this, the analysis:

1. compares 2024 and 2025 directly, as the only two full years;
2. converts 2026 to **cases per month** (January–October ÷ 10);
3. tests every 2026 comparison against a **nine-month** cut-off, because the exact last month is not recorded, and reports a direction as "not settled" when the two readings disagree.

![Monthly rates](images/fig2_monthly_rate_drugs_traffic.png)

![2026 sensitivity](images/fig3_2026_change_sensitivity.png)

## Data

| Item | Detail |
|---|---|
| Source | Maldives Police Service crime statistics (<https://www.police.gov.mv/crime-statistics>) |
| Coverage | 12 categories × 3 years (2024, 2025, 2026 to October) |
| Measure | Annual case counts per category |
| Files | `MALDIVES_CRIMESTATS_2426.xlsx` (primary dataset), `evidence.xlsx` (news and legislation notes) |

The yearly totals in the spreadsheet (12,641, 12,113, 10,205) reconcile with the sum of the 12 categories, and no values are missing. Traffic accidents and lost items are incident reports rather than crimes (33.6% of 2025 cases), so the total is best read as "recorded cases".

## Repository contents

```
.
├── README.md
├── Maldives_Crime_Statistics_2024-2026.docx   # full written report
├── crime.ipynb                                 # analysis notebook
├── MALDIVES_CRIMESTATS_2426.xlsx               # case counts by category and year
├── evidence.xlsx                               # news and legislation context
└── images/                                     # figures used in this README
```

## Running the notebook

```bash
pip install pandas matplotlib openpyxl jupyter
jupyter notebook crime.ipynb
```

Keep `MALDIVES_CRIMESTATS_2426.xlsx` in the same folder as the notebook; it is read with `pd.read_excel(..., skiprows=2)`.

## Method

- Absolute and percentage change between full years (2024 → 2025).
- Cases per month for 2026, with a nine-month sensitivity check.
- Category shares of the total, and a split of the total into drugs, traffic accidents and everything else.
- Every finding is written as an observation, an interpretation and a limitation. No significance tests are used: the figures are complete tallies rather than a sample.

## Limitations

- Only 36 values exist (12 categories × 3 years), with a partial final year.
- The measure is not formally defined (reported crimes versus cases attended), and categories mix crimes with accidents and lost property.
- There are no population, visitor, regional or monthly figures, so no rates per head and no seasonality.
- A change in recorded cases can reflect reporting behaviour, enforcement, classification or recording practices, not only changes in underlying crime.
- News items and legislation give context only; they cannot establish cause.

## Possible next steps

1. Confirm the exact end date of the 2026 data.
2. Look for monthly or quarterly counts and rebuild the analysis on them.
3. Define each category and separate crimes from accident and lost-property reports.
4. Add population and visitor figures to compute rates per 100,000 residents.
5. Test dated hypotheses, for example monthly drug cases before and after May 2025.

## Sources

- Maldives Police Service, crime statistics: <https://www.police.gov.mv/crime-statistics>
- Presidency of the Maldives, Prevention of Gang and Other Serious Offences Act (Act No. 7/2025): <https://presidency.gov.mv/Press/Article/33786>
- Presidency of the Maldives, Land Transport Act, 31 August 2026: <https://presidency.gov.mv/Press/Article/37273>

## License

Add a license of your choice (for example MIT) before publishing. The underlying statistics belong to the Maldives Police Service.
