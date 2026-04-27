# PPT Addams Family Casting Conflict Tracker

## Project overview
This is a single-page web app for tracking auditioner conflicts for **The Addams Family** youth summer musical production at **Peoria Players Theatre (PPT)** in Peoria, IL. It is co-directed by Jace and his sister Kena.

## Production details
- **Show:** The Addams Family (youth summer production)
- **Opens:** August 5, 2026
- **Closes:** August 9, 2026
- **Cast announced by:** May 27, 2026
- **Rehearsal window:** May 25 – August 9, 2026
- **Rehearsal schedule:** Monday–Friday, 6:00pm–9:00pm (weekends are NOT rehearsal days)

## Tech stack
- Single HTML file (`index.html`) — no build process, no dependencies, no backend
- Fetches live audition data from a Google Sheet on page load
- Hosted on Netlify via GitHub auto-deploy
- Gothic/Addams Family dark theme with UnifrakturMaguntia + Crimson Text fonts from Google Fonts

## Data source
- **Google Sheet ID:** `1qInBL2YVfpI_opYZ6-woEhp0k8yorfmV3i4J04CN7wY`
- **CSV export URL:** `https://docs.google.com/spreadsheets/d/1qInBL2YVfpI_opYZ6-woEhp0k8yorfmV3i4J04CN7wY/export?format=csv`
- The sheet is the raw Google Form responses from auditioners — it must remain set to "Anyone with the link can view"
- Data is deduplicated by email address (latest submission wins)

## Deployment
- **GitHub repo:** `github.com/jmoe36/AddamsFamilyCasting` (public)
- **Netlify:** auto-deploys on every push to `main` branch
- **Live URL:** the Netlify-assigned URL (addamsfampptconflics.netlify.app or similar)
- No build command or publish directory needed — Netlify serves the repo root directly

## How the app works
1. On load, fetches the Google Sheet as CSV
2. Parses each row — one row per auditioner
3. Deduplicates by email (latest submission kept)
4. Classifies each person's conflict text into: `none`, `minor`, `major`, or `tbd`
5. Extracts specific conflict dates using regex date parsing
6. Renders a conflict table (desktop) + card layout (mobile) and a calendar view

## Conflict classification logic
- **none** — explicitly no conflicts, or conflicts that don't affect Mon–Fri 6–9pm (weekends only, daytime only, before cast period)
- **tbd** — vague responses: "work (flexible)", "not sure yet", "TBD", other shows with unconfirmed dates
- **major** — multi-day ranges, week-long trips, anything with a date span
- **minor** — 1–2 isolated specific dates

## Roles in the show
Gomez Addams, Morticia Addams, Wednesday Addams, Puggsley Addams, Uncle Fester, Grandmama, Lurch, Ancestor(s), Lucas Beineke, Alice Beineke, Mal Beineke, Any Role

## Planned features (not yet built)
- Rehearsal miss count per person — once the rehearsal schedule is locked in, calculate how many specific rehearsal dates each auditioner would miss based on their conflict dates
- Role-focused view — flip the perspective to show all candidates per role sorted by conflict level
- Casting status tracker — mark people as Interested / Auditioned / Callback / Cast / Passed

## Files in this repo
- `index.html` — the entire app (all HTML, CSS, JS in one file)
- `CLAUDE.md` — this file

## Notes
- The Google Form is still open and accepting responses through late May, so the data changes frequently
- Signup forms were built using SignUpGenius + Google Forms hybrid
- Jace also runs sound for PPT productions and is Co-Sound Chair — audio/sound questions may come up in context
- 3Six Audio is Jace's separate boutique audio hardware side project (not related to this repo)
