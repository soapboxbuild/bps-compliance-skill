---
name: bps-compliance
description: Calculate Local Law 97 carbon penalties, track BEPS and BERDO compliance deadlines, assess building performance against regulatory thresholds, and recommend fine mitigation strategies. Use when asked about LL97, BERDO, building performance standards, carbon penalties, benchmarking compliance, or regulatory fines.
---

# Building Performance Standards Compliance

## Jurisdiction Routing — REQUIRED FIRST STEP

Before any compliance calculation, identify the city:
- **NYC → Local Law 97**: Carbon intensity limits by occupancy group. Fine = (actual_tCO2e − limit_tCO2e) × $268/tonne/year. Current period: 2024–2029. Electricity emissions factor: 0.000288962 tCO2e/kWh (2024–2029) — CHANGES in 2030 and 2035 per Local Law 22. Always flag multi-period projections. Limit = gross_floor_area_sf × occupancy_group_limit (kgCO2e/sf/yr from Appendix A).
- **DC → BEPS**: EUI-based targets by property type (from DOEE benchmarking tool). Phase gates: 2026, 2030, 2036. Alternative Compliance Path available. Not a carbon intensity formula.
- **Boston → BERDO**: GHG intensity trajectory targets by property type. See BERDO section below for full calculation methodology. Penalty: $1,000/tCO2e over limit/year. Non-reporting: $1,000/day.
- **Chicago → TBE**: Thermal Energy Standards, 50,000 sf+ buildings. Benchmarking-first approach.
- **Seattle → Carbon Neutral Buildings**: Fossil fuel elimination for new construction by 2031; existing buildings by fuel phase-out schedule.
- **Toronto → BEPS**: Ontario Building Code integration; ENERGY STAR baseline check required.

If the user's city is not on this list, say so and do not apply any formula.

## LL97 Carbon Penalty Calculation (NYC)

### Carbon Thresholds by Occupancy Group (2024-2029)
Calculate using: Annual Penalty = (Reported Emissions - Threshold) × $268/tCO2e

Key thresholds (tCO2e/sf/yr):
- Multifamily residential (Group R-2): 0.00675
- Office (Group B): 0.00846  
- Retail (Group M): 0.01074
- Hotel (Group R-1): 0.00529
- Parking (Group S-2): 0.00403

Step 1: Get annual emissions from benchmarking data (ENERGY STAR Portfolio Manager)
Step 2: Identify occupancy group (check NYC DOB records)
Step 3: Calculate threshold = GFA × threshold_factor
Step 4: If emissions > threshold → penalty = (emissions - threshold) × 268
Step 5: Note: 2030-2034 thresholds are ~40% tighter

### Free Resources
- Building Energy Exchange LL97 Calculator: https://be-exchange.org/calculator
- NYC Benchmarking Compliance: nyc.gov/benchmarking
- Carbon emissions by fuel type (NYC DEP conversion factors)

## BERDO 2.0 Compliance Calculation (Boston)

### Overview
- **Applies to:** All Boston buildings ≥20,000 sq ft (commercial, residential, institutional)
- **Metric:** GHG emissions intensity (kgCO2e/sf/yr) — annual building-level emissions divided by gross floor area
- **Compliance periods:** 2025, 2030, 2035, 2040, 2050 (each sets tighter limits)
- **Compliance penalty:** $1,000/tCO2e over the annual limit
- **Non-reporting penalty:** $1,000/day
- **Annual reporting deadline:** April 30 (prior year data), submitted to City of Boston Environment Department

### GHG Intensity Limits by Building Type (kgCO2e/sf/yr)

> **Source:** Boston BERDO 2.0 regulations. Verify against the current City of Boston BERDO schedule before relying on these numbers for client advice.

| Building Type | 2025–2029 | 2030–2034 | 2035–2039 | 2040–2049 | 2050+ |
|---------------|-----------|-----------|-----------|-----------|-------|
| Commercial office | 5.3 | 3.3 | 1.9 | 0.7 | 0.0 |
| Multifamily residential | 4.0 | 2.5 | 1.5 | 0.5 | 0.0 |
| Retail / commercial | 4.0 | 2.5 | 1.5 | 0.5 | 0.0 |
| Hotel / lodging | 7.4 | 4.6 | 2.8 | 1.0 | 0.0 |
| Healthcare / medical | 13.0 | 8.1 | 4.8 | 1.7 | 0.0 |
| Lab / life science | 25.0 | 15.6 | 9.4 | 3.3 | 0.0 |
| Education | 4.6 | 2.9 | 1.7 | 0.6 | 0.0 |
| Assembly / recreation | 5.0 | 3.1 | 1.9 | 0.7 | 0.0 |
| Mixed use | 4.5 | 2.8 | 1.7 | 0.6 | 0.0 |

### BERDO Penalty Calculation

```
Actual GHG intensity = Total annual GHG emissions (kgCO2e) ÷ GFA (sf)
Emissions over limit  = max(0, actual_intensity − berdo_limit) × GFA (kgCO2e)
Annual penalty ($)    = (emissions_over_limit ÷ 1000) × 1,000
                      = emissions_over_limit (in tCO2e) × $1,000
```

**Example:** 50,000 sf office building emitting 320,000 kgCO2e/yr in 2026:
- Actual intensity: 320,000 ÷ 50,000 = 6.4 kgCO2e/sf
- 2025-2029 limit: 5.3 kgCO2e/sf
- Over limit: (6.4 − 5.3) × 50,000 = 55,000 kgCO2e = 55 tCO2e
- Annual penalty: 55 × $1,000 = **$55,000/year**

### GHG Emissions Conversion Factors (Boston BERDO)

| Fuel | Emissions Factor |
|------|-----------------|
| Electricity (grid) | 0.000356 tCO2e/kWh (NEPOOL regional factor) |
| Natural gas | 0.0531 tCO2e/therm |
| Fuel oil #2 | 0.0731 tCO2e/gallon |
| Steam (district) | 0.0001148 tCO2e/lb |
| District chilled water | 0.000079 tCO2e/ton-hr |

> Electricity factor changes as the New England grid decarbonizes — always check the current BERDO emissions factor schedule.

### Alternative Compliance Options

1. **Alternative Compliance Payment (ACP):** Pay a fixed fee per tCO2e over the limit in lieu of reducing emissions. Rate set by City annually. Not a long-term strategy; use only for short compliance gaps.
2. **Renewable Energy Credits (RECs):** Purchase Massachusetts Class I RECs to offset electricity emissions. Must be vintage-matched and sourced from in-region projects. Limited to a percentage of total compliance obligation.
3. **Hardship Exemption:** Available for properties with documented financial distress. Application required; covers one compliance period with required corrective action plan.
4. **Historic Building Exemption:** Designated historic buildings may apply for modified compliance pathway if energy retrofits would damage historic fabric.
5. **Specific Use Exemption:** Certain high-intensity uses (data centers, hospital critical care) may qualify for an adjusted limit based on operational intensity.

### BERDO Compliance 5-Year Schedule Calculator

Step 1: Confirm property is ≥20,000 sf and located in Boston
Step 2: Identify primary building type from the GHG intensity table
Step 3: Retrieve prior year benchmarking data (Portfolio Manager or utility data)
Step 4: Calculate actual GHG intensity using BERDO conversion factors
Step 5: For each compliance period (2025, 2030, 2035), compare to the schedule limit
Step 6: For non-compliant periods: calculate penalty, model 3 compliance pathways (fuel switching, efficiency retrofits, ACPs/RECs)
Step 7: Compare NPV of each pathway vs. paying penalties for 5 years

### Key Dates
- April 30: Annual BERDO report due (prior calendar year data)
- Every 5 years: New tighter GHG intensity limits take effect
- First compliance period ends: December 31, 2029
- Resources: boston.gov/departments/environment/building-emissions-reduction-and-disclosure

### BEPS Ordinances by City
| City | Law | Effective | Metric |
|------|-----|-----------|--------|
| NYC | LL97 | 2024 | tCO2e/sf |
| DC | BEPS | 2021 | Energy Use Intensity (EUI) |
| Denver | BEPO | 2022 | EUI (kBtu/sf) |
| Boston | BERDO 2.0 | 2025 | GHG intensity |
| St. Louis | BEPS | 2024 | EUI |
| Chicago | CBEPS | 2023 | EUI |
| Seattle | Building Tune-Ups | 2017 | Operations |
| Toronto | EWRB | 2023 | GHG intensity |

### Compliance Strategy Sequence
1. Pull Portfolio Manager benchmarking data
2. Calculate current vs. threshold gap
3. If non-compliant: estimate penalty
4. Model retrofit scenarios: what EUI/GHG reduction closes the gap?
5. Compare penalty cost vs. retrofit capex + NPV
6. Consider: RECs, offsets (limited LL97 use), green leases

### Key Dates
- LL97 reporting due: May 1 annually (prior year data)
- 2024-2029: First compliance period
- 2030-2034: Second compliance period (stricter thresholds)
- 2035+: Third period (path to carbon neutral)

## EPC Ratings (Europe)
- UK: EPC A-G scale, MEES requires min E for commercial lettings
- EU Taxonomy: NZEB standard or top 15% of national stock
- France: DPE ratings affect rental value and transaction price

## Report Output

When the user asks to generate a report, export results, or produce a PDF, deck, or spreadsheet — dispatch the `report-renderer` subagent from the `soapbox-report` plugin:

```json
{
  "template": "bps-compliance",
  "org": "{org if known}",
  "portfolio": "{portfolio if known}",
  "asset": "{asset if known}",
  "data": { "...structured output from this skill..." }
}
```

The `report-renderer` handles branded pagination, interactive review in the artifact pane, and export to PDF/PPTX/XLSX. Do not produce final output as raw markdown when a formatted report is requested.
