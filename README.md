# Performance Tracker

Turns a flat ticketing export into a live, filterable read on how a multi-market support team is actually performing — who is on pace, which operation is lagging, and how the month is trending — replacing the spreadsheet someone used to rebuild by hand every morning.

**[Live demo](https://sebastianvalenza.github.io/performance-tracker/)** · runs instantly on synthetic data, or drop in your own ticketing export.

---

## The problem it solves

Performance for a large multi-market support team lived in a manually maintained spreadsheet: someone exported the day's ticket data, pasted it into tabs, and rebuilt the same charts by hand every morning. It was slow, error-prone, and gave no live view — by the time you could see who was behind or which operation was dragging, the month was already gone.

Performance Tracker ingests the same export and turns it into a dashboard that answers the daily question — *is the team on pace?* — the moment it loads, with the at-risk operation visible before you read a second tab.

## What's inside

- **Overview** — team KPIs, a gamified tier board per operation (a "floor" model: an operation only turns fully gold when *every* agent clears the gold threshold), the daily points trend, and a sortable, groupable agent leaderboard. The floor model is the honest one — a single lagging agent keeps the operation off gold, so the board shows the weakest link instead of hiding it behind an average.
- **Projection** — linear month-to-date extrapolation of each agent's points to end of month, against the gold target, so a shortfall is visible in week two rather than confirmed on the last day.
- **Individual** — a full per-agent profile: operation, markets, shift rotation, tier progress and daily trend.
- **Compare** — normalized radar comparison of up to four agents across points, volume, SLA and QA, so a high-volume agent with weak quality is distinguishable from a balanced one.
- **History** — weekly and monthly trends for volume and quality across the full period.

Points are computed as `public comments × 1 + internal comments × 0.25`. Agents earn 🥉 bronze (800), 🥈 silver (1,200) and 🥇 gold (1,600) tiers; operation and team tiers inherit the lowest agent tier beneath them.

## Use your own data

The tracker ships with a deterministic synthetic dataset (48 agents, 4 operations, 10 markets, 90 days) so the live demo works with zero setup. The **column-mapping CSV uploader** accepts an arbitrary ticketing export (Zendesk or otherwise) — it auto-detects agent, date and metric columns, falls back to manual mapping and graceful error states when a file isn't in the expected shape, and hides optional metrics (SLA, QA, resolution time) automatically when they're absent. Nothing leaves the browser.

## Part of an operations ecosystem

Performance Tracker is one of five control surfaces for a single multi-hub operation, built to follow one decision down the whole chain — *from the shift being covered to the cash being collected*:

| Stage | Tool | The question it answers |
|---|---|---|
| Capacity | [Shift Planner](https://github.com/Sebastianvalenza/shift-planner) | Is the shift covered? |
| Workflow | [Ticket Triage](https://github.com/Sebastianvalenza/ticket-triage) | Who takes what, without collisions? |
| **Productivity** | **Performance Tracker** *(this tool)* | **Is the team performing?** |
| Revenue | [Revenue Cockpit](https://github.com/Sebastianvalenza/revenue-cockpit) | Are we going to make the number? |
| Cash | [AR Cockpit](https://github.com/Sebastianvalenza/ar-cockpit) | Did the money actually land? |

All five run on the same four hubs (Madrid 🇪🇸 · Berlin 🇩🇪 · Warsaw 🇵🇱 · Dublin 🇮🇪), the same ten markets, the same seed and the same visual system — one company seen from five functions. The hubs are the same operating centres throughout: the Berlin that books deals in Revenue Cockpit is the Berlin whose support floor this tool tracks. Same world, different layer of the business.

## Stack

Single-file `index.html` — no backend, no build step, no framework — deployable to GitHub Pages as-is. Vanilla JavaScript for the data model and tier logic, Chart.js for the line, bar and radar visualizations, PapaParse for CSV import and column detection. Synthetic data is generated from a fixed seed (`mulberry32`) so the dataset is identical on every load. Dark and light themes, persisted locally; the current view is shareable via URL. Fully client-side — no credentials, no data leaving the page.

## Notes

All data is synthetic. No real agents, tickets or company names appear anywhere in this repository. Names, markets and figures are randomly generated for demonstration.

---

*[linkedin.com/in/sebastianvalenza](https://linkedin.com/in/sebastianvalenza)*
