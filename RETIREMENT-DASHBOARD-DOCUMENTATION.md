# Retirement Dashboard Documentation

**Last Updated:** January 17, 2026
**File:** `retirement-dashboard.html`

---

## Overview

The Retirement Dashboard is an interactive HTML-based visualization tool for projecting retirement income, account balances, and tax implications over a customizable time horizon. It provides scenario analysis capabilities with configurable parameters.

---

## Features

### Scenario Selection

The dashboard supports multiple baseline scenarios:
- **Baseline (Conservative)** - Conservative market assumptions
- **Moderate Growth** - Moderate market growth assumptions
- **Aggressive Growth** - Higher growth assumptions

Use the dropdown at the top of the dashboard to switch between scenarios.

### Year Range Presets

Quick preset buttons allow jumping to common planning horizons:
- **10 Years** (2027-2036)
- **15 Years** (2027-2041)
- **20 Years** (2027-2046)
- **25 Years** (2027-2051)
- **27 Years** (2027-2053)

---

## Charts

### After-Tax Income by Year (Stacked Bar Chart)

**Purpose:** Shows spendable income after taxes are applied.

**Income Sources (bottom to top):**
1. Bob's Pension (purple)
2. Susan's Pension (light purple)
3. Susan's Social Security (blue)
4. Bob's Social Security (cyan)
5. Susan's IRA RMD (pink)
6. eTrade IRA RMD (amber)
7. Roth Withdrawal (teal)
8. Wells Fargo Withdrawal (green)

**Note:** Bob's IRA Distribution is excluded from this chart because it represents a Roth conversion (moving money between accounts), not spendable income.

**Tax Calculation:** Taxable sources (pensions, Social Security, RMDs) are reduced by the effective tax rate. Tax-free sources (Roth, Wells Fargo) pass through at 100%.

### Income Sources by Year (Stacked Bar Chart)

**Purpose:** Shows all pre-tax income sources including Roth conversions.

**Income Sources (bottom to top):**
1. Bob's Pension (purple)
2. Susan's Pension (light purple)
3. Susan's Social Security (blue)
4. Bob's Social Security (cyan)
5. Susan's IRA RMD (pink)
6. eTrade IRA RMD (amber)
7. Roth Withdrawal (teal)
8. Wells Fargo Withdrawal (green)
9. Bob's IRA Distribution (orange) - Roth conversion amount

### Account Balances Over Time (Line Chart)

**Purpose:** Shows projected account balance trajectories.

**Accounts displayed:**
- Bob's Roth IRA (purple)
- Susan's IRA (purple/violet)
- Bob's Traditional IRA (orange)
- eTrade IRA (amber)
- Wells Fargo (green)
- Total (white dashed line)

**Colors:** Matched to the income bar charts for visual consistency.

### Tax Analysis (Dual-Axis Chart)

**Purpose:** Shows tax burden over time.

**Displays:**
- Bars: Federal Tax, State Tax, IRMAA
- Line: Effective Tax Rate (%)

---

## Tables

### Income by Year Table

Displays detailed year-by-year breakdown of all income sources showing:
- Age (Bob / Susan)
- Individual income source amounts
- Total Pre-Tax Income
- Monthly Pre-Tax Income

### After-Tax Income Table

Displays spendable income after applying effective tax rates:
- Age (Bob / Susan)
- Individual after-tax amounts for each income source
- Total After-Tax Income
- Monthly After-Tax Income

**Calculation Method:**
- Taxable sources: Amount × (1 - effectiveTotalRate)
- Tax-free sources: Amount × 100% (no reduction)

**Note:** Bob's IRA Distribution is excluded as it's a Roth conversion, not spendable income.

---

## Chart Interactions

### Tooltips

Hovering over any bar segment shows:
- **Label:** The specific income source and amount
- **Footer:** Total income for that year (sum of all sources)

The tooltip footer shows the true yearly total across all income sources, not just the hovered category.

### Legend

Click legend items to show/hide specific data series.

---

## Color Scheme

The dashboard uses a consistent color palette across all charts:

| Source | Color | Hex |
|:-------|:------|:----|
| Bob's Pension | Purple | `#6366f1` |
| Susan's Pension | Light Purple | `#8b5cf6` |
| Susan's SS | Blue | `#3b82f6` |
| Bob's SS | Cyan | `#06b6d4` |
| Susan's RMD | Pink | `#ec4899` |
| eTrade RMD | Amber | `#fbbf24` |
| Roth Withdrawal | Teal | `#14b8a6` |
| Wells Fargo | Green | `#10b981` |
| Bob's IRA Dist | Orange | `#f59e0b` |

---

## Technical Details

### Dependencies

- **Chart.js** - Used for all chart rendering
- No other external dependencies required

### Responsive Design

The dashboard uses CSS Grid with responsive breakpoints:
- Desktop: 2-column layout for charts
- Mobile: Single column layout

### Data Flow

1. User selects scenario and year range
2. `runSimulation()` calculates projections
3. `updateDashboard()` refreshes all charts and tables
4. Individual render functions handle each component

---

## Change Log

### January 17, 2026

- **Added:** After-Tax Income table showing spendable income by year
- **Added:** After-Tax Income stacked bar chart
- **Changed:** Excluded Bob's IRA Distribution from after-tax displays (Roth conversion rationale)
- **Changed:** Swapped After-Tax Income chart with Account Balances Over Time (improved layout)
- **Changed:** Account Balances line chart colors now match bar chart colors
- **Fixed:** Tooltip totals now show actual yearly total instead of just hovered category
- **Changed:** Income chart dataset ordering (Bob's IRA Distribution on top)

### January 2026 (Earlier)

- **Added:** Year range preset buttons (10, 15, 20, 25, 27 years)
- **Added:** Baseline scenario switching functionality
- **Changed:** Income Sources chart expanded to show specific accounts vs. categories
- **Added:** Dark borders between stacked bar segments for clarity

---

## Related Documents

- [JANUARY-2026-REVISED-STRATEGY.md](JANUARY-2026-REVISED-STRATEGY.md) - Current portfolio strategy
- [FINAL-Bobs-Unified-Portfolio-2026-01-02.md](FINAL-Bobs-Unified-Portfolio-2026-01-02.md) - Bob's portfolio details

---

**END OF DOCUMENTATION**
