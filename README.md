# Park Bar & Club Manager

A local-first digital replacement for the club/bar's paper stock and sales ledgers.

## Run

```bash
npm install
npm start
```

Open http://localhost:3000

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
