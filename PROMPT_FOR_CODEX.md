# Prompt for Codex — Park Bar & Club Manager

**You are working on an existing Park Bar & Club Manager application. Do NOT rebuild the application from scratch. Inspect the existing code first and preserve all working functionality.**

The application is a digital replacement for the handwritten records used by the club/bar. The current working MVP already supports products, imported paper-ledger products, prices, price-history, stock movements, sales, purchases/suppliers, expenses, dashboard statistics, product intelligence, daily closing, reports, printing, CSV export, login/roles, audit trail and database backup.

## First inspect

- `server.js`
- `public/index.html`
- `public/app.js`
- `public/style.css`
- `README.md`

Do not replace the architecture unless there is a strong technical reason. Make small, testable improvements.

## Product intelligence requirement

The dashboard/product-insights area must dynamically show the following for a selected product, using real database data:

**Example:**

> Tusker Lager
> - Bought at: KSh 180
> - Current buying price: KSh 195
> - Selling at: KSh 250
> - Margin: KSh 55 (and margin %)
> - Sold this week: 146 bottles
> - Sales trend: ↑ 18% compared with the previous 7-day period
> - Current stock: 23 bottles
> - Reorder recommended when current stock is at/below its reorder level

Do NOT hard-code the example. The numbers must come from sales, stock, and price-history records. If there is no previous-period data, display a sensible message instead of inventing a percentage.

The product insight should also show:
- 7-day units sold by day
- price history for buying and selling prices
- estimated-price warning where applicable
- current stock and reorder level
- gross margin per unit

## Existing paper-ledger product data

The initial product catalog was transcribed from the photographed Park Bar stock sheets supplied with the project. Keep this imported catalog intact unless a correction is explicitly requested.

Some handwritten prices were unclear. Those values are intentionally marked as **ESTIMATED** in the database/UI. Do not silently present an estimated price as confirmed. The user must be able to edit the product and replace estimated values with confirmed prices.

If you discover a product that is clearly present in the supplied paper sheets but missing from the database, add it without deleting existing products. Preserve the `source_note` and estimated-price fields.

## Implement/verify these upgrades in priority order

### 1. Daily closing

Maintain a proper daily closing/reconciliation workflow:
- Opening cash
- Cash sales
- M-Pesa sales
- Card sales
- Other sales
- Expenses
- Expected cash
- Actual cash counted
- Difference
- Clearly identify shortage vs overage
- Closing date/time
- User who performed the closing
- Closing note

Expected cash should be calculated from the opening cash, cash sales and cash expenses. M-Pesa/Card should not be treated as physical cash.

### 2. Purchases and suppliers

Receiving stock must support:
- Supplier
- Invoice number
- Purchase date
- Product
- Quantity
- Buying price
- Estimated-price flag
- Total purchase cost

Saving a purchase should increase stock and update buying-price history.

### 3. Price history

When a buying or selling price changes:
- Preserve the previous value
- Add a new price-history record
- Store effective date
- Store whether the price was estimated
- Store source/note

The UI must make price changes easy to understand.

### 4. Reports

Provide:
- Daily report
- Weekly report
- Monthly report
- Sales report
- Expense report
- Stock report
- Profit/result report
- COGS/gross profit
- Best-selling products
- Low-stock/reorder report
- Stock valuation
- Payment-method totals
- Sales by day
- Expense totals by category

Reports must use real database records and not sample/fake figures.

### 5. Printing

Reports should print cleanly on A4 paper.

Printed reports should include:
- Park Bar & Accommodation/business name
- Report title
- Date range
- Generation date/time
- Summary totals
- Tables
- Page-friendly spacing

Avoid printing navigation, buttons and unnecessary UI elements.

### 6. Login and roles

Keep role-based access:
- Administrator/Owner
- Manager
- Cashier
- Stock clerk

Permissions should be sensible. Cashiers should be able to record sales but should not be able to change important product prices or perform management functions unless explicitly allowed.

### 7. Audit trail

Important actions should record:
- user
- action
- entity
- entity ID where applicable
- details
- timestamp

At minimum audit:
- sales
- purchases
- stock movements
- product creation/edit/archive
- expenses
- daily closing

### 8. Backup

Keep the database backup function working and make sure only an Administrator/Owner can perform backups.

## Quality rules

- Do not remove existing working functionality.
- Do not reset or overwrite real user data.
- Do not create fake business transactions just to make charts look populated.
- Do not hard-code sales/trends such as “146 sold” or “18%” — calculate them.
- Use the existing SQLite database unless a migration is genuinely necessary.
- If adding a database column/table, create a safe migration that works on an existing installation.
- Validate quantities, prices, dates and required fields.
- Prevent negative stock unless an explicit correction workflow is implemented.
- Keep money calculations in numeric database fields.
- Make the UI responsive and usable on a normal laptop/desktop.
- Keep the interface simple enough for staff who are not highly technical.
- Prefer clear labels such as “Receive Stock”, “Record Sale”, “Daily Closing”, “Print Report” rather than technical terminology.

## Testing

After changes:
1. Run syntax checks.
2. Start the application.
3. Log in using the existing local admin account.
4. Verify products load.
5. Record a test sale and confirm stock decreases.
6. Record a purchase and confirm stock increases.
7. Change a price and confirm price history is created.
8. Verify product intelligence updates from real data.
9. Verify daily closing calculations.
10. Generate and print a report.
11. Verify audit records are created.
12. Verify backup still works.

Do not stop at explaining what should be changed. Make the changes in the existing project and leave the project runnable with:

```bash
npm install
npm start
```
