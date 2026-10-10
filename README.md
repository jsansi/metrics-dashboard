# metrics-dashboard

A month-over-month performance dashboard for Facebook and Instagram, built from
the CSV exports in Meta Business Suite.

It is a single file, `index.html`. It needs no server, build step or account,
and works on GitHub Pages or opened straight from your computer. Everything
runs in your browser: imported data is stored locally (IndexedDB) and never
uploaded.

## Using it

1. In Meta Business Suite, open **Insights** and export each Facebook and
   Instagram metric as a CSV. Save them in a folder with a `facebook` and an
   `instagram` folder inside, for example:

   ```
   metricas/
     facebook/   Visualizaciones.csv, Espectadores.csv, …
     instagram/  Visualizaciones.csv, Alcance.csv, …
   ```

2. Open the dashboard and select **Connect folder…**, then choose `metricas`.
   This needs Chrome or Edge.
3. Choose two months in the bar at the top. Every view updates to compare them.

Each month, replace the CSVs in those folders with the new exports. The
dashboard reads the folder every time you open it; select **Refresh** in the top
bar if it is already open. After a browser restart, Chrome asks once for
permission to read the folder again (**Reconnect**).

Re-reading is safe: values are stored once per day, so overlapping dates are
updated rather than counted twice, and unchanged files are skipped. The CSVs
never leave your computer, even when the dashboard itself is on GitHub Pages.

In Safari or Firefox, drop the CSV files (or the two folders) on the page
instead.

## Views

- **Overview**: both platforms side by side, the biggest changes, and a
  12-month snapshot.
- **Facebook / Instagram**: one card per metric, then a detailed view of the
  selected metric (monthly history, day-by-day comparison, every month in a
  table).
- **Trends**: any metrics over 3, 6 or 12 months, all data or a custom range,
  by month or by day.
- **Data**: which months are complete, the list of imports (with Remove), and
  backup, restore and CSV export.

Use one **workspace** per client (the switcher next to the title).

## How the numbers are calculated

- Daily values are grouped into calendar months. A month with missing days is
  marked as incomplete. For a fair comparison with a partial month, switch to
  **Daily average**.
- Facebook **Viewers** and Instagram **Reach** are daily unique counts. Adding
  days together would count the same people more than once, so these always
  show as an average per day.
- **New follows** is the number of follows gained, not the total follower
  count. Instagram's export leaves out days with no new follows, so those days
  add nothing to the total.
- No percentage change is shown when the earlier month is 0. Facebook and
  Instagram figures are never added together.
- Colours show the direction of a change only. Set "Higher is better" or
  "Lower is better" per metric with the ⓘ button.

## Backups

Your data lives in this browser only. Use **Data → Download backup** to keep a
copy or to move to another computer, and **Restore from backup** to load it.
Clearing your browser's site data deletes anything that isn't backed up.

## Credits

Charts: charts-lib (from the chart-dashboard skill), inlined.
Typeface: Schibsted Grotesk, SIL Open Font License 1.1, embedded.
