# InvoiceExpensePro Tools

A static, frontend-only collection of invoice, finance, business, reporting, and document tools. There is no account, backend, database server, or subscription.

## Run the app

Open `index.html` in a modern browser, or serve this folder with any static file server. For example, from this folder run `python -m http.server 8000` and open `http://localhost:8000`.

The core interface and calculations work locally. PDF creation, spreadsheets, charts, PDF merging, and OCR load their pinned libraries from public CDNs when first used, so those features require an internet connection.

## Project files

- `index.html` — semantic page shell, navigation, metadata, currency display preference.
- `css/styles.css` — responsive design system. Edit `--navy`, `--teal`, and related variables at the top to change the theme.
- `js/app.js` — tool catalog, calculations, browser storage, dashboard, reports, exports, and reusable form/table engines.

To change the brand, edit `.brand` in `index.html`. Tool names, categories, and descriptions live in the `TOOLS` list in `js/app.js`. The category SVG icons are defined in `ICON_PATHS`.

## Tool inventory

### Invoices and billing

Invoice Generator, Quote Maker, Receipt Maker, Invoice PDF Generator, Payment Receipt Generator, Recurring Invoice Planner.

Invoice and invoice PDF records support partial payments. Use **Record payment** on an invoice row to add an amount and payment date. Outstanding balances and overdue states update from that payment history. Fixed and percentage discounts are supported.

### Finance

Expense Tracker, Profit Calculator, Loss Calculator, Budget Planner, Cash Flow Calculator, Break-Even Calculator, Savings Planner.

### Business calculators

Tax Calculator, Discount Calculator, Markup Calculator, Profit Margin Calculator, Commission Calculator, Loan Repayment Calculator.

### Business management and reports

Client Manager, Product & Service Manager, Inventory Tracker, Purchase Order Generator, Salary Calculator, Business Report Generator, Reports & Analytics.

Reports & Analytics includes income, expense, cash-basis profit and loss, cash flow, invoice status, receivables, expense categories, monthly/yearly summaries, client billing, and inventory reports. Reports support date presets, custom dates, table search, CSV export, spreadsheet export, and print-to-PDF. Saved-record tables have global field search and field-based sorting.

The dashboard summarizes recorded payments and expenses, open/overdue invoices, paid/unpaid counts, recent transactions, and inventory value. Its charts use saved records only. An unpaid invoice is not treated as received cash.

### Document and file tools

CSV Viewer, CSV-to-JSON Converter, Excel Export Tool, PDF Utility (merge/extract pages), Receipt OCR Scanner.

## Currency display

Choose a display currency in the header. It changes number formatting only; it does not convert values or retrieve exchange rates. Existing records do not contain a currency field, so choose the currency that matches your data. If none is selected, values display without a currency code.

## Data and privacy

Records are stored in this browser's localStorage on this device. They are not uploaded or synchronized. Clearing browser data can erase them. Use **Export all my data** for a JSON backup before changing devices or clearing storage. **Import backup** asks before replacing current records. **Delete all my data** separately asks for confirmation before removing the app's saved records.

Changing a product's current price does not rewrite saved invoice line items; invoice descriptions, quantities, and prices are stored on each document.

## Calculation assumptions and limits

- Tax and discount calculations use the flat rates entered by the user; tax rules vary by jurisdiction.
- Business summaries use a cash basis: recorded invoice payments are income, and expenses use their saved expense dates.
- Historical invoices made before payment tracking have no payment history; they are not counted as cash received unless a payment is recorded.
- Inventory is a current quantity snapshot because inventory movement dates are not captured.
- OCR results need manual review. Loan and tax outputs are estimates and are not legal, tax, or financial advice.
- The app does not fetch live currency rates, sync devices, or provide automated invoice reminders.
