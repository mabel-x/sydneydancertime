# Changelog

All notable changes to the Sydney Dance Event Calendar.

---

## Update VER - 2025-02-09

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
