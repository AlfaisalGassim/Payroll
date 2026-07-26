# PayrollPro

**English** | [العربية](README.ar.md)

A single-file, browser-based HR and payroll management system for small and medium businesses. No server, no installation — open the HTML file and start working. All data is stored locally in the browser.

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
- **Single file**: `PayrollPro.html` — no build step, no dependencies to install
- **Storage**: `localStorage` key `payrollpro_v2`
- **Excel**: [SheetJS](https://sheetjs.com/) (xlsx 0.18.5, loaded from CDN) — requires internet connection for Excel import/export
- **No server required**: runs entirely in the browser; all computation is client-side

## Getting Started

1. Open `PayrollPro.html` in any modern browser (Chrome, Edge, Firefox, Safari)
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

## Copyright

© 2026 Alfaisal Gassim. All rights reserved.
