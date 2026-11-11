PRODUCTION TRACKER — FIRST WORKING VERSION

Contents
- index.html: app interface
- app.js: local app logic and calculations
- manifest.webmanifest: Android/PWA install metadata
- sw.js: offline app cache
- assets/: app icons

CURRENT FEATURES
- 35-day month calendar
- Four timeframes per day: Morning, Mid-Day, Evening, Night
- Record one production action per profession in a timeframe
- Profession list starts with Lumberjack, Sawyer and Builder from the supplied workbook's Data Sheet
- Add/edit/delete professions and define their product, supplier, supplier ratio, usable-material flag, starting inventory and starting TP
- Automatic proficiency dice: Un-Skilled 2d6, Skilled 3d6, Expert 4d6, Master 6d6
- Manual dice roller (d4, d6, d8, d10, d12, d20, d100), modifier and roll history
- Supplier stock is a hard limit. A profession with no supplier stock cannot work. Potential output is capped at available supplier stock multiplied by the buyer's configured output-per-supplier-unit ratio.
- Inventory carries across months; supplier consumption is deducted from the supplier's balance
- Training points follow the supplied Column AP rule: each timeframe result at least equal to Base Output earns 1 TP; a result exactly equal to 2x Base Output earns 2 TP; results greater than Base Output but not exactly 2x earn 1 TP. TP is calculated from actual output after supply caps.
- TP accumulates permanently. Proficiency thresholds: 0–99 Un-Skilled, 100–399 Skilled, 400–999 Expert, 1,000+ Master. Master earns no additional TP.
- Backup export/import to JSON
- Local browser storage and offline caching

WORKBOOK NOTES
The supplied workbook has a blank Tracker Template (no action history or populated profession rows) and a Data Sheet containing three profession definitions. The app seeds those three professions. The workbook's formulas establish Base Output values of 6, 9, 12 and 20 for Un-Skilled, Skilled, Expert and Master. Column AP counts qualifying daily/timeframe cells using COUNTIF(>= Base Output) plus COUNTIF(= 2x Base Output), so an exact double earns 2 TP while any other value at or above Base Output earns 1 TP.

The supplied Data Sheet listed Builder's Supplier as “MP”, but the user's explicit gameplay rule says Builder is the buyer of Sawyer and can use no more lumber than Sawyer has. Therefore the initial app configuration links Builder to Sawyer at a 1:1 ratio. Sawyer is linked to Lumberjack at 6 units of Sawyer output per 1 unit of supplier input, matching the workbook's QTY per Supply value of 6.

IMPORTANT LIMITATIONS IN THIS FIRST VERSION
- This is a first working MVP, not a published Google Play app.
- Data is stored in the browser on this device. Use Export Backup before clearing browser data or changing phones.
- To install as a true Android PWA and use offline caching, the files must be hosted on an HTTPS website. Opening index.html directly from a file manager may allow basic use but will not enable PWA installation/service-worker features.
- No automatic cloud sync is included (personal, device-local app as requested).
- The app's TP rule uses the actual capped production result, not the un-capped dice result.

DEPLOYMENT
Upload the entire contents of this folder to any static HTTPS host while preserving the folder structure. Open the HTTPS address in Chrome on Android, then use Chrome's three-dot menu > Install app (or Add to Home screen). Keep index.html, app.js, manifest.webmanifest, sw.js and assets together in the same folder.
