# Changelog

Documenting changes to the Sydney Dance Event Calendar.

---
<br>

## Update 2026-07-13

### Performance and display fixes

- **Skeleton loader:**
  - Replaced the plain loading state with a structured skeleton that mirrors the event list layout — each placeholder row shows a date column and text/tag blocks that pulse while data loads. Rows animate with a staggered delay for a more natural feel.

- **List view fixes:**
  - Fixed past events incorrectly appearing in the default list view: all-day events (such as multi-day battles) now correctly use their display end date rather than Google Calendar's exclusive end date when filtering.
  - Fixed the upcoming event highlight: the yellow indicator now marks the first event starting today or later, rather than any event that spans today.

- **Performance — localStorage caching:**
  - Added a 30-minute client-side cache so repeat visits render the event list instantly without waiting for the Apps Script response
  - Stale cache is refreshed silently in the background after expiry, so the page always shows without delay while staying up to date.

- **Performance — Tally form cache invalidation:**
  - Added a listener for Tally's form submission event: when anyone submits a new event, the local cache is immediately cleared and a fresh fetch fires after 4 seconds, so the new event appears in the list automatically without a manual reload.

- **Performance — load timing:**
  - Switched from window.onload to DOMContentLoaded so the data fetch begins as soon as the page structure is ready, rather than waiting for all images and external assets to finish loading.

- **Page load performance:**
  - Added client-side caching so repeat visits render the event list instantly, eliminating the 2–8 second Apps Script cold start that previously occurred on every page load and refresh.

- **Cache invalidation — form submissions:**
  - Added a listener for Tally's form submission event: when anyone submits a new event via the form, the cache is cleared immediately and a fresh fetch fires within a few seconds, so the new event appears without a manual reload.

- **Cache invalidation — direct Google Calendar additions:**
  - Added an Apps Script trigger that writes a timestamp to a dedicated sheet cell (AE1) whenever the calendar is updated (events created, edited, or deleted). The site checks this cell on every page load and re-fetches automatically if a change is detected, without needing to fetch the full event list first.
  - Note: Google Calendar triggers have an inherent delay of 1–5 minutes (occasionally up to 15) before firing. Direct calendar additions will appear on the next page refresh after that delay. Previously, changes appeared immediately on refresh since every load fetched fresh data — this is a deliberate trade-off for the faster load experience.
Fallback behaviour
If the sheet check fails for any reason, the cache falls back to a 30-minute TTL to ensure data does not become stale indefinitely. In normal operation this timer is bypassed by the sheet check and does not affect how quickly changes appear.
<br>
<br>

## Update 2026-04-20

### Submission update

• **Tally submission flow refined and stabilised:**
Updated the submission workflow around the embedded Tally popup so the main event submission path remains consistent while supporting the newer Tally-connected sheet and downstream calendar automation.

### Changes to script

• **Adjusted the Tally-connected Apps Script to better handle imported sheet values:**
Refined the Google Apps Script logic used for the Tally-populated Google Sheet so new rows are processed more reliably and event creation remains aligned with the current submission pipeline.

• **Improved date and time handling for calendar event creation:**
Updated the event creation logic to better control how submitted dates and times are interpreted when creating Google Calendar events, especially where imported values may not behave the same way as direct form inputs.

• **Added safer rebuild and retest support while troubleshooting event creation:**
Kept the row-based rebuild workflow in place so individual submissions can be reprocessed more easily during fixes, making it faster to verify changes without affecting the entire sheet.

### Refined event details

• ***Safer event description rendering on the website:***
Updated the event detail popup rendering so pasted content is handled more safely, while still preserving expected formatting such as line breaks and supported links.

• ***Link handling in event descriptions is more controlled:***
Refined how description content is displayed so plain text remains plain text, while supported explicit links can still render correctly in the event detail popup.

• ***Continued troubleshooting for Tally-related timezone behaviour:***
Investigated the time shift affecting some Tally submissions, where submitted local times appear to be transformed during the integration flow before calendar creation. Further refinement focused on matching the calendar output more closely to the locally displayed values in the sheet.




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
- **Invalid End Date Guardrail:**
Updated the Google Apps Script to safely handle cases where the submitted end date is earlier than the event date. Instead of failing to create the event, the script now ignores the invalid end date and creates the event as a single-day entry.

- **Improved All-Day Event Handling:**
Adjusted the all-day event creation logic so that only valid end dates are used. This helps prevent incorrect date ranges from blocking event creation in Google Calendar.

- **More Resilient Submission Parsing:**
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
