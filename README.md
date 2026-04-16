# ABB Trading Journal

ABB Trading Journal is a lightweight web app for documenting BingX trades from screenshots, reviewing them manually, and exporting the final journal data as CSV or JSON backup files.

The app is built as a static Progressive Web App (PWA). It runs entirely in the browser, stores data locally on the device, and uses OCR to extract key trade details from screenshots.

## Overview

The journal is designed for a simple workflow:

1. Add your starting account size.
2. Import an open-trade screenshot and/or a closed-trade screenshot.
3. Let OCR prefill the form.
4. Correct the values manually if needed.
5. Save the trade.
6. Review open and closed trades.
7. Export monthly CSV files or full JSON backups.

## Main Features

- Static web app with no backend setup required
- Installable PWA for desktop and mobile
- OCR-based extraction from BingX trade screenshots
- Separate handling for open-trade and closed-trade screenshots
- Manual editing of all detected values before saving
- Local trade storage in the browser via `localStorage`
- Metrics dashboard for account size, total PnL, win count, and loss count
- Trade list with state and month filters
- Monthly CSV export for closed trades
- CSV import for existing journal rows
- Full JSON backup export and restore

## Technology

- `index.html`: full UI, styles, logic, OCR parsing, storage, import/export
- `manifest.webmanifest`: PWA metadata
- `service-worker.js`: offline asset caching
- `tesseract.js` loaded from CDN for OCR

## How To Install

### Option 1: Run locally

1. Clone the repository:

```bash
git clone https://github.com/DieVukisHome/trade-journal.git
cd trade-journal
```

2. Start a local static server:

```bash
python3 -m http.server 8000
```

3. Open the app in your browser:

```text
http://localhost:8000
```

### Option 2: Deploy to GitHub Pages or any static host

Because the project is a pure static web app, it can be hosted on:

- GitHub Pages
- Netlify
- Vercel static hosting
- Any basic web server that serves static files

Upload these files as-is:

- `index.html`
- `manifest.webmanifest`
- `service-worker.js`
- `icon.svg`

### Install as a PWA

After opening the app in a supported browser:

1. Open the browser install menu.
2. Choose `Install app`, `Add to Home Screen`, or the browser equivalent.
3. Launch ABB Trading Journal like a normal app.

## How To Use

### 1. Set the starting account size

Enter your initial account size in the `Start Account Size` field. The dashboard uses this value to calculate:

- current account size
- total PnL
- percentage return
- wins
- losses

### 2. Import screenshots

The journal supports two screenshot types:

- `Open Trade Screenshot`
- `Closed Trade Screenshot`

You can click the upload area or drag and drop an image file.

Typical flow:

1. Add an open-trade screenshot when the position is entered.
2. Add a closed-trade screenshot when the trade is finished.
3. Let OCR read the image.
4. Review the form fields and fix anything OCR interpreted incorrectly.

### 3. Review and edit the trade form

The form contains these journal fields:

- `Post date`
- `Session`
- `Coin`
- `Direction`
- `1% Risk`
- `TF trade taken`
- `Status`
- `$ PnL`
- `Did you follow your rules`
- `Win or Loss?`
- `TV link`
- `Notes`
- `Emotions`

OCR tries to prefill values such as:

- coin
- direction
- trade times
- average price
- close price
- realized or closed PnL

You should always verify the result before saving.

### 4. Save an open or closed trade

- If `$ PnL` is empty, the record is treated as an open trade.
- If `$ PnL` is filled, the record is treated as a closed trade.
- `Win or Loss?` and `Status` may be inferred automatically from PnL values, but you can still change them manually.

Click `Save Trade` to store the record in the browser.

### 5. Manage trades

Open the `Trades` view to:

- review all saved records
- filter by `all`, `open`, or `closed`
- filter by month
- reopen an entry for editing

### 6. Export data

Open the `Export` view for these actions:

- `Export monthly CSV`: exports closed trades for the selected month
- `Import CSV`: imports rows with the expected journal header format
- `Export Backup`: exports the full dataset and settings as JSON
- `Import Backup`: restores the full dataset from a JSON backup
- `Clear All Trades`: deletes all locally stored records after confirmation

## Expected CSV Format

The app expects the following CSV columns:

```text
Post date, session, Coin, Direction, 1% Risk, TF trade taken, Status, $ PnL, Did you follow your rules, TV link, Notes, Emotions, Win or Loss?
```

For best compatibility, keep the header names exactly as shown above.

## Handling Conditions

This section describes the practical conditions and limitations for correct operation.

### Browser and runtime requirements

- Use a modern browser with JavaScript enabled.
- `localStorage` must be available, because the app stores records only in the browser.
- PWA installation and offline behavior work best over `localhost` or `https`.

### OCR requirements

- OCR depends on `tesseract.js`, which is loaded from a CDN.
- The browser must have internet access when the OCR library is not already available.
- OCR accuracy depends heavily on screenshot quality.
- Clear, uncropped BingX screenshots with readable labels produce the best results.
- OCR is a helper, not a source of truth. Manual review is always required before saving.

### Screenshot handling conditions

- The parser is optimized for BingX-style trade screenshots.
- Missing labels, cropped values, blurred text, overlays, or unusual layouts may reduce accuracy.
- Open-trade screenshots are used mainly for setup details.
- Closed-trade screenshots are used mainly for final PnL and closing details.

### Data handling conditions

- All records are stored locally in the browser, not on a server.
- Clearing browser storage, changing browser profiles, or switching devices will not carry over your data automatically.
- If your journal matters, export JSON backups regularly.
- Importing a backup replaces the current in-browser dataset with the backup content.
- Importing CSV adds imported rows to the current journal.

### Operational limitations

- There is no user account system.
- There is no cloud sync.
- There is no backend validation.
- There is no guarantee that OCR-detected values are correct.
- The app currently mixes an English data structure with a German UI label set in several places.

## Recommended Workflow

For reliable results, use this order:

1. Start the app and set the account size.
2. Import the open-trade screenshot.
3. Check the OCR result and complete any missing fields.
4. Save the trade as open.
5. When the trade closes, import the closed-trade screenshot.
6. Review the PnL, status, and notes.
7. Save the updated trade as closed.
8. Export the monthly CSV and regular JSON backups.

## Privacy

ABB Trading Journal is privacy-friendly by design:

- no server-side storage
- no account registration
- no database connection
- no external sync service

The only external dependency used during normal operation is the OCR library loaded from CDN.

## Troubleshooting

### OCR is not available

Possible causes:

- no internet connection
- CDN blocked by the browser or network
- script loading failed

What to do:

- reload the page
- check the internet connection
- use the form manually if OCR is temporarily unavailable

### My data is missing

Possible causes:

- browser storage was cleared
- a different browser profile or device is being used
- a backup import replaced the current data

What to do:

- restore a JSON backup if available
- keep regular backup exports

### PWA installation does not appear

Possible causes:

- unsupported browser
- page opened directly from a file path instead of `localhost` or `https`
- browser-specific install restrictions

What to do:

- run the app through a local server
- try Chrome, Edge, or Safari on a supported platform

## Suggested Screenshots For This Documentation

If you want to extend the documentation visually later, these are the most useful screenshots to add:

1. Dashboard and top navigation
2. Screenshot import area with an open trade image loaded
3. Trade edit form after OCR prefills values
4. Trades list with open and closed records
5. Export view with CSV and backup actions

## Repository

GitHub repository:

[https://github.com/DieVukisHome/trade-journal](https://github.com/DieVukisHome/trade-journal)
