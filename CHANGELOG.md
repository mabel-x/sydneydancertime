# Changelog

Documenting changes to the Sydney Dance Event Calendar.

---
<br>
<br>

## Update 2026-04-18

### Submission update
- **Tally popup replaces Google Forms**:
Updated the site’s event submission links to open the new Tally popup form instead of the previous Google Forms workflow. This applies to the main submission entry points so event submissions now happen through the embedded Tally experience.

### Changes to script
- **Rebuilt automation for the new Tally-connected sheet**:
Reworked the Google Apps Script to process submissions from the new Google Sheet populated by Tally. Because Tally writes rows directly into Sheets, the old form-submit trigger was replaced with a time-driven process that checks for new rows every minute.

- **Added row tracking and rebuild support**:
Added helper columns for `Calendar status`, `Calendar error`, and `Calendar created at` so each submission can be tracked more clearly, plus a `rebuildRow(rowNumber)` utility for reprocessing individual entries when needed.

- **Improved header matching reliability**:
Updated the script to use normalized header matching so minor spacing differences in the sheet do not break field lookups such as event description and other submission details.

- **Location now carries through to calendar events**:
Added support for the Tally `Event location` field so submitted locations are included when calendar events are created.

- **Better multi-day event handling**:
Fixed event creation logic so multi-day events use the submitted end date correctly, including cases where a start time is provided but no end time is entered.

- **Specificity tags now use short codes in titles**:
Added abbreviation handling for specificity labels so titles stay compact in calendar views. For example, Female, Invitational, Kids, Rookie, Random, and Under 18 now appear as `F`, `I`, `K`, `R`, `RD`, and `U18` in event titles, while the full wording remains in the event details.

### Refined event details
- **Multi-day end date now shows in the event detail popup**:
Updated the website popup so multi-day events display the full visible date range in the detail view instead of only the first day.

- **Submission detail flow is clearer**:
Refined how submitted event details carry through from form submission to calendar output, especially for end date and location fields, so event information is more complete and easier to verify.

<br>
<br>

## Update 2026-04-14

### Changes to script
- **Invalid End Date Guardrail:**:
Updated the Google Apps Script to safely handle cases where the submitted end date is earlier than the event date. Instead of failing to create the event, the script now ignores the invalid end date and creates the event as a single-day entry.

- **Improved All-Day Event Handling:**:
Adjusted the all-day event creation logic so that only valid end dates are used. This helps prevent incorrect date ranges from blocking event creation in Google Calendar.

- **More Resilient Submission Parsing:**:
Improved the automation so that minor form input mistakes do not stop otherwise valid event submissions from being processed.



<br>
<br>

## Update 2026-02-18
### Changes to script 

- **Flexible Style Matching**:
Updated the style detection logic to use partial matching instead of exact matching. This ensures that variations like "All styles/Open style" are correctly identified as "All styles" (AS).

- **Multiple Tag Support**:
Improved the logic to ensure that if multiple styles are mentioned in a single entry (e.g., "All styles/Open style, Experimental"), all corresponding tags (e.g., AS, EXP) are included in the event title.

- **Robust Date & Time Parsing:**
Implemented a custom Regular Expression parser to reliably handle standalone time strings (e.g., "10:00:00 AM") and strip non-date prefixes like "TBA" or "TBC".

<br>
<br>

## Update VER: 2026-02-10

### Changes

- **New communuity links layout**:
Replaced the list-style with row-based layout and icons

- **Updated links**:
  - Burn City Street Dance Calendar: linked to Blogspot URL.
   - Instagram Handles: Added a row of handles (@sydcitywaack, @ballroomaustralia, @ausbreaking, @sydneyhouseheads, @sydneypopping, @qldfreestyleinfo) each linked to their respective Instagram profiles.

<br>
<br>

## Update VER: 2026-02-09

### Improved
- **Enhanced event parsing logic**: Better detection of dance style modifiers
  - Events now properly parse prefixes like Rookie, Women, Kids, Under 18
  - Example: `R.WA` (Rookie Waacking) now displays both "Rookie Waacking" and "Waacking" tags
  - Supports multiple formats: R./Rookie, F./Female/Women, K./Kids, U18/Under 18, I./Invitational, RD/Random
  - Handles various bracket styles: `(BB)`, `[HH]`, `(BB & PP)`
  - Improved exclusion logic to prevent false positives (e.g., "Opera House" doesn't match "House" style)

### Fixed
- Style detection now works with both abbreviated and full-word formats
- Combined prefix + style tags now display correctly (e.g., "Rookie Popping" shows both tags)

---

## Credits

**Builder**: mabes with [manus.im](https://manus.im)  
**Community Contributors**: Event submitters via [Google Form](https://forms.gle/ZTrkhMcMasnJ5Veq6)

---

**View Live**: [sydneydancertime.blogspot.com](https://sydneydancertime.blogspot.com)  
**Report Issues**: [Contact Form](https://forms.gle/bfdvKiRM1rzccpq28)
