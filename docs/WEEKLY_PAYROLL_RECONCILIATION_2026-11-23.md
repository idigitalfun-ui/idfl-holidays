# IDFL — Weekly payroll reconciliation (23 November 2026)

**Authority:** `WEEKLY HRS 111.xlsx`, worksheet `STAFF HRS`, payroll periods to 15 November 2026. The manager has approved the available-balance figures dated 18 September 2023 as original starting points. Do not overwrite these values with alternative holiday workbooks.

## Verified database state
- 65 employees preserved, of whom 37 are `inactive` (Past Staff). No status changes in this reconciliation.
- 15 Sep-2023 historical opening figures are matched in the historical archive; records without an unambiguous source match must not receive invented starting figures.
- 97 matched employee/year source groups were reviewed; most working-hour totals agree exactly. `Awais` in **Maynooth** (first 15 weeks of 2025, 429h) followed by `Awais Rasheed` (37 weeks, 1,223.5h) is a continuous payroll series of **1,652.5h**, matching Supabase.
- Zero-hour source rows may be absent from the database without changing earned leave. Inactive employees' extra zero-hour rows must not reclassify them as Active.
- Supabase recalculated and backed up 59 changed records. Cached `totalWorked`, `calculatedHolidays`, and `holidaysTaken` now agree with weekly and chargeable-leave entries for **all** stored 2024, 2025, and 2026 records (0 discrepancies in the post-update SQL audit).
- The special Rana Abdullah, Ibrar Tufail, Osama Saleem Sabri payroll and bank-holiday rules were retained. Source salary lines sometimes place **40** in the rate column and leave the worked-hours column blank; these are manual exceptions, not independently extracted payroll hours.

## Do not auto-merge these ambiguous identities
- **Adam Walker:** source rows at **Arklow**, historic profile at **Maynooth**. Not proven to be the same employee.
- **Patrick Dobos:** source rows at **Killarney**, historic profile at **Portlaoise**; some entries postdate the profile's leaving date.
- **Szymon:** source contains Newbridge zero-hour rows while the stored employee is in Thurles.
- **Sean Trant ≠ Sean Ryan** without stronger evidence.

No source rows were attributed to these conflicting profiles, and no former staff were reactivated.

## Frontend safeguard
The `public/index.html` Supabase save path now rejects any unconfirmed `inactive → active` transition. The explicit **Reactivate** action requires a confirmation. Changing working hours or editing a former employee's historic record does not by itself make them Active.

## Sharing
Employees use a private, revocable, read-only permanent link. Manager authentication remains required for editing. Avoid publicly committing staff data, confidential payroll rows, access tokens or exported backups.

## Important limits
- A post-2023 historical opening exists for only 15 unambiguously matched staff; 50 others cannot have a verified 18 September 2023 starting figure inferred from this source.
- The application models bank-holiday credit at one hour per eligible selected date. This is an application assumption, not a certified statutory entitlement.
- Source-derived numbers should not be labelled statutory/payroll certified until the unresolved identity cases and statutory basis have been reviewed.
- `WEEKLY HRS 111.xlsx` does not include later weeks beyond 15 November 2026. Do not invent them.
- Private, detailed source-to-ledger comparison belongs in the confidential reconciliation workbook, **not in this public GitHub repository**.
