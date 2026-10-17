# PayrollPro

**English** | [العربية](README.ar.md)

[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)

A single-file, browser-based HR and payroll management system for small and medium businesses. No server, no installation — open the HTML file and start working. All data is stored locally in the browser.

**▶ [Try the live demo](https://alfaisalgassim.github.io/SalaryCal/)** — no signup, nothing is uploaded; all data stays in your browser.

## ⚠️ Important: Your Data

**Please read this before you start using the app for real payroll.**

Everything you enter is saved **only in your browser's local storage, on the device you are using.** There is no account, no server, and no cloud sync. Nothing is ever uploaded anywhere — which is good for privacy, since nobody else can see your data, but it also means:

**Your data will be gone if you:**

- Clear your browser history, cookies, or site data
- Use private / incognito browsing
- Open the app on a different browser or a different device
- Uninstall or reset your browser

**You are solely responsible for backing up your own data.** Use the **Export** button in the sidebar regularly to download a backup file, and **Import** to restore it. The app will remind you on the dashboard whenever you have changes that have not been backed up.

If your browser blocks storage entirely (common in private mode), the app will warn you that your work will not be saved — export immediately if you see that message.

## Features

### Employee Management
- Add, edit, and deactivate employees
- Per-employee fields: name, ID, department, position, base salary, housing/transport/other allowances, GOSI employee & employer percentages, join date, OT formula assignment, commission category assignments
- Employees with at least one paid payroll record cannot be deleted — they can only be set to Inactive
- Import employees from Excel (.xlsx) using a downloadable template; export the full employee list to Excel

### Payroll Processing
- Process monthly payroll for all active employees in one click
- Auto-calculates: prorated base salary, allowances, GOSI deduction, absent-day deductions, late-minute deductions, additional deductions, OT pay, commission pay, gross, and net
- **Two-tier payment locking**
  - **Base salary lock**: once base is marked Paid, salary/allowances/GOSI/attendance values are frozen permanently
  - **OT & Commission lock**: can only be marked Paid after base salary is paid; locks OT and commission values independently
  - Once both tiers are paid, the record is fully locked forever — no changes can affect it
- Any change to an employee (salary, allowances, GOSI) or attendance automatically syncs to all unpaid payroll months
- Payroll snapshot: stores the salary, allowances, GOSI %, and OT formula in the record at time of processing, so paid records always display the values that were in effect — not current values
- Filter payroll by department and payment status
- Hover tooltips on every payroll column showing the full breakdown (daily rate, proration, individual allowances, deduction sources, etc.)

### Attendance
- Enter work days, absent days, late minutes, additional earnings, and extra deductions per employee per month
- Saving attendance immediately syncs changes to unpaid payroll records for that month

### OT & Commission
- Custom OT formula builder with presets and a live formula tester
  - Variables available: `baseSalary`, `hourlyRate`, `dailyRate`, `otHours`, `workDays`, `otMultiplier`
  - Snapshot of the formula and multiplier is stored in each payroll record at time of calculation
- Commission categories: flat-rate or percentage-of-sales, assignable per employee
- Enter monthly sales values per employee per category
- Hover tooltips on OT and commission columns showing the formula used and per-category breakdown
- OT & Commission approval PDF (detailed, suitable for manager sign-off)

### Payslips
- View and print individual payslips for any employee and month
- Payslip reads from the stored snapshot — always shows the numbers as they were when processed

### Reports
- Monthly payroll summary: total gross, net, deductions, OT, commission, department breakdown
- Historical view across all processed months

### Exports
| Export | Format | Notes |
|---|---|---|
| Full data backup | JSON | Exports everything; used for Import |
| Employee list | Excel (.xlsx) | All employee fields |
| Monthly payroll | Excel (.xlsx) | Grouped by department, color-coded, full breakdown columns |
| Payroll approval report | PDF | Grouped by department, signature lines for manager |
| OT & Commission report | PDF | Detailed per-category breakdown, approval format |

### Data Management
- **Export**: download a full JSON backup of all data
- **Import**: restore from a previously exported JSON backup
- **Clear All Data**: requires typing `CLEAR` to confirm; automatically exports a dated backup before wiping, ensuring data is never lost without a copy

## Language Support
- English and Arabic (right-to-left)
- Toggle between languages using the button in the sidebar footer

## Technical Notes
- **Single file**: `index.html` — no build step, no dependencies to install
- **Storage**: `localStorage` key `payrollpro_v2`
- **Excel**: [SheetJS](https://sheetjs.com/) (xlsx 0.18.5, loaded from CDN) — requires internet connection for Excel import/export
- **No server required**: runs entirely in the browser; all computation is client-side

## Getting Started

Either **[open the live demo](https://alfaisalgassim.github.io/SalaryCal/)**, or download `index.html` and open it locally — both work identically and store data only in your browser.

1. Open the app in any modern browser (Chrome, Edge, Firefox, Safari)
2. Go to **Employees** and add your staff, or import from the Excel template
3. Go to **Settings → OT Formula** to configure overtime calculation rules
4. Go to **Settings → Comm. Categories** to set up commission categories
5. Each month: enter attendance, enter commission sales, then process payroll
6. Mark base salary paid when approved; mark OT & Commission paid after base is settled
7. Use **Export** regularly to back up your data

## Payment Locking Rules

```
Base unpaid  → all changes (employee, attendance, OT, commission) reflect on payroll
Base paid    → only OT and commission can still change; salary/attendance/GOSI are locked
Both paid    → record is fully locked; no changes affect it
```

OT & Commission cannot be marked paid unless base salary is already paid for that month.

## License

Copyright © 2026 **Alfaisal Gassim**

This program is free software: you can redistribute it and/or modify it under the terms of the [GNU General Public License v3.0](LICENSE) as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

In practical terms:

- ✅ You may use, study, modify, and share it — including commercially
- ⚠️ If you distribute a modified version, it must also be released under GPL-3.0 with its source available
- ⚠️ The copyright notice and license must be preserved in all copies
- ❌ It comes with **no warranty** — see sections 15 and 16 of the license

The copyright holder retains full ownership. If you need to use this software under terms other than the GPL (for example, inside a closed-source commercial product), contact the author to discuss a separate commercial license.

## Disclaimer

This software is provided **free of charge and "as is"**, without warranty of any kind, express or implied — see sections 15 and 16 of the [GNU GPL v3.0](LICENSE).

To be explicit about what that means in practice:

- **The author is not responsible for any loss of data**, however it occurs. Your data is stored in your own browser and backing it up is your responsibility.
- **The author is not responsible for the accuracy of any figure the app calculates.** Always verify payroll, overtime, commission, and GOSI amounts against your own records before paying anyone.
- **The author is not responsible for any decision made using this software**, or for any financial, legal, tax, or regulatory consequence arising from its use.
- **You are responsible for compliance.** Statutory rates and rules change — GOSI percentages in particular. Confirm the current rates and your own obligations with a qualified accountant or the relevant authority. The defaults in this app are starting values, not advice.

This tool is a calculator and record-keeper. It is not accounting, legal, or tax advice.

## Acknowledgements

Excel import/export is powered by [SheetJS](https://sheetjs.com/) (xlsx 0.18.5), licensed under Apache-2.0 and loaded from CDN rather than bundled. Apache-2.0 is compatible with GPL-3.0.
