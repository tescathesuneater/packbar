# Park Bar & Club Manager

A local-first digital replacement for the club/bar's paper stock and sales ledgers.

## Run

```bash
npm install
npm start
```

Open http://localhost:3000

## Vercel deployment

Set **Root Directory** to `club_system` when importing this repository. The
included `vercel.json` routes the site and API through the Express server.

Vercel functions have a read-only deployment directory, so the app uses `/tmp`
for SQLite while deployed. That prevents the startup crash, but `/tmp` is
ephemeral and is not shared reliably between function instances. It is suitable
only for a preview/demo: sales, stock, users, and settings can disappear at any
time. For a production club system, move the data to a managed persistent
database and set `DATABASE_PATH` only where a real writable persistent disk is
available; Vercel does not provide one for SQLite.

Default local login:
- Username: `admin`
- Password: `admin123`
- Role: Administrator/Owner

## Included
- Products and categories imported from the photographed paper stock sheets.
- Buying/selling prices, estimated-price flags and price history.
- Sales with automatic stock deduction.
- Purchases/suppliers/invoices with automatic stock increase.
- Stock movements and low-stock/reorder alerts.
- Product intelligence: current buy/sell price, margin, units sold this week, 7-day sales trend, current stock and reorder recommendation.
- Expenses.
- Daily cash closing and cash variance.
- Daily/weekly/monthly reports, stock valuation, COGS/gross profit and net result.
- A4 printing and CSV export.
- Roles, audit trail and database backup.

## Important
The product catalog was transcribed from photographed handwritten/printed stock sheets. Where a price was not clear enough to read confidently, the application uses an estimated value and displays `ESTIMATED`. Replace those values with the club's confirmed prices before relying on them for accounting.
