# utils

A collection of small, self-contained utilities. Each util is a single HTML file with no build step — open it in a browser. Most work fully offline; House Builder loads three.js, jsPDF and fonts from a CDN, so it needs a network connection.

## Utilities

| Util | Path | Description |
| --- | --- | --- |
| Vacation Planner | [`vacation_planner/index.html`](vacation_planner/index.html) | Plan PTO, work-from-abroad (WFA) and paternal leave on a yearly calendar. |
| House Builder | [`home_builder/index.html`](home_builder/index.html) | Sketch floor plans, furnish rooms and view the house in 3D. |

The root [`index.html`](index.html) is a browsable landing page that links to each util.

## Vacation Planner

A yearly calendar for planning time off against your allowance.

- **Day types:** PTO, work from abroad (WFA), paternal leave, and public holidays, each colour-coded. Weekends are shaded.
- **Allowances:** set a yearly allowance per type and track what's used and what's left with progress meters. PTO counts working days only.
- **PTO rollover:** unused PTO can carry over into the next year until a configurable deadline (default 31 March). Carried-over days are used first, and anything left after the deadline is forfeited.
- **Public holidays:** built-in holiday calendars for Germany (nationwide or per federal state), the United Kingdom (England & Wales) and the United States. You can also add custom holidays.
- **Suggest days:** get suggestions for which days to take off, with a preview you can accept or exit.
- **Undo** for edits, and an editable plan title.
- **Export / print:** save the plan as JSON or print it.
- **Local storage:** your plan is saved in the browser's `localStorage`; nothing leaves your machine. Light and dark colour schemes are supported.

### Usage

Open `vacation_planner/index.html` directly in a browser, or serve the repo statically:

```sh
python3 -m http.server 8000
# then visit http://localhost:8000/vacation_planner/
```

Note that data is stored per browser and per origin, so a plan created at a `file://` URL won't appear when served from `localhost`.

## Adding a util

Create a new directory containing a self-contained `index.html`, then add it to the table above and to the `UTILS` list in the root `index.html`.
