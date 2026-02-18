# Changelog

Documenting changes to the Sydney Dance Event Calendar.

---

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
