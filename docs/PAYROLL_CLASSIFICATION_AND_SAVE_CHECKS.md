# Staff payroll classification and save-verification safeguards

The authoritative weekly ledger may contain **more than one type of hours in the same week**.

- **Worked hours** are the number in the source `Total hrs` column. Do not replace a recorded 8-hour working week with 40 simply because the employee is contracted for 40 hours.
- **Holiday pay** in source `Details` is a separate deduction from the holiday balance. For example, `8 worked + 32 holiday pay` must become `8 worked` and `32 holiday hours taken`, not `40 worked`.
- **Sick pay** in the source `Details` must use the **scheduled sick hours in the note**, not the default eight-hour day. For example, two notes for `14 sick` and `21 sick` consume 35 hours of a 35-hour company sick allowance, leaving zero available.
- Do not silently set a recorded holiday/sick claim to zero because it is historic. Retain original records and a private backup.
- Source notes that say `N hours holiday pay` must agree with their saved `hours`. Review conflicting notes before posting final statements; preserve an exception when a final payout is ambiguous.
- Annual summary fields (`totalWorked`, `calculatedHolidays`, `holidaysTaken`, `currentAvailableHrs`) must be recalculated on the **edited employee**, not trusted from stale browser caches.
- Changing a staff record must not write all other staff merely because JSON object key ordering differs between browser code and PostgreSQL JSONB.
- A manager save is **not confirmed** until the changed rows have been read back from Supabase and matched by revision and payload.
- Past Staff remain inactive. An explicit manager reactivation is required.
- Never commit personal weekly payroll sheets, raw source screenshots containing staff data, or private backups to public GitHub.

## Live-source boundary
This release fixes source rows evidenced by supplied screenshots and confirms summary-field consistency with current Supabase records. It **does not certify** that every historical source Excel row matches Supabase. The original full workbook is necessary for an independent row-by-row source audit. No data should be called legally certified solely because the arithmetic matches.
