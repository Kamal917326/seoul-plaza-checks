# Seoul Plaza Checks

A paperless food safety app prototype for a Korean, Chinese and Japanese grocery with a hot food counter. It replaces the paper sheets staff fill in by hand for hot food temperatures, delivery checks and date checks, and keeps every record time-stamped and named.

**Live demo:** [https://YOUR-USERNAME.github.io/seoul-plaza-checks/](https://kamal917326.github.io/seoul-plaza-checks/)

> This is a prototype with example data. Suppliers, barcodes, staff names and prices are made up. Records are saved only in the browser on the device you use.

## The problem

When I started working at the shop, all food safety records were on paper:

- Hot food on the counter (pork, beef, tofu, corn dogs and four kinds of chicken) is probed every 2 hours and written on a sheet.
- Deliveries are ticked off on paper against the delivery note.
- Best before and use-by dates are checked by walking the shelves.

Paper records get missed, are hard to read, and are hard to pull out quickly when an Environmental Health Officer inspects the shop.

## What the app does

### Hot food log
- 2-hourly rounds for every tray, with the current round, progress and time to the next round.
- Readings below 63°C (the legal hot-holding minimum in England) cannot be saved without a corrective action: reheated to 75°C with a re-check, sold within one 2-hour period, or discarded.
- Discarded trays go straight into the waste log.
- A grid of the whole day's readings.

### Delivery check-in
1. Pick the supplier and its usual order.
2. Scan or tick each item. Enter quantity received, probe temperature (chilled 8°C or below, frozen −15°C or colder) and the use-by or best before date.
3. Tick the arrival checks (packaging, van, pests, invoice) and photograph the delivery note.
4. Sign on screen and save.

Warm items and short-dated use-by items are rejected automatically. Short and missing items are flagged so the shop can claim credit. A supplier report shows who delivers warm or short most often over the last 30 days.

### Dates and waste
- Dates captured at delivery feed the tracker automatically. Stock already on the shelf can be added by hand.
- **Use by** is about safety, so items past it are blocked and must be removed from sale.
- **Best before** is about quality, so items past it can still be sold after a quality check.
- Reduce-to-clear and removal actions, with a waste log, monthly £ total and a 7-day chart.

### Today and inspection record
- One screen showing what needs attention now.
- A one-tap food safety record for the day (hot holding, deliveries, items removed) to show an inspector.

## Tech

A single `index.html` with plain HTML, CSS and JavaScript. No build step, no framework, no server. Data is stored in the browser with `localStorage`. Works on phones and supports light and dark mode.

## Run it

Open `index.html` in a browser, or serve the folder:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

## Roadmap

- Shared storage so all staff phones see the same records (SharePoint or Google Sheets backend).
- Staff sign-in with a PIN.
- Camera barcode scanning and Bluetooth probe input.
- Push reminders for each hot food round.
- PDF export of the daily record.
- Power BI dashboard for waste, supplier performance and check compliance.
- Hiring and onboarding: application form, e-signed contracts and right-to-work check records.

## Author

Harshvardhan Badgujar
