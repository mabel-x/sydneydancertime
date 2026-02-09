# Sydney Dance Event Calendar


A web-based event calendar for Sydney's street dance community, built on Blogspot with custom JavaScript and CSS.

**Live Site**: [sydneydancertime.blogspot.com](https://sydneydancertime.blogspot.com)

---

## Overview

This calendar aggregates dance events across Sydney, providing dual-view modes (list and calendar), advanced filtering by event type and dance style, and automatic event categorization from title patterns.

### Features

- **Dual View Modes**: Switch between list and calendar grid layouts
- **Smart Filtering**: Filter by event type (Battles, Workshops, Jams, etc.) and dance style (Breaking, House, Popping, etc.)
- **Event Parsing**: Automatically extracts dance styles and event categories from titles
- **Automated Submissions**: Google Form submissions auto-populate via Apps Script
- **Date Navigation**: Custom date picker with month/year selection
- **Modal Details**: Click any event for full details and Google Calendar integration
- **Responsive**: Mobile-optimized layout

---

## Data Pipeline

The calendar uses an automated event management system:

**Submission → Processing → Display**

1. Community members submit events via [Google Form](https://forms.gle/ZTrkhMcMasnJ5Veq6)
2. Google Apps Script validates and adds approved submissions to Google Calendar
3. Calendar data is fetched via Apps Script API endpoint
4. Frontend processes and displays events with automatic categorization

This eliminates manual entry and keeps the calendar synchronized with the source calendar.

---

## Technical Stack

- **Platform**: Blogspot (custom XML template)
- **Frontend**: Vanilla JavaScript (ES6+), CSS Grid/Flexbox
- **Data Pipeline**: Google Forms → Google Apps Script → Google Calendar → Apps Script API
- **Development**: AI-assisted coding with [manus.im](https://manus.im)
- **No Runtime Dependencies**: Pure JavaScript, no frameworks or libraries


---

## Updates

**Latest Version**: 2.0.0 (February 2025)

See [CHANGELOG.md](CHANGELOG.md) for complete version history.


---

## Event Submission

Community members can submit events via [this form](https://forms.gle/ZTrkhMcMasnJ5Veq6).


---

## Contact

For questions or issues, use the [contact form](https://forms.gle/bfdvKiRM1rzccpq28).


<br>
<br>
<br>
<p align="right"><sub>built with manus by makes, powered with coffee &#9749;&#65039; </sub></p>
