# JGK MoneyHaven PRO — Personal Finance Dashboard

A browser-based personal finance dashboard for reviewing income, expenses, running balance, category spending, monthly trends, and individual transactions. The dashboard loads transaction data from Google Sheets and presents it through interactive charts, summary cards, filters, and tables.

**Live Dashboard:** [JGK MoneyHaven PRO](https://jakkagopalakrishna.github.io/personal-finance-dashboard/)

> **Data note:** The dashboard depends on the connected Google Sheet being accessible to the page. Keep sensitive financial data and sharing permissions in mind when configuring the sheet.

---

## 📌 Dashboard Features

### 💰 Summary Cards

The dashboard starts with three high-level financial indicators:

- **Total Income** — the sum of transactions marked as income in the active dataset.
- **Total Expenses** — the sum of expense transactions in the active dataset.
- **Current Balance** — the net result of income minus expenses in the active dataset.

These cards provide a quick overview before exploring the detailed charts and transaction list.

### 📈 Groww-Style Running Balance Chart

The interactive balance chart displays how the running balance changes as transactions occur. It includes:

- **Time-range controls:** `1D`, `1W`, `1M`, `3M`, `6M`, `1Y`, and `ALL`.
- **Portfolio value:** the latest running balance represented by the displayed transaction history.
- **Period change:** the net balance movement over the selected range.
- **Period start, high, and low:** reference values to help compare the selected period.
- **Hover details:** inspect a data point's balance, transaction type, amount, and category.
- **Interactive navigation:** zoom and pan horizontally to explore transaction history.

On initial load, the chart can focus on the latest few transaction points while retaining the `ALL` range selection. Use the range controls or **Reset View** to navigate the data.

### 📊 Income vs Expense by Category

This grouped bar chart compares income and expense totals across categories. It helps identify which categories contribute income and which account for spending. Use the legend and hover tooltips to inspect values.

### 📅 Monthly Income, Expense, and Balance

The monthly chart compares income and expenses across months and also displays the running net balance trend. It is useful for spotting changes in spending and income over time.

### 📉 Expense Breakdown by Category

This chart groups expense transactions by category and sorts categories by expense amount. Its month dropdown lets you inspect a specific month or choose **All Time**. The latest month with expense data is selected by default, and month options are ordered from newest to oldest, with **All Time** at the bottom.

The displayed total expense updates to match the selected month or all-time view.

### ⚖️ Income vs Expense Doughnut Chart

The doughnut chart provides a high-level comparison of total income and total expenses, making the relative proportions easy to scan.

### 🕒 Recent Transactions

The transaction table displays recent transactions with their date, category, type, and amount. It supports:

- **Category filter** — show transactions from a selected category.
- **Type filter** — show income only, expenses only, or all types.
- **Date range** — filter between a start date and an end date.
- **Apply and Clear controls** — apply the selected criteria or clear transaction filters.
- **Rows per page** — choose how many rows to display at once.
- **Pagination** — move between pages when the filtered result contains more rows than fit on one page.

### 📋 Category Summary

The category summary table combines income and expense totals by category and calculates the net total for each category. It helps compare category-level financial activity in one place.

### 💳 Global Payment Method Filter

The planned/current v6.0 feature adds a **Payment Method** selector in the footer. It is designed to populate options from the transaction data, default to **UPI** when that option is available, and apply the selected method consistently across the dashboard.

When enabled, changing the payment method should update the summary cards, running balance, charts, expense breakdown, recent transactions, and category summary. The payment method filter works alongside the existing transaction inclusion rule. Test the available methods (such as UPI and PF) against the live sheet after deployment to confirm the data column mapping and results.

### 🔄 Reset View

The **Reset View** button restores chart zoom levels to their initial view where supported. It is useful after zooming or panning through a large dataset.

### 🦶 Footer and Data Source

The footer contains JGK MoneyHaven PRO branding, the app version, a link to the Google Sheets data source, and the Payment Method selector in the global-filter release.

---

## 🧾 Transaction Inclusion Rule

The dashboard uses the `IncludeInTransaction` field in column H of the connected Google Sheet to decide whether a row should be included in dashboard calculations:

- `FALSE` — exclude the transaction.
- `TRUE` — include the transaction.
- Blank — include the transaction.

Only rows explicitly marked `FALSE` are excluded. Keep this rule in mind when checking why a transaction does or does not affect totals and charts.

---

# 📊 JGK MoneyHaven PRO — Chart Interaction Guide

This guide explains how to use the interactive chart features in the dashboard, including **zooming**, **panning (scrolling)**, and **resetting the view**.

---

## 🔍 Zoom In / Zoom Out

You can zoom into charts to analyze data in detail.

### 🖱️ Using Mouse Wheel

* Scroll **up** → Zoom **in**
* Scroll **down** → Zoom **out**

### 🤏 Using Touch (Mobile)

* Use **pinch gesture** (two fingers):

  * Pinch inward → Zoom out
  * Spread outward → Zoom in

---

## ↔️ Scroll / Pan (Move Left & Right)

Once you are zoomed in, you can move across the chart.

### 🖱️ Desktop

* Click and drag left/right on the chart to move through the visible data where panning is supported.

### 📱 Mobile

* Swipe left or right to explore the chart where panning is supported.

👉 This helps you explore older or newer data points easily.

---

## 🔄 Reset Chart View

If you want to go back to the chart's initial view:

* Click the **Reset View** button at the top of the dashboard.

This will reset zoom for charts that support the reset action. The visible range may depend on the chart's configured initial view and selected time-range control.

---

## 💡 Tips for Best Usage

* Zoom in to analyze **specific days or transactions**.
* Use pan/scroll to navigate large datasets.
* Reset the view after deep zooming to avoid confusion.
* Use the running balance chart's time-range buttons to switch between short-term and longer-term views.
* Combine date, category, and transaction-type filters to narrow the Recent Transactions table.
* Compare the month-specific expense breakdown with **All Time** to understand both recent and long-term spending.
* If a transaction appears to be missing, check its `IncludeInTransaction` value in the Google Sheet.

---

## ⚠️ Notes

* Zoom is configured on the **X-axis** for charts that support the zoom plugin.
* A minimum zoom range is configured to help avoid over-zooming.
* Available interactions and the initial visible range can differ by chart.
* Performance depends on the size of the dataset and the browser/device.
* Dashboard totals depend on the transactions returned by the connected Google Sheet and the active filters.
* The Payment Method filter depends on the payment method values being present and consistently recorded in the source data.

---

## 🚀 Interaction Summary

| Action | Desktop | Mobile |
| --- | --- | --- |
| Zoom In | Scroll up over a chart | Pinch outward |
| Zoom Out | Scroll down over a chart | Pinch inward |
| Scroll/Pan | Click and drag where supported | Swipe where supported |
| Reset View | Click **Reset View** | Tap **Reset View** |
| Change Balance Range | Select `1D` / `1W` / `1M` / `3M` / `6M` / `1Y` / `ALL` | Tap the desired range |

---

## 🛠️ Data and Troubleshooting

- **Dashboard data does not load:** check the internet connection, Google Sheet URL/ID, and the sheet's access settings.
- **Totals look incorrect:** verify transaction dates, types, amounts, and the `IncludeInTransaction` field.
- **A payment method is missing:** verify that the method is recorded consistently in the source sheet and that the deployed version reads the correct column.
- **Charts do not respond to zoom:** try the mouse wheel or touch pinch gesture, then use **Reset View**. Some chart types may not support every interaction in the same way.
- **Recent Transactions looks empty:** clear category, type, and date filters and check whether any transactions remain after inclusion rules are applied.

---

## 🧰 Technologies

The page uses HTML, CSS, and JavaScript for the interface and dashboard logic, Google Sheets as the transaction data source, and Chart.js for visualizations. Chart interaction uses the Chart.js zoom plugin and Hammer.js for touch gesture support. External libraries are loaded through CDN links in the page.

---

## 📦 Project Purpose

JGK MoneyHaven PRO is intended to make personal financial activity easier to review in one place. Summary cards provide a quick snapshot, charts reveal category and month-level patterns, transaction filters help locate individual entries, and the running balance chart supports exploration over time.

---

Enjoy exploring your financial data interactively! 📈

**Live Link:** [JGK MoneyHaven PRO](https://jakkagopalakrishna.github.io/personal-finance-dashboard/)
