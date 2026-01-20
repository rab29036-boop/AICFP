# Retirement Planning Dashboard - Complete Documentation

## Overview

The Retirement Planning Dashboard is a comprehensive web-based financial planning application designed to help Bob and Susan plan their retirement finances from 2026 through 2052. The application consists of two interconnected HTML dashboards that work together to provide complete retirement financial modeling and portfolio tracking.

---

## Application Components

### 1. Retirement Dashboard (`retirement-dashboard.html`)

The primary application for long-term retirement projections, Roth conversion strategy planning, and financial modeling.

### 2. Holdings Tracker (`holdings-tracker.html`)

A companion application for tracking current portfolio holdings, daily performance, and asset allocation across all investment accounts.

### 3. Settings File (`settings.json`)

Stores all user-configurable parameters, assumptions, and scenario presets for automatic loading.

---

## Retirement Dashboard Features

### Model Parameters (Collapsible Sections)

#### General Settings
| Parameter | Default Value | Description |
|-----------|---------------|-------------|
| Inflation Rate | 3% | Annual inflation rate used to adjust income targets |
| Annual After-Tax Income Target | $325,000 | Target spendable income per year |
| Itemized Deductions | $78,000 | Annual itemized deductions for tax calculations |
| State Tax Rate | 6% | South Carolina state income tax rate |

#### Fixed Income Sources (Annual)
| Parameter | Default Value | Description |
|-----------|---------------|-------------|
| Bob's Pension | $134,686 | Annual pension income |
| Susan's Pension | $22,000 | Annual pension income |
| Susan's Social Security | $21,600 | Annual Social Security benefit |
| Bob's Social Security (at 70) | $61,032 | Social Security starting at age 70 |

#### Account Balances & Returns (End of 2026)
| Account | Default Balance | Default ROI |
|---------|-----------------|-------------|
| Bob's IRA | $1,025,000 | 6% |
| Bob's Roth | $300,000 | 6% |
| Susan's IRA | $800,000 | 6% |
| eTrade IRA | $1,583,637 | 6% |
| Wells Fargo | $2,000,000 | 4% (interest) |

### Scenario System

The dashboard supports two pre-configured scenarios:

#### Conservative Scenario
- All equity accounts: 6% ROI
- Wells Fargo: 4% interest rate
- Represents baseline conservative projections

#### Aggressive Scenario
- Bob's IRA: 13% ROI
- Bob's Roth: 17% ROI
- Susan's IRA: 9.5% ROI
- eTrade IRA: 9.5% ROI
- Wells Fargo: 4% interest rate
- Represents optimistic market performance

### Year Range Selector

View projections for different time horizons:
- **10 Year**: 2026-2035
- **15 Year**: 2026-2040
- **20 Year**: 2026-2045
- **25 Year**: 2026-2050
- **27 Year**: 2026-2052 (full projection)
- **Custom**: Select any start and end year

### Baseline Comparison System

- **Save as Baseline**: Captures current projections for both scenarios
- **Clear Baseline**: Removes saved baseline
- **Comparison Display**: Shows difference from baseline in all metrics

### Backup & Restore

- **Backup Button**: Downloads current settings as `settings.json`
- **Restore Button**: Loads settings from a previously saved JSON file
- **Auto-Load**: Dashboard automatically loads `settings.json` on startup

---

## Financial Model Calculations

### Roth Conversion Strategy

The model implements an optimized Roth conversion strategy:
- **Target**: Fill the 24% tax bracket (up to $403,550 taxable income)
- **Conversion Period**: Bob ages 65-71 (years 2027-2033)
- **Source**: Converts from Bob's Traditional IRA to Bob's Roth IRA
- **Tax Optimization**: Maximizes tax-deferred growth while staying within the 24% bracket

### Required Minimum Distributions (RMDs)

RMD calculations follow IRS life expectancy tables:
- **Bob's accounts**: RMDs begin at age 73
- **Susan's accounts**: RMDs begin at age 75
- **RMD Formula**: Prior year-end balance ÷ Life expectancy factor

### Tax Calculations

#### Federal Tax Brackets (2024 Married Filing Jointly)
| Taxable Income | Rate | Cumulative Tax |
|----------------|------|----------------|
| $0 - $24,800 | 10% | $0 |
| $24,801 - $100,800 | 12% | $2,480 |
| $100,801 - $211,400 | 22% | $11,600 |
| $211,401 - $403,550 | 24% | $35,932 |
| $403,551 - $512,450 | 32% | $82,048 |
| $512,451 - $768,700 | 35% | $116,896 |
| $768,701+ | 37% | $206,583.50 |

#### State Tax
- Flat rate applied to taxable income (default 6% for South Carolina)

### Income Flow Model

For each year (2027-2052), the model calculates:
1. **Fixed Income**: Pensions + Social Security
2. **Interest Income**: Wells Fargo balance × interest rate
3. **RMDs**: Required distributions from IRAs
4. **Roth Conversions**: Calculated to fill 24% bracket (2027-2033 only)
5. **Taxes**: Federal + State on taxable income
6. **After-Tax Income**: Gross income - taxes - Roth conversions
7. **Wells Fargo Withdrawal**: Additional needed to meet income target

---

## Charts and Visualizations

### 1. After-Tax Income (By Source)
- **Type**: Stacked Bar Chart
- **Shows**: Annual spendable income broken down by source
- **Components**: Taxable income after tax + Roth withdrawals + Wells Fargo withdrawals

### 2. Net Worth Over Time
- **Type**: Stacked Bar Chart
- **Shows**: Total net worth with account breakdown
- **Accounts**: Bob's Roth, Susan's IRA, Bob's IRA, eTrade IRA, Wells Fargo

### 3. Account Balances Over Time
- **Type**: Line Chart
- **Shows**: Individual account trajectories
- **Interaction**: Hover shows account value + total

### 4. After-Tax Income (Summary)
- **Type**: Line Chart
- **Shows**: Total annual spendable income trend

### 5. Income Sources by Year (Pre-Tax)
- **Type**: Stacked Bar Chart
- **Shows**: All income sources before tax
- **Components**: Pensions, Social Security, RMDs, IRA distributions, Wells Fargo

### 6. Roth Conversion Strategy
- **Type**: Bar Chart
- **Shows**: Annual Roth conversion amounts (2027-2033)

### 7. Tax Analysis
- **Type**: Bar Chart (full width)
- **Shows**: Federal tax, State tax, and Total tax by year

---

## Data Tables

### Income Sources Table
Displays year-by-year breakdown of:
- Ages (Bob / Susan)
- All pension income
- Social Security benefits
- IRA distributions and RMDs
- Wells Fargo withdrawals
- Interest income
- Roth conversions
- Total income and taxes
- Net income target vs actual

### After-Tax Income Table
Shows spendable income calculation:
- Gross taxable income (excluding Roth conversions)
- Total taxes
- After-tax from taxable sources
- Tax-free withdrawals (Roth, Wells Fargo)
- Total and monthly spendable income

### Account Balances Table
Tracks all account balances:
- Bob's Roth IRA
- Susan's IRA
- Bob's IRA
- eTrade IRA
- Wells Fargo Brokerage
- Total Net Worth
- Baseline comparison (when active)

### Tax Analysis Table
Detailed tax breakdown:
- Gross taxable income
- Itemized deductions
- Net taxable income
- Federal and state taxes
- Marginal, effective federal, and effective total rates

---

## Summary Metrics

The dashboard displays key metrics at the top:

| Metric | Description |
|--------|-------------|
| Net Worth (Start Year) | Total assets at beginning of selected range |
| Net Worth (End Year) | Total assets at end of selected range |
| Net Worth (2052) | Final projected net worth (always shown) |
| Total Roth Conversions | Sum of all conversions in selected range |
| Roth Balance (End Year) | Bob's Roth IRA balance at end of range |
| Total Taxes | Sum of all taxes paid in selected range |
| Monthly Income (End Year) | Monthly spendable income in final year |

---

## Holdings Tracker Features

### Account Structure
- Bob's IRA
- Susan's IRA
- Bob's Roth IRA
- eTrade IRA
- Wells Fargo Brokerage
- Nutrien 401K

### Holdings Management
- Add/edit/delete individual holdings
- Track symbol, description, quantity, price, cost basis
- Automatic gain/loss calculation
- Asset type categorization (Stocks, ETFs, Bonds, Cash)

### Price Updates
- Manual price entry
- Daily snapshot recording
- Performance history tracking

### Charts
- Allocation by Account (pie chart)
- Asset Type Breakdown (pie chart)
- Portfolio Value Over Time (line chart with optional moving averages)

### Data Persistence
- Holdings stored in browser localStorage
- Export/Import functionality for backup
- Performance history tracking

---

## Technical Architecture

### Technologies Used
- HTML5
- CSS3 (with CSS custom properties)
- Vanilla JavaScript (ES6+)
- Chart.js library for visualizations
- Google Fonts (Inter, JetBrains Mono)

### Data Storage
- **Browser localStorage**: Holdings Tracker data
- **settings.json**: Retirement Dashboard settings (file-based)
- **No server required**: Fully client-side application

### File Structure
```
Gemini Financial Advisor/
├── retirement-dashboard.html    # Main retirement planning app
├── holdings-tracker.html        # Portfolio tracking app
├── settings.json               # Dashboard settings backup
├── Documentation.md            # This documentation
└── [various supporting files]
```

---

## Key Assumptions

### Ages
- **Bob**: Born 1962 (age 64 in 2026)
- **Susan**: Born 1952 (age 74 in 2026)

### Retirement Timeline
- **2026**: Base year (no distributions modeled)
- **2027-2033**: Active Roth conversion period (Bob ages 65-71)
- **2032**: Bob turns 70, Social Security begins
- **2033**: Last Roth conversion year (Bob turns 71)
- **2035**: Bob turns 73, RMDs begin from Bob's IRA and eTrade
- **2027+**: Susan (already 75) begins RMDs from her IRA
- **2052**: End of projection (Bob age 90, Susan age 100)

### Financial Assumptions
- Social Security receives 2% annual COLA after age 70
- Income target inflation applies for first 10 years only (then caps)
- Wells Fargo earns simple interest (not compounded within year)
- All account growth occurs before distributions
- Roth conversions happen at year-end

---

## Maintenance Notes

### Updating Account Balances
1. Open retirement-dashboard.html
2. Expand "Account Balances & Returns" section
3. Update balances as of year-end
4. Click "Backup" to save new settings

### Changing Scenarios
1. Modify the SCENARIOS object in the JavaScript code
2. Or create new settings.json with desired values

### Extending Projections
- The model is hard-coded for 2026-2052
- To extend, modify MODEL_END_YEAR and ALL_YEARS generation

---

## Version History

- **v1.0** (January 2026): Initial release with Roth conversion modeling
- **v1.1**: Added net worth stacked bar chart
- **v1.2**: Added backup/restore functionality with settings.json auto-load

---

## Support

For questions or modifications, the application source code is fully contained in the HTML files and can be edited with any text editor. All calculations are performed in JavaScript and can be traced through the `calculateModel()` function.
