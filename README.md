# Tenant Satisfaction Analysis: Councils vs Housing Associations (2024–25)

An Excel analysis of England's social housing **Tenant Satisfaction Measures (TSM)** for 2024–25, published by the Regulator of Social Housing.

**Question:** Do council tenants or housing association tenants report higher overall satisfaction with their landlord?

## Key finding

Across **353 social landlords**, housing association tenants reported higher overall satisfaction than council tenants:

| Landlord type | Avg overall satisfaction | Number of landlords |
|---|---|---|
| Housing associations (PRP) | **74.0%** | 195 |
| Councils (LA) | **68.1%** | 158 |
| All landlords | 71.3% | 353 |

That is a gap of about **6 percentage points**.

### Limitations

- Each landlord counts equally, so a small landlord affects the average as much as a large one (the averages are not weighted by number of tenants).
- The comparison shows a difference, not its cause. Factors such as region or landlord size may explain part of the gap.

## Data

- **Source:** Regulator of Social Housing, Tenant Satisfaction Measures 2025 release (2024–25 reporting year), File 01: low-cost rental (LCRA) tenant perception results.
- **Scope:** one row per landlord, low-cost rental tenants only.

## What I did

### 1. Cleaning

- Kept the raw data untouched on its own sheet (in) and worked on a separate Clean sheet, so the original could always be restored.
- Reduced **135 columns to 17** (about 87% fewer), keeping only what the question needed: landlord name, ID, type, region, number of tenants and the 12 satisfaction scores (TP01–TP12).
- Used only the _Calc satisfaction columns, which hold the final percentages; the others were breakdowns by survey method or answer type.
- Fixed data-quality issues:
  - Landlord IDs stored as a mix of numbers and text → set the whole column to Text.
  - A score stored as text because of hidden leading spaces → converted back to a number.
  - Non-numeric [E] codes in two score cells → cleared to blank (not 0, which would falsely pull averages down).
- Renamed long regulator headers to short, readable names (e.g. TP01_Satisfied_Calc_LCRA → Overall).
- Converted the data to an Excel table named TSM.

### 2. Analysis

- Built a PivotTable (pvt_LA_vs_PRP) showing **average** overall satisfaction and the **count** of landlords by landlord type.
- Changed Excel's default aggregation from Sum to Average, since adding percentages together has no meaning.
- Kept the landlord count alongside the average so each figure's sample size is visible.

### 3. Visualisation

- Created a clustered column chart from a separate PivotTable containing only the average, so the counts (158, 195) and averages (~70) were not plotted on the same axis.
- Fixed Excel's default vertical axis, which started at 64 and made the gap look several times bigger than it is. The axis now runs from **0 to 100**.
- Added a clear title, axis titles and data labels, and removed the unnecessary legend and field buttons.

## Files

| File | Description |
|---|---|
| tsm_2024_25_analysis.xlsx | Excel workbook: raw data (in), cleaned table (Clean) and analysis with chart (LA_vs_PRP) |
| tsm_2024_25_clean.csv | The cleaned data as CSV (353 landlords, 17 columns), readable on GitHub |

## Tools

Microsoft Excel: tables, Find & Replace, PivotTables, PivotCharts.

## Next steps

- Compare satisfaction by **region** to test whether location explains part of the gap.
- Weight averages by number of tenants to see the picture per tenant rather than per landlord.
- Look at the other measures (repairs, complaints, safety) to see where the gap is largest.
