# US → Amazon.ae Fulfilment Tracker

A live operations dashboard for tracking US-sourced orders sold on Amazon.ae,
from purchase through procurement, Dubai transit, and last-mile delivery.

## What it does

Reads order data live from a Google Sheet and shows:

- **KPI cards** — total orders, delivered, open, danger (past ship deadline),
  cancelled, and not-procured counts, plus delivery rate
- **Status breakdown** — distribution across all fulfilment stages
- **Order state** — Closed / Open / Danger split
- **Order table** — searchable by order ID, SKU, product, AWB, or ASIN;
  sortable columns; filter by state; export the filtered view to CSV
- **Date filters** — switch between order date and latest ship date,
  with 7d / 30d / 90d / all-time quick ranges

Data refreshes automatically every 5 minutes and on manual refresh.
Dark and light themes included.

## How it works

The dashboard reads the Google Sheet through its public CSV export endpoint,
so no backend or API key is needed. Hosted as a single static `index.html`
on GitHub Pages.

## Order state logic

- **Closed** — delivered to customer, or buyer cancelled
- **Danger** — not closed and past the latest ship date
- **Open** — not closed and still within the ship deadline
