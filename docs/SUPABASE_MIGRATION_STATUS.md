# IDFL Holidays: Supabase migration release notes

## Database
Project: `hzyhtikotffweewneynu` (Cloudflare Worker uses only publishable key).
- 65 staff records retained in Supabase.
- Payroll: 2,850 unambiguously matched 2024–2026 weekly working-hour entries matched `WEEKLY HRS 111.xlsx` with zero differences.
- Holiday taken and stored year-end openings remain the source of the 2026 balance calculation. The 28 Excel-only year opening adjustments were reversed; before-and-after backups remain in the private schema.
- Preserved Rana Abdullah, Osama Saleem Sabri and Ibrar Tufail bank-holiday treatment and Rana's 40 + 40 working hours in the two corrected weeks.
- 14 pre-2024 historical source snapshots are **unverified read-only historical context**, never included in calculations.

## App
- `public/index.html`: manager-only Supabase tracker, version-checked updates, and backup handling for old browser edits.
- `public/staff.html`: email-verified, read-only individual staff view. Manager must assign each employee email in Share/Link. An unassigned employee cannot see a record.
- `public/supabase-config.js`: public URL and publishable key only.
- Staff data removed from current GitHub branch files; review and clean public Git history separately.

## Release / review
- Cloudflare Worker `idfl-holidays` undeployed version `77277700-35fc-4346-a5d9-417b810e4106` uploaded for review.
- Security is enforced by Supabase RLS, manager-only writes, and verified-email employee RPCs.
- Browser sign-in and cross-device flows require user acceptance testing. No email has yet been authorised for a staff portal.
- The payroll workbook does not by itself prove the historic opening entitlement. Do not call the resulting remaining balance an independently audited legal entitlement.
- Do not disclose service-role keys or upload personal data to public assets.

## Testing
- Manager login -> verify staff lists and 2026 computed balances.
- Change a staff status -> reload on another device; ensure it persists.
- Assign one test staff email -> verify that staff user sees only their record, not other staff or manager controls.
- Download browser backup on any device with old local changes before switching.
- Compare sample payroll weeks (including Rana) and bank-holiday credits before launch.
- Re-check deployment routing and rollback settings when promoting the Worker version.
