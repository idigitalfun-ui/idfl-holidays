# IDFL Employee-Specific Year Navigation

## Source limitation (23 November 2026)
The latest file supplied as `WEEKLY HRS 111.xlsx.lnk` is a **Windows shortcut**, not the Excel workbook. It points to a local Windows `D:\Rota\` location; it does **not** contain payroll cells. Therefore **this change uses previously imported and saved Supabase records** and does not claim to independently re-audit the source workbook. The actual `.xlsx` must be uploaded for a new row-by-row reconciliation.

## Year-tab rules
- Always restrict the displayed year tabs by the employee's recorded **employment start year**, not a global selection shared across all employees.
- Employees who joined in **2026** show only 2026; those who joined in **2025** show 2025–2026; those who joined in **2024** show 2024–2026.
- Earlier employees show the 2023 historical tab only when source data (worked weeks, recorded snapshot, or dated 2023 holiday entries) exists.
- **Osama Saleem Sabri, Rana Abdullah and Ibrar Tufail** have an explicit `2023 & earlier` review tab for their requested historical evidence. The first two have **unverified** earlier salaried records and must not be given fictional worked hours; Ibrar has recorded 2023 hours, including 1,200 worked before 18 September 2023. Historical tabs identify the source and uncertainty.
- The “Before 2024” global tab is not shown for new joiners. Older records remain accessible in Past Staff with no status changes.

## Year detail panels
Each employee's available annual panels show actual saved weekly worked hours, holiday-pay deductions, sick pay, accrued leave, opening and remaining balance, and dated bank holidays with selection status. Osama's and Ibrar's selected bank-holiday dates remain **separate** from their holiday-hour balances, per manager instruction.

## Data privacy
Employee access is through the existing hashed, revocable read-only private token and only returns the linked employee's records. Sick history is included in that narrowly scoped response for the employee's own view; **no** general staff listing or manager-write permission is granted.

## Release checks
JavaScript syntax verified on manager and private staff pages. Supabase read-only function's hashed-token matching retained and the sick-history field verified in its definition. The change does not mutate worked hours, leave records, joining dates, opening figures, bank-holiday values, staff status or historic snapshots.

The Cloudflare production deployment and an authenticated browser walkthrough are **not** verified by this code change.
