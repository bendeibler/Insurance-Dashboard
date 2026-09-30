# Loss Development Analysis: Workers' Compensation Reserving Dashboard

An interactive Tableau dashboard analyzing loss development and reserve adequacy for Workers' Compensation insurers, built on real claims data compiled by the Casualty Actuarial Society (CAS) from NAIC Schedule P filings.

## Overview

This workbook models the core actuarial reserving workflow: tracking how claims from a given accident year grow in value as they mature, and using that pattern to evaluate reserve adequacy.

**Dashboard 1 — Loss Development Triangle**
- Accident year × development lag heatmap of cumulative paid losses (the classic actuarial "triangle")
- KPI panel: earned premium, incurred losses, and loss ratio for the selected insurer
- Dynamic insight text summarizing the selected company's premium and loss ratio
- Filterable by insurer (`GRNAME`)

<img width="1640" height="787" alt="image" src="https://github.com/user-attachments/assets/e5b20295-071c-4936-9038-470f06164e73" />


**Dashboard 2 — Development Factors & Reserve Comparison**
- Age-to-age development factor trend by development lag — shows how quickly (or slowly) claims mature
- Latest cumulative paid loss vs. latest posted reserves by accident year, to assess reserve adequacy
- Company filter carried across both dashboards for consistent comparison

<img width="1630" height="782" alt="image" src="https://github.com/user-attachments/assets/985042a3-6eb2-423c-ac5c-f451fa88c19a" />


## Methodology

- Built on the CAS Loss Reserving Database (Workers' Compensation), sourced from NAIC Schedule P filings, 1998–2007 accident years
- Development factors and "latest diagonal" values calculated using Tableau LOD (Level of Detail) expressions (`FIXED`) to correctly isolate the most recent development period per accident year
- Loss ratio = Incurred Losses / Earned Premium (net)
- Age-to-age factor = current period cumulative paid loss ÷ prior period cumulative paid loss, the standard chain-ladder development metric used in P&C reserving (CAS Exam 5/8/9 methodology)

## Data

`wkcomp_pos_98-07.csv` — Workers' Compensation loss data by insurer, accident year, and development lag, including:
- `GRCODE` / `GRNAME` — insurer group/name
- `AccidentYear`, `DevelopmentLag` — the two triangle axes
- `IncurredLosses`, `CumPaidLoss`, `BulkLoss` — loss measures
- `EarnedPremNet` — net earned premium
- `PostedReserves2007` — reserves as carried by the insurer at year-end 2007

Source: [CAS Loss Reserving Data Pulled from NAIC Schedule P](https://www.casact.org/publications-research/research/research-resources/loss-reserving-data-pulled-naic-schedule-p), compiled by the Casualty Actuarial Society from data provided by S&P Global Market Intelligence.

## Tools

- **Tableau Desktop 2025.2** — data modeling, LOD calculations, dashboard design

## How to View

1. Open `Insurance_dashboard.twb` in [Tableau Desktop](https://www.tableau.com/products/desktop) or Tableau Reader (free), or
2. View it live on (https://public.tableau.com/views/Insurance_dashboard_17907932345430/Dashboard1?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)

## Repo Contents

```
├── Insurance_dashboard.twb     # Tableau workbook
├── wkcomp_pos_98-07.csv        # Workers' Compensation loss data (NAIC Schedule P, via CAS)
└── README.md
```

## About

Built by Ben Deibler, exploring P&C actuarial reserving concepts (loss development triangles, chain-ladder factors, reserve adequacy) ahead of the CAS exam track (ACAS).
