# Census

A census board for a behavioral health program with PHP, IOP and OP levels of care. It replaces the mix of EMR screens and an Excel sheet with one place to see who is in the program, where they are in their plan of care, and who needs attention.

**This is a prototype.** It runs entirely in the browser, uses made-up sample clients, and saves changes only in the browser you are using. Do not enter real client information. Real use needs HIPAA-grade hosting, sign-in and access controls, audit logging, and a signed BAA with the hosting provider.

## What it does

- **Board.** One column per level of care: Pending, PHP, IOP, OP and Discharged. Drag a client card to another column to admit, step down, step up or discharge them. On a move the app fills in the defaults automatically: the attendance schedule (PHP Mon–Fri, IOP Mon/Wed/Thu, OP Tue), the frequency, the next projected step-down date, and the discharge date. Every automatic change can be undone from the message that appears.
- **Needs attention.** Overdue or upcoming step-downs, upcoming or overdue discharges, admissions due tomorrow, clients past their incoming commitment, and clients without a schedule.
- **Week.** Who is expected each day, with counts by level of care and how many live in LPD. Drag a name from one day to another to change that client's schedule.
- **Spreadsheet.** All fields in a sortable table, plus a button that copies the census as CSV to paste into Excel.
- **Import.** Upload an Excel (.xlsx) or CSV file, or paste rows copied from Excel. Columns are matched by their headings, and you see a preview before anything is added.
- **Client details.** Click any client to edit name, LOC, housing (LPD or commuter), admission, step-down and DC dates, schedule, clinician, case manager, psych APN, referral source and incoming commitment. Each client keeps a history of moves.
- **Filters.** Search, filter by any staff member (with caseload counts), and filter LPD or commuters.

## Running it

Open `index.html` in a browser. There is nothing to install.

`app.html` is the source. After editing it, run `./build.sh` to regenerate `index.html`.

## Not in the prototype yet

- Kipu EMR integration
- Sign-in, roles, and a shared database so the whole team sees the same census
- Reports (census trends, length of stay by level of care, referral source outcomes)
