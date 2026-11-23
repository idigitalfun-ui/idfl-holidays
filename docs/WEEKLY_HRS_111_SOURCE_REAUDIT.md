# Payroll source re-audit — 23 November 2026

## Source of truth
Original private `WEEKLY HRS 111.xlsx`, sheet `STAFF HRS`, weekly headings and payroll `Total hrs` / `Details` columns. The 2024 holiday workbook supplies the original **18 September 2023** available-balance snapshot where names can be positively matched. The private payroll workbook and personal rows are **not** committed to this public repository.

## Previously missed classifications
- Salary-paid staff can have hours written in the apparent pay-rate column. Read the actual source row; `0 worked + 40 holiday pay` is **not** `40 worked`; `8 worked + 32 holiday pay` is **not** `40 worked`.
- 2026 payroll notes contained scheduled sick hours. Do not substitute the default seven/eight-hour day. A 35-hour company allowance can be fully used even when fewer than five separate payroll notes exist.
- Payroll instructions to pay a **remaining** holiday balance without a numerical amount require a review, not an invented deduction.
- 2024 and 2025 records had many sick-pay rows imported with default seven-hour values. Source-backed scheduled hours and previously missing records were corrected in Supabase with private backups.
- Source-matched **2023** employees had holiday pay after 18 September 2023 that must be deducted from the original source opening. Worked-hour accrual alone overstated their 2024–2026 carry-forward.
- For matched source records, `opening2024 = 2023_snapshot + 8% × source_worked_hours_after_snapshot − 2023_holiday_pay_after_snapshot`. Each later year inherits the prior closing, never another full opening credit.

## Supabase write verification
The manager's edit/save flow compares canonical JSON (no mass rewrites due to object key order), recalculates annual summary fields only for edited staff, and **reads back** each changed row's payload and revision before showing “Verified saved to Supabase.” A save conflict or failed verification remains visible and blocks overwriting.

## Protected status and unresolved exceptions
Past Staff remain inactive (37 records). No public employee links permit editing. Employee identities with mismatched shops or duplicate names have **not** been merged. Ambiguous sick-pay times, unquantified final holiday payouts, public-holiday statutory calculations, and 2023 opening balances without positive source matches remain **uncertified**, rather than silently assigned numbers.

## Testing
- Read all relevant dated original workbook rows for corrections.
- Database source records were backed up before changes and re-read after saving.
- JavaScript syntax was checked in both manager and read-only employee pages.
- A full authenticated browser end-to-end test and confirmation of the newest Cloudflare deployment are separate release checks.
