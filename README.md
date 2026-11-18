# Census

A census board for a behavioral health program with partial care, IOP and OP levels of care. It replaces the mix of EMR screens and an Excel sheet with one place to see who is in the program, where they are in their plan of care, and who needs attention.

**This is a prototype.** It runs entirely in the browser, uses made-up sample clients, and saves changes only in the browser you are using. Do not enter real client information. Real use needs HIPAA-grade hosting, sign-in and access controls, audit logging, and a signed BAA with the hosting provider.

## What it does

- **Census.** The Active census box at the top shows the total with PC, IOP, EIOP and OP sub-counts. The Residence box splits the active census into LPD and commuters. The Pending box counts today only: admissions scheduled for today, and discharges due today (projected DC date today, or a date of discharge of today). One row per client, like the Excel sheet. LOC includes the attendance frequency: PC6, PC5, IOP6, IOP5, IOP4, IOP3, EIOP (evening IOP) and OP, plus Pending. Discharge is not a LOC: entering a date of discharge marks the client discharged, and they keep the LOC they left from. Change a client's LOC or housing right in the row with a dropdown, and their attendance days update to match. Click the Schedule column to edit days and times. Every change can be undone. Filter by LOC group, sort by any column, or copy the census as CSV to paste into Excel.
- **Scheduled LOC changes.** Click a client's projected step-down date to open their scheduling card. Line up to 3 changes, each with a date, the new LOC, and the days and times they'll attend. On each date the client's LOC and schedule update automatically. In this prototype the update runs when the page is open or next opened; a hosted version would run it overnight on the server.
- **Days and times.** Each attended day has a time block: daytime (9–12), afternoon (12:30–3:30) or evening (6–9pm) for IOP and OP, and all day (9–3:30) for PC. Evening groups (6–9pm) run only Mon, Tue and Thu nights. EIOP defaults to those evenings, but daytime and afternoon IOP blocks can be chosen too. IOP4, IOP3 and OP days vary per client. The census flags a client whose number of days doesn't match their LOC.
- **Projected DC from LOS.** When a client's incoming commitment (length of stay in days) or admission date is entered, the projected DC date is set to admission + LOS, counting the admission date as day 1. A date that lands on Saturday moves back to Friday; one on Sunday moves forward to Monday. It can still be edited by hand.
- **Discharge.** Each client's details card has a date of discharge. Entering one discharges the client on that date (their row stays, dimmed and marked discharged, under the LOC they left from, until removed from the census), and then asks for the discharge type (sample list for now), whether they completed their commitment, and whether they stayed longer than it. A discharge missing any of these shows under Needs attention.
- **Archive.** Removing a client from the census archives them instead of deleting them. Clients with a date of discharge go to **Discharges**; clients still Pending with no discharge date go to **Incomplete admissions** (likely failed admits). Discharges show name, admission date, discharge date, discharge type, incoming commitment, completed commitment? and longer than commitment?. Incomplete admissions show name, admission date, incoming commitment and an editable note about what happened (which can also be entered when archiving). Each list can be copied as CSV, and any record can be restored. Click a name to see the archived record and its full history. An active client needs a date of discharge before they can be removed.
- **Needs attention.** A red bell with a count, to the right of the Settings gear, on every view. It lists only things someone needs to fix: missing profile info (clinician, case manager and psych APN (chosen from the staff lists in Settings), referral source, incoming commitment, housing, projected DC date), missing discharge details, admit dates that passed while still Pending, overdue DCs, clients past their incoming commitment, and schedules that are missing or don't match the LOC. Click a name to open the client.
- **Week overview.** A button next to Needs attention opens the calendar week (Mon–Sat; on Sunday, the coming week): admissions, LOC changes and discharges for each day, with totals. Its badge counts what is still ahead this week. Click a name to open the client.
- **Week.** Click the Expected today box at the top to jump to today in the 3-day view. Each day's heading (date, expected count, LOC counts and color bar) stays in place: on a computer the page itself doesn't scroll on the Week view, and everything below the day headings scrolls as one block. Switch between a 3-day view (the next three program days from today, Sundays skipped) and a full week (Mon–Sat), and step back or forward with the arrows. Who is expected each day, with counts by level of care and how many live in LPD. Each day is split into all day, daytime, afternoon and evening. Drag a name to another day or time block to change that client's schedule.
- **Settings.** The gear next to Archive opens Settings: edit the clinician, case manager and psych APN lists that fill the dropdowns on each client's card (renaming updates every assigned client), and import a spreadsheet.
- **Import** (in Settings). Upload an Excel (.xlsx) or CSV file, or paste rows copied from Excel. Columns are matched by their headings, and you see a preview before anything is added.
- **Client details.** Click any client to edit name, LOC, housing (LPD or commuter), admission and DC dates, scheduled step-downs, attendance days, clinician, case manager, psych APN, referral source and incoming commitment. Each client keeps a history of moves.
- **Dates** are shown as mm/dd/yy.
- **Filters.** Search, filter by any staff member (with caseload counts), and filter LPD or commuters.

## Running it

Open `index.html` in a browser. There is nothing to install.

`app.html` is the source. After editing it, run `./build.sh` to regenerate `index.html`.

## Not in the prototype yet

- Kipu EMR integration
- Sign-in, roles, and a shared database so the whole team sees the same census
- Reports (census trends, length of stay by level of care, referral source outcomes)
