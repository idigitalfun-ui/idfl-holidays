# Single-source historical holiday opening (23 November 2026)

## Rule
The **only original holiday balance** is the amount in **Staff Holidays Sheet 2024.xlsx**, column **“Holidays Available until 18.09.23”**. It is an amount available **as of 18 September 2023**, not an additional 2024 or 2025 credit.

For a positively matched employee, calculate the 2024 starting amount as:

`2023-09-18 source balance + 8% of documented Sep–Dec 2023 worked hours`.

The recorded worked weeks and holiday-pay entries then determine each year's closing:

`closing(year) = opening(year) + 8% × recorded worked hours(year) − chargeable holiday hours(year) + selected eligible bank-holiday credit(year)`

For **2025 and 2026**, opening(year) is exactly the **previous year's calculated closing**. Do **not** also add the prior imported `years[year].opening` field. Selected bank-holiday credits are counted **once in the relevant year**, then naturally carried forward, not added again as historical credits in each later year.

## Source coverage and caution
- **15** original 2023 balances have a confirmed employee match; their stored 2023 hours have been carried once into the calculation.
- The 2024 source also contains worked weeks for **Mantas** and **Vlad**, but their starting-balance cells are blank. Those worked weeks are documented; a missing initial balance is **not independently verified as zero**.
- **Rana's** matching 2023 opening amount is absent, and the source-only provisional calculation has no unverified extra annual opening added. His original payroll sick and holiday notes are preserved for audit.
- Remaining employees without a reliable 2023 source amount are **not certified**. Do not overwrite uncertain historic staff entitlements with guessed zeros.
- For source-matched records, the manager and private read-only employee views must recalculate carried openings rather than trusting stale later-year caches.
- For **Rana**, previously excluded June/July 2026 holiday-pay notes are again charged as recorded. Sick requests were preserved but the 2026 sick-used amount is excluded following the employee's explicit correction.
- **Past Staff remains Past Staff** unless a manager explicitly confirms a reactivation.
- **Bank holiday credit remains 1 hour per eligible selected date** in this application's internal model; this is not a certified statutory public-holiday entitlement.

## Data controls
All affected records were copied to `private.staff_reconciliation_backups` under batch `2026-11-23-source-2023-single-opening-and-restored-leave` before changing balances. Private staff payroll data and identifiers must not be committed to the public GitHub repository. Source payroll workbook is authoritative for worked hours.
