# Seoul Plaza Checks

A paperless food safety app for a Korean, Chinese and Japanese grocery with a hot food counter. It replaces the paper sheets staff fill in by hand for hot food temperatures, delivery checks and date checks. Every record is time-stamped, named, and cannot be changed afterwards.

**Live demo:** [Open Seoul Plaza Checks](https://kamal917326.github.io/seoul-plaza-checks/)

> The demo runs with example data saved only on your device. Every demo PIN is **1234**; Kamal is the manager.

## The problem

All food safety records in the shop were on paper:

- Hot food on the counter (pork, beef, tofu, corn dogs and four kinds of chicken) is probed every 2 hours and written on a sheet.
- Deliveries are ticked off on paper against the delivery note.
- Best before and use-by dates are checked by walking the shelves.

Paper records get missed, are hard to read, and are hard to find when an Environmental Health Officer inspects the shop.

## What it does

| Part | What staff do | What the app makes sure of |
|---|---|---|
| **Hot food log** | Probe each tray at every round and type the reading | Below 63°C cannot be saved without a corrective action (reheat to 75°C with re-check, sell within one 2-hour period, or discard). Late and missed rounds show in red |
| **Delivery check-in** | Pick the supplier, scan items, enter temperature and date, tick arrival checks, photograph the note, sign | Chilled above 8°C, frozen warmer than −15°C and short use-by dates are rejected. Short and missing items are listed with their value to claim back |
| **Dates and waste** | Act on the daily list | Use-by past its date is blocked and must be removed. Best before asks for a quality check. Removals go to a waste log in £ |
| **Records by date** | Open any day | The full day's food safety record, ready for an inspector, downloadable as CSV |
| **Settings** (managers) | Manage staff and PINs, hot food items, suppliers and products, check times | Only a manager account with a manager PIN can change them |

## How it works

- **Front end:** plain HTML, CSS and JavaScript. No build step. Hosted free on GitHub Pages and installable on a phone's home screen.
- **Database:** [Supabase](https://supabase.com) (Postgres). Row-level security means:
  - only the shop's own accounts can read or write anything;
  - temperature, delivery and waste records can be added but never edited or deleted;
  - staff PINs are stored hashed and are never sent to the app;
  - only manager accounts can change settings.
- **Two modes:** with `js/config.js` empty the app runs in demo mode. With the Supabase keys filled in it uses the shared database.
- **Barcode scanning:** phone camera in Chrome on Android, or any Bluetooth handheld scanner.

```
index.html              app shell
css/app.css             styles (light and dark mode)
js/config.js            connection settings (empty = demo mode)
js/store.js             data layer: demo backend and Supabase backend
js/app.js               screens and logic
supabase/schema.sql     tables, security rules, PIN functions
supabase/seed.sql       starter data
docs/SETUP.md           step-by-step guide to go live
```

## Going live

Follow **[docs/SETUP.md](docs/SETUP.md)**: create a free Supabase project, run two SQL files, create a shop account and a manager account, paste two keys into `js/config.js`, and upload to GitHub Pages.

## Run it locally

Open `index.html` in a browser, or serve the folder:

```bash
python -m http.server 8000
# then open http://localhost:8000
```

## Roadmap

- Fridge and freezer daily temperature checks
- Push reminders at each hot food round
- PDF export of the daily record
- Power BI dashboard for waste, supplier performance and check compliance
- Hiring and onboarding: application form, e-signed contracts and right-to-work check records

## Author

Kamal
