# Trade Journal

Trade Journal is a lightweight web app for documenting BingX trades from screenshots, reviewing them manually, and exporting the final journal data as CSV or JSON backup files.

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

## How To Install On A Mobile Device

This app is intended to work well as a mobile web app and installable PWA.

### iPhone and iPad

1. Open the deployed app URL in `Safari`.
2. Tap the `Share` button.
3. Tap `Add to Home Screen`.
4. Confirm the app name and tap `Add`.
5. Open `Trade Journal` from the home screen like a normal app.

### Android

1. Open the deployed app URL in `Chrome`.
2. Tap the browser menu.
3. Tap `Install app` or `Add to Home screen`.
4. Confirm the installation.
5. Open `Trade Journal` from the launcher or home screen.

### Important mobile installation conditions

- The app should be served over `https` for the best installation behavior.
- `localhost` also works for development, but that is mainly relevant on desktop.
- Some browsers expose `Install app`, while others only show `Add to Home Screen`.
- If installation is not offered, reload the page once and try again in Safari or Chrome.

## How To Deploy The App

Because the project is a pure static web app, it can be hosted on:

- GitHub Pages
- Netlify
- Vercel static hosting
- any standard static web host

Upload these files as-is:

- `index.html`
- `manifest.webmanifest`
- `service-worker.js`
- `icon.svg`

Once hosted, users can open the public URL on their mobile device and install it from the browser.

## How To Use On A Mobile Device

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

On mobile, tap the upload area and choose a screenshot from your photo library or file picker.

Typical flow:

1. Save the BingX screenshot on your phone.
2. Add an open-trade screenshot when the position is entered.
3. Add a closed-trade screenshot when the trade is finished.
4. Let OCR read the image.
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

Tap `Save Trade` to store the record in the browser on that mobile device.

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

### Mobile browser and runtime requirements

- Use a modern mobile browser with JavaScript enabled.
- `localStorage` must be available, because the app stores records only in the browser.
- PWA installation and offline behavior work best over `https`.
- On iPhone and iPad, `Safari` is the preferred browser for installation.
- On Android, `Chrome` is the preferred browser for installation.

### OCR requirements

- OCR depends on `tesseract.js`, which is loaded from a CDN.
- The browser must have internet access when the OCR library is not already available.
- OCR accuracy depends heavily on screenshot quality.
- Clear, uncropped BingX screenshots with readable labels produce the best results.
- Full-screen mobile screenshots usually work better than compressed or edited images.
- OCR is a helper, not a source of truth. Manual review is always required before saving.

### Screenshot handling conditions

- The parser is optimized for BingX-style trade screenshots.
- Missing labels, cropped values, blurred text, overlays, or unusual layouts may reduce accuracy.
- Screenshots should be taken directly from the mobile trading app before editing or annotation.
- Open-trade screenshots are used mainly for setup details.
- Closed-trade screenshots are used mainly for final PnL and closing details.

### Data handling conditions

- All records are stored locally in the browser, not on a server.
- Clearing browser storage, uninstalling the app, changing browser profiles, or switching devices will not carry over your data automatically.
- If your journal matters, export JSON backups regularly.
- Before replacing or resetting a phone, export a JSON backup first.
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

1. Install the app on your phone through `Add to Home Screen` or `Install app`.
2. Open the app and set the account size.
3. Import the open-trade screenshot from your device.
4. Check the OCR result and complete any missing fields.
5. Save the trade as open.
6. When the trade closes, import the closed-trade screenshot.
7. Review the PnL, status, and notes.
8. Save the updated trade as closed.
9. Export the monthly CSV and regular JSON backups.

## Privacy

Trade Journal is privacy-friendly by design:

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

### Installation on mobile does not appear

Possible causes:

- unsupported browser
- page opened from an unsupported context instead of `https`
- browser-specific install restrictions

What to do:

- open the deployed `https` version
- try Safari on iPhone/iPad or Chrome on Android

## Suggested Screenshots For This Documentation

If you want to extend the documentation visually later, these are the most useful screenshots to add:

1. Home screen icon after installation on a phone
2. Dashboard and top navigation on mobile
3. Screenshot import area with an open trade image loaded
4. Trade edit form after OCR prefills values
5. Trades list with open and closed records
6. Export view with CSV and backup actions

## Repository

GitHub repository:

[https://github.com/DieVukisHome/trade-journal](https://github.com/DieVukisHome/trade-journal)
