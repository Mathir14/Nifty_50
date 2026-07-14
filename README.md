# Can the Average Indian Reliably Build Long-Term Wealth Through a Nifty 50 SIP?

> **An end-to-end data analytics project evaluating whether a passive
> monthly investment in the Nifty 50 historically provided a more
> reliable path to long-term wealth creation than traditional savings
> products.**

------------------------------------------------------------------------

# Executive Summary

This project investigates a practical question faced by many Indian
households:

> **Should long-term savings remain in traditional bank products, or has
> a disciplined Nifty 50 SIP historically been a better vehicle for
> preserving and growing purchasing power?**

Rather than comparing investment products solely by returns, the project
evaluates them through the lens of **real (inflation-adjusted) wealth**,
because preserving purchasing power is ultimately more important than
increasing nominal account balances.

The analysis combines:

-   Deterministic benchmark simulations
-   Historical Nifty 50 backtesting
-   Inflation-adjusted wealth analysis
-   Risk and recovery analysis
-   PostgreSQL data engineering
-   Interactive BI dashboards

------------------------------------------------------------------------

# Why This Project?

Many investment comparisons stop at final returns.

This project instead asks:

-   What happens after inflation?
-   When does compounding become the primary source of wealth?
-   How severe were historical losses?
-   How long did recoveries take?
-   Did long-term investors historically benefit from remaining
    invested?

------------------------------------------------------------------------

# Research Question

> Can an average Indian investing approximately **₹5,000 per month**
> build greater long-term wealth through a passive Nifty 50 SIP than
> through traditional Savings Accounts and Recurring Deposits?

------------------------------------------------------------------------

# Scope

## Included

-   Savings Account benchmark
-   Recurring Deposit benchmark
-   Nifty 50 SIP
-   Inflation-adjusted analysis
-   Purchasing power analysis
-   Drawdowns
-   Recovery periods
-   Wealth composition
-   Dashboard

## Excluded

-   Stock picking
-   Active investing
-   Market timing
-   Gold
-   PPF
-   EPF
-   Taxes
-   Expense ratios
-   Brokerage
-   Monte Carlo simulation

------------------------------------------------------------------------

# Methodology

## Data Sources

  Dataset                  Source                  Coverage
  ------------------------ ----------------------- ------------------------
  Nifty 50 Monthly Index   Historical Index Data   Dec 1995 -- Jan 2026
  Inflation                OECD CPI                1995--2025
  Savings Rate             SBI                     Representative average
  RD Rate                  SBI                     Representative average

------------------------------------------------------------------------

## Benchmark Philosophy

Instead of replaying every historical interest-rate change, benchmark
products use representative long-run averages.

This creates a stable baseline where the investment product is the
primary variable.

  Parameter                      Value
  --------------------------- --------
  Savings Interest               3.31%
  Recurring Deposit              5.85%
  Inflation                      4.94%
  Representative Nifty CAGR     11.85%

Contribution strategies:

-   Fixed ₹5,000/month
-   Increase by 50% of inflation
-   Increase by 100% of inflation

------------------------------------------------------------------------

## Historical Simulation

Each month:

1.  Invest SIP
2.  Purchase fractional index units
3.  Update portfolio
4.  Revalue using actual market prices

Each year:

-   Nominal corpus
-   Real corpus
-   Total contributions
-   Investment gain
-   Purchasing power
-   Wealth composition

------------------------------------------------------------------------

# Technical Architecture

``` text
Historical Data
        │
        ▼
Polars Cleaning
        │
        ▼
PostgreSQL
 ├── benchmark
 └── analysis
        │
        ▼
Derived Analytical Tables
        │
        ▼
Metabase Dashboard
        │
        ▼
Business Insights
```

------------------------------------------------------------------------

# Database

``` text
benchmark/
├── savings_fixed
├── savings_half
├── savings_full
├── recurring_deposit
└── summary

analysis/
├── inflation
├── nifty_monthly
├── nifty_historical_fixed
├── nifty_historical_half
├── nifty_historical_full
├── nifty_wealth_composition
└── *_summary
```

------------------------------------------------------------------------

# Dashboard

## Investor Journey

Displays:

-   Total contributions
-   Nominal portfolio growth
-   Inflation-adjusted portfolio growth
-   Contributions vs investment gains

------------------------------------------------------------------------

## Risk & Reliability

Displays:

-   Drawdowns
-   Running portfolio peak
-   Benchmark vs historical purchasing power

------------------------------------------------------------------------

## Key Findings

Summarizes:

-   Compounding crossover
-   Maximum drawdown
-   Longest recovery
-   Inflation insight
-   Benchmark validation
-   Practical conclusion

------------------------------------------------------------------------

# Results

## Benchmark

  -----------------------------------------------------------------------
  Product                             Observation
  ----------------------------------- -----------------------------------
  Savings                             Preserved nominal capital but
                                      consistently lost purchasing power

  RD                                  Approximately preserved purchasing
                                      power

  Representative Nifty                Produced substantial long-term real
                                      wealth
  -----------------------------------------------------------------------

------------------------------------------------------------------------

## Historical Findings

### Compounding

Investment gains overtook cumulative contributions in **2005**, roughly
ten years after the initial investment.

### Maximum Drawdown

Worst decline:

**≈54%**

Occurred during the **2008 Global Financial Crisis**.

### Longest Recovery

Approximately **33 months**.

### Major Corrections

-   Dot-com Crash
-   Global Financial Crisis
-   COVID-19 Crash

Each recovered to new highs during the historical period.

### Purchasing Power

Historical Nifty investing substantially outperformed both benchmark
products after inflation adjustment.

### Benchmark Validation

Both the deterministic benchmark and historical simulation independently
supported the same long-term conclusion regarding purchasing power.

------------------------------------------------------------------------

# Design Decisions

Several modeling decisions intentionally simplified the analysis.

-   Savings and RD were modeled as benchmarks rather than exhaustive
    banking products.
-   RD rollover strategies were excluded to avoid turning the benchmark
    into portfolio management.
-   Inflation-adjusted wealth was prioritized over nominal balances.
-   Historical simulation used monthly prices rather than annual returns
    to better reflect actual SIP investing.

These choices keep the project focused on the central research question
while remaining reproducible.

------------------------------------------------------------------------

# Tech Stack

-   Python
-   Polars
-   PostgreSQL
-   SQLAlchemy
-   Plotly
-   Metabase
-   NumPy
-   Git

------------------------------------------------------------------------

# Repository Structure

``` text
├── data/
├── notebooks/
├── outputs/
├── dashboard/
├── sql/
├── README.md
└── requirements.txt
```

------------------------------------------------------------------------

# Running the Project

``` bash
git clone <repo>

cd <repo>

python -m venv .venv

source .venv/bin/activate

pip install -r requirements.txt
```

Configure `.env` with PostgreSQL credentials before running notebooks.

------------------------------------------------------------------------

# Limitations

-   Historical performance cannot predict future returns.
-   Taxes, brokerage and expense ratios were excluded.
-   Benchmark products use representative average rates.
-   Assumes uninterrupted SIP investing.
-   Focuses only on passive Nifty 50 investing.

------------------------------------------------------------------------

# Future Work

-   Tax-adjusted analysis
-   Additional investment products
-   Interactive web application
-   Scenario testing
-   Monte Carlo simulation
-   Portfolio optimization

------------------------------------------------------------------------

# Conclusion

This project began with a simple question:

> **Can the average Indian reliably build long-term wealth through a
> passive Nifty 50 SIP?**

Across benchmark simulations and historical market analysis, the
evidence consistently showed that traditional savings products generally
protected nominal balances but struggled to preserve purchasing power
over long horizons. In contrast, the Nifty 50 historically generated
substantially greater inflation-adjusted wealth despite experiencing
severe temporary market declines.

While historical performance should not be interpreted as a guarantee of
future outcomes, the analysis suggests that disciplined long-term
investing historically compensated investors for accepting market
volatility.

------------------------------------------------------------------------

# Skills Demonstrated

-   Data Engineering
-   Time-Series Analysis
-   Financial Analytics
-   Simulation Modeling
-   Statistical Thinking
-   SQL & PostgreSQL
-   Dashboard Design
-   Business Communication
-   End-to-End Analytics Workflow
