# Historical opening source audit and safeguards

## Source scope
The private `WEEKLY HRS 111.xlsx` contains payroll periods before September 2023 and records as early as December 2019. The original `Staff Holidays Sheet 2024.xlsx` has a September 18, 2023 available-balance column with **some blank cells**.

**A blank opening balance is unknown, not verified zero.** Do not infer a positive balance from accrued hours alone without identifying historical leave payments, final payouts, dates of employment and source identity. Employees hired after September 2023 have no employment at that original snapshot and must start tracking from their actual date of hire.

## Manager-approved accounting chain
- Keep confirmed 18 September 2023 source balance unchanged.
- Add 8% of matched worked hours in the remainder of 2023 and subtract dated 2023 holiday-pay entries for matched staff.
- For employees whose 2023 original snapshot is blank, reconstruct only when source history is sufficiently complete and matchable. Mark reconstructions separately from confirmed original figures.
- Carry each year's **calculated closing** to the next year's opening, without adding the saved 2024/25 opening figures as new credits.
- When a historical pay-rate cell contains `40 hrs` but the `Total hrs` worked cell is blank, do not silently insert 40 worked hours or assume zero; record the ambiguity.
- Record bank-holiday credit once per year; avoid adding historical credit again to an already-carried closing.

## Additional source checks
- The historical audit reviewed all **65** staff profiles, their join dates, their original 2023 snapshot status, and all exact-name/controlled-alias earlier payroll evidence. Private audit workbook lists 40 identity, source coverage or entitlement review cases.
- One 2023 employee with 30 pre-September and 15 post-September 40-hour weeks has source-derived 144 hours earned in 2023. This reconciles with the saved 2024 opening of 144. The source reconstruction is in Supabase, without adding a second 2024 credit.
- Ten matched autumn 2023 worked-week figures differed between the original 2024 holiday sheet and the authority `WEEKLY HRS 111.xlsx`. The verified source weeks replaced the discrepancies for nine staff, and their annual carry-forwards were recomputed with private backups. A different-shop identity case was held back.
- Two historical 2023 staff histories have documented gross accrual but an ambiguous final holiday payout. Their raw evidence is archived with a payout-review flag; neither a final payout nor an entitlement balance was silently invented.
- A separate 2025-to-2026 carry-forward omission for a former employee was repaired with backup while retaining `inactive` status.

## Release controls
- The manager UI visibly warns when an employee joined before September 2023 but the historical opening is not verified.
- The read-only employee portal receives only that employee's permitted start date and historical record, displays source-review cautions, and does not add earlier bank credits twice for source-reconstructed records.
- The source workbook, raw payroll contacts/identifiers, detailed source rows and employee-by-employee audit **must remain private**. Never commit them to the public GitHub repository.
- All Past Staff remain inactive. The manager save path separately verifies changed data by reading the rows back from Supabase.

**Limitations:** A payroll work-hour total does not itself establish a final annual leave entitlement. Pay-rate-only weeks, employees whose names/shops or stated join dates conflict with the source, and unquantified final-pay requests require clarification. This reconciliation is a source-based tracker audit and not a statutory payroll certification.
