# IDFL Holidays — Supabase + historical archive (staging)

Do not merge this branch directly into production. The existing GitHub main branch still has a legacy application and publicly committed staff data. A full private-data removal/review and safe manager migration must precede release.

## Verified on 20 November 2026
- Supabase: hzyhtikotffweewneynu — 65 staff records.
- 14 unambiguous 2023 historical source snapshots imported as `payload.pre2024` (18 September 2023 balances and September–December 2023 weekly worked hours). Source: uploaded Staff Holidays Sheet 2024.xlsx. Historical, unverified; **not automatically added to 2024 entitlement**.
- 28 adjustments to 2025/2026 openings are tagged `pending_source_verification` in `private.staff_balance_reviews`. Before-change records are backed up in `private.staff_reconciliation_backups` under batch `2026-11-20-excel-year-opening`. These corrections must be validated against payroll/leave evidence.
- Rana Abdullah, Ibrar Tufail, and Osama Saleem Sabri were excluded from pre-2024 additions and starting-balance corrections.
- Rana's 27 July and 3 August 2026 weeks remain 40 worked / 0 holiday each; previously recorded five holiday weeks retained.
- Staff portal server functions installed in Supabase: `portal_set_email`, `portal_manager_get_email`, `portal_my_record`.
- No staff email has yet been authorised; `private.staff_portal_access` is empty.

## This branch
- `public/staff.html` — authenticated, read-only employee portal with Before 2024 archives.
- `public/supabase-config.js` — public project connection key only; no service key.

## Release blockers
1. Replace legacy manager index with the reviewed Supabase manager app from the local staging package, preserving the full interface.
2. Remove personal/employee data from public web assets, repo and deployment. Review access exposures and historical Git commits.
3. Configure Supabase Authentication URL allowlist for staging staff.html and verify real email OTP login.
4. Authorise one test employee email via manager-only RPC. Confirm separate employees cannot access one another or public staff_records directly.
5. Reconcile disputed year openings before declaring any figure verified, and test manager/employee calculations for the same staff.
6. Only deploy first to a separate staging Worker. Keep production Worker untouched until sign-off.
