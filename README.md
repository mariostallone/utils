# utils

A collection of small, self-contained utilities. Each util is a single HTML file with no build step — open it in a browser. Most work fully offline; House Builder loads three.js, jsPDF and fonts from a CDN, so it needs a network connection.

## Utilities

| Util | Path | Description |
| --- | --- | --- |
| Vacation Planner | [`vacation_planner/index.html`](vacation_planner/index.html) | Plan PTO, work-from-abroad (WFA) and paternal leave on a yearly calendar. |
| Stay Planner | [`stay_planner/index.html`](stay_planner/index.html) | Mark where you'll stay each day and keep time at two homes balanced. |
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
- **Preview & share:** a clean view of the calendar for screenshots and emails. Choose a subset of dates to show, and turn the carryover highlight on or off. Then copy the view as an image to paste into an email, download it as a PNG, or print / save it as a PDF. Images always use the light colour scheme and are sized to the months shown.
- **Export / print:** save the plan as JSON or print it. Printing also respects the carryover-highlight setting.
- **Local storage:** your plan is saved in the browser's `localStorage`; nothing leaves your machine. Light and dark colour schemes are supported.

### Usage

Open `vacation_planner/index.html` directly in a browser, or serve the repo statically:

```sh
python3 -m http.server 8000
# then visit http://localhost:8000/vacation_planner/
```

Note that data is stored per browser and per origin, so a plan created at a `file://` URL won't appear when served from `localhost`.

## Stay Planner

A calendar for planning where you'll be on each day of a visit, and for keeping the time split fairly between two homes (for example, your place and your partner's).

- **Places with emoji:** starts with two places, BLR 🏙️ (yours) and TUT 🌴 (your partner's). Add more places, such as trips, each with its own emoji (pick one or type any emoji) and colour. Click a place to edit or delete it.
- **Whose place:** each place belongs to you, your partner, or neither (a trip). Set both names under *Who's who*.
- **Mark days:** click a day, or drag or Shift-click to select a range, then pick a place. Number keys `1`–`9` pick a place, `N` creates a new place for the selection, `F` marks the days as flights, and `C` clears them.
- **Flights:** mark travel days as ✈️ Flight. They show on the calendar and in the stays list, but don't count toward any place's total or the balance, and aren't counted as unplanned.
- **Counts and balance:** day counts per place, plus a balance between the two of you that shows who is ahead, by how many days, and what it takes to finish even with the unplanned days left. Counts cover either the dates in view (set the range to your trip) or all time.
- **Stays:** each run of days at one place is listed; click one to select it.
- **Undo**, an editable title, JSON export and import, printing, `localStorage` saving and light and dark colour schemes, as in Vacation Planner.

## Live site and PR previews

The [`Pages` workflow](.github/workflows/pages.yml) publishes the repo with GitHub Pages:

- `main` is published at `https://mariostallone.github.io/utils/`.
- Every pull request gets its own preview at `https://mariostallone.github.io/utils/pr-preview/pr-<number>/`. The preview updates on each push, a comment on the PR links to it, and it's removed when the PR is closed or merged.

One-time setup: after this workflow is merged and has run on `main` (which fills the `gh-pages` branch with the site), go to **Settings → Pages → Build and deployment** and change the branch from `main` to `gh-pages`, folder `/ (root)`. Don't switch earlier: until `main` has been deployed, `gh-pages` holds only previews and the site root would be empty.

Data is stored per origin, so plans saved on the live site, on a preview or in a local file are kept separately.

## Adding a util

Create a new directory containing a self-contained `index.html`, then add it to the table above and to the `UTILS` list in the root `index.html`.
