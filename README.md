# Census

A census board for a behavioral health program with PHP, IOP and OP levels of care. It replaces the mix of EMR screens and an Excel sheet with one place to see who is in the program, where they are in their plan of care, and who needs attention.

**This is a prototype.** It runs entirely in the browser, uses made-up sample clients, and saves changes only in the browser you are using. Do not enter real client information. Real use needs HIPAA-grade hosting, sign-in and access controls, audit logging, and a signed BAA with the hosting provider.

## What it does

- **Census.** One row per client, like the Excel sheet. Change a client's LOC or housing right in the row with a dropdown. When LOC changes, the app fills in the defaults automatically: the attendance schedule (PHP Mon–Fri, IOP Mon/Wed/Thu, OP Tue), the frequency, the next projected step-down date, and the discharge date. Every automatic change can be undone. Filter by LOC, sort by any column, or copy the census as CSV to paste into Excel.
- **Scheduled LOC changes.** Click a client's projected step-down date to open their scheduling card. Line up to 3 changes, each with a date, the new LOC, the session (day, evening or night) and the days they'll attend. On each date the client's LOC, session and schedule update automatically. In this prototype the update runs when the page is open or next opened; a hosted version would run it overnight on the server.
- **Sessions.** Each client attends day, evening or night sessions. The Week view groups each day by session, and you can drag a client between sessions.
- **Needs attention.** Overdue or upcoming step-downs, upcoming or overdue discharges, admissions due tomorrow, clients past their incoming commitment, and clients without a schedule.
- **Week.** Who is expected each day, with counts by level of care and how many live in LPD. Drag a name to another day or session to change that client's schedule.
- **Import.** Upload an Excel (.xlsx) or CSV file, or paste rows copied from Excel. Columns are matched by their headings, and you see a preview before anything is added.
- **Client details.** Click any client to edit name, LOC, housing (LPD or commuter), admission, step-down and DC dates, schedule, clinician, case manager, psych APN, referral source and incoming commitment. Each client keeps a history of moves.
- **Dates** are shown as mm/dd/yy.
- **Filters.** Search, filter by any staff member (with caseload counts), and filter LPD or commuters.

## Running it

Open `index.html` in a browser. There is nothing to install.

`app.html` is the source. After editing it, run `./build.sh` to regenerate `index.html`.

## Not in the prototype yet

- Kipu EMR integration
- Sign-in, roles, and a shared database so the whole team sees the same census
- Reports (census trends, length of stay by level of care, referral source outcomes)
