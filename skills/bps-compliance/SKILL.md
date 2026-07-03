---
name: bps-compliance
version: 1.0.0
description: >
  Building Performance Standards (BPS) Analysis — identify every applicable building energy,
  carbon, and emissions regulation for a property or portfolio by jurisdiction, calculate
  current and projected penalty exposure, and produce a structured compliance report with
  prioritized remediation pathways. Covers major US cities/states, Canada, UK (MEES, SECR),
  and EU frameworks (EPBD, CSRD/ESRS E1, ETS2). Triggers on: "BPS compliance", "building
  performance standard", "LL97", "BERDO", "BEPS", "Energize Denver", "MEES", "Décret
  Tertiaire", "carbon penalty", "emissions fine", "building compliance exposure", "energy
  benchmarking penalty", "EPC", "building decarbonization risk", "carbon fine exposure",
  "BPS penalty", "benchmark compliance", "LL84", "LL87", "retro-commissioning deadline".
---

# Building Performance Standards (BPS) Analysis Skill

## Purpose

Calculate the full regulatory compliance exposure — current penalties, projected penalties through 2035, required capital investment, and available compliance pathways — for any property or portfolio subject to building energy and emissions performance regulations. This skill translates complex multi-jurisdictional regulations into precise dollar figures that can be underwritten, stress-tested, and included in acquisition models.

**The core problem this solves:** BPS regulations have proliferated across 30+ jurisdictions since 2019. Each jurisdiction uses different metrics (EUI, tCO2e/sf, kgCO2e/m², Energy Star score, EPC letter), different penalty formulas, and different deadlines. Missing a filing or misclassifying an occupancy can result in six-figure annual penalties. This skill provides a single authoritative reference and calculation engine.

**Coverage as of July 2026:** 30+ jurisdictions across the US, Canada, UK, and EU. Data current as of July 2026. Flag any regulation with a (verify) note for independent confirmation before using in a legal or financial closing context.

---

## Trigger Detection

Activate this skill when the user:
- Names a specific property address, city, or region and asks about energy compliance, carbon fines, BPS, or benchmarking obligations
- Mentions any regulation by name: LL97, BERDO, BEPS, Energize Denver, CBPS, MEES, Décret Tertiaire, EPBD, GEG, etc.
- Asks about "penalty exposure", "carbon fine", "emissions cost", "compliance cost", or "decarbonization obligation" for a building or portfolio
- Uploads an OM, pro forma, or lease abstract and asks for sustainability or BPS analysis
- Asks about "building benchmarking" deadlines or requirements

If jurisdiction is ambiguous: ask for the property address or city/state before proceeding.

---

## Step 1 — Identify Applicable Jurisdictions

For every property, identify ALL potentially applicable layers:

1. **Municipal ordinance** (city-level: LL97 NYC, BERDO Boston, BEPS DC, etc.)
2. **State/provincial law** (WA CBPS, OR BPS, CO BPS, MA Stretch Code, etc.)
3. **Federal/national** (US: no direct BPS; Canada: NECB model codes; EU: EPBD, ETS2)
4. **Supranational finance regulation** (EU Taxonomy, CSRD — applies to reporting entities, not buildings directly)

**Jurisdiction lookup by city:**

| City | Municipal Layer | State/Province Layer | Notes |
|------|----------------|---------------------|-------|
| New York City, NY | LL97, LL84, LL87, LL33, LL154 | None (NYC-specific) | Most complex US regime |
| Boston, MA | BERDO 2.0 | MA Stretch Code | Tier 1 ≥35k SF active 2025 |
| Cambridge, MA | BEUDO | MA Stretch Code | Net-zero by 2035 for large bldgs |
| Washington, DC | BEPS, DC Benchmarking | None | Cycle 1 enforced 2027 |
| Denver, CO | Energize Denver | CO Statewide BPS | Both apply; use more stringent |
| Seattle, WA | Seattle Tune-Ups (ends 2028), Seattle BEPS | WA CBPS Tier 1/2 | WA CBPS Phase A enforced Jun 2026 |
| Los Angeles, CA | LA EBEWE | AB 802 | No CA statewide performance standard |
| San Francisco, CA | SF EBEO + proposed SF BPS | AB 802 | SF BPS not yet enacted as of Jul 2026 |
| San Jose, CA | San Jose EWBPO | AB 802 | Beyond Benchmarking is enforceable |
| Chicago, IL | Chicago Benchmarking | None | CABO stalled; no performance standard |
| St. Louis, MO | St. Louis BEPS | None | First deadline May 2025 |
| Philadelphia, PA | Philadelphia BEPP | None | Tune-up mandate, not EUI cap |
| Portland, OR | Portland Benchmarking | OR State BPS | OR BPS first enforcement Jun 2028 |
| Baltimore/Annapolis, MD | None | MD BEPS (statewide) | First perf. period 2030 |
| Minneapolis, MN | Minneapolis Benchmarking | MN Statewide Benchmarking | No performance standard |
| Toronto, ON | Toronto EWRB (reporting) | ON EWRB (O. Reg. 506/18) | BEPS (performance caps) developing |
| Vancouver, BC | Vancouver GHG Limits By-law | BC Step Code (new construction) | GHG limits effective 2026, penalties 2027 |
| London/England | MEES (EPC E now; B by 2031 >1,000m²) | SECR (company-level) | Devolved from Scotland |
| Paris + France | Décret Tertiaire (OPERAT) | None | -40% by 2030 vs 2010 baseline |
| Germany | GEG 65% renewable heating | EU-level only | No EPC letter system |
| Netherlands | Office label C (enforced 2023) | EU-level only | A by 2030 proposed |
| EU broadly | EPBD 2024, EU Taxonomy, CSRD/ESRS E1, ETS2 | Member state transposition | EPBD transposed by May 2026 |

---

## Step 2 — Determine Applicability

### Size and Type Thresholds by Jurisdiction

#### US City Programs

| Jurisdiction | Min Size | Building Types | Occupancy Qualifier |
|---|---|---|---|
| NYC LL97 | 25,000 SF gross | All covered types | Per Certificate of Occupancy |
| NYC LL84 (benchmarking) | 25,000 SF gross | All | Annual filing, feeds LL97 |
| NYC LL87 (audit/RCx) | 50,000 SF gross | All | 10-year cycle by tax block |
| Boston BERDO 2.0 | Tier 1: ≥35,000 SF or ≥35 units; Tier 2: ≥20,000 SF or ≥15 units | Non-res + residential | Mixed-use by dominant use |
| Cambridge BEUDO | ≥25,000 SF (non-res, reduction req); ≥100,000 SF (accelerated 2035 target); ≥50 units (res, reporting only) | Non-res + multifamily | Large non-res net-zero by 2035 |
| DC BEPS Cycle 1 | ≥50,000 SF private; ≥10,000 SF DC govt | All types | Private expands to 25k SF in Cycle 2 (2028) |
| DC Benchmarking | ≥10,000 SF private (from May 2026) | All | Annual filing |
| Maryland BEPS | ≥35,000 SF (excluding parking) | Commercial, multifamily, state-owned | Excludes hospitals, K-12, manufacturing, Montgomery County |
| Energize Denver Phase 1 | ≥25,000 SF | Commercial, multifamily, mixed-use | EUI target required |
| Energize Denver Phase 2 | 5,000–24,999 SF | Commercial, multifamily | LED/renewable, not EUI |
| WA CBPS Tier 1 | >50,000 SF non-residential | Non-res, hotel, motel, dormitory | Excludes parking; excludes multifamily |
| WA CBPS Tier 2 | 20,001–50,000 SF non-res; ALL multifamily >20,000 SF | Multifamily (any size >20k SF); smaller non-res | Benchmarking only |
| OR BPS Tier 1 | ≥35,000 SF (non-res, hotel, motel) | Non-res, hotel, motel | First enforcement Jun 2028 |
| OR BPS Tier 2-Special | ≥35,000 SF multifamily, hospitals, schools, senior care | Multifamily/healthcare/edu | Distinct compliance path |
| OR BPS Tier 2-Regular | 20,000–35,000 SF (hotel, non-res) | Hotel, non-res | Benchmarking + compare |
| LA EBEWE | ≥20,000 SF | Commercial, industrial, multifamily (17+ utility accounts), city-owned | A/RCx every 5 years |
| SF EBEO | ≥10,000 SF non-res; ≥50,000 SF multifamily | Non-res + multifamily | Renewable electricity mandate for 50k+ SF |
| San Jose EWBPO | ≥20,000 SF | Residential + non-residential | Beyond Benchmarking every 5 years |
| Chicago Benchmarking | ≥50,000 SF | Commercial, institutional, residential | Disclosure only |
| St. Louis BEPS | ≥50,000 SF | Municipal, commercial, institutional, multifamily | EUI targets enforced May 2025 |
| Philadelphia BEPP | ≥50,000 SF non-res | Non-residential commercial | Tune-up mandate; 200k+ SF first (2026) |
| CO Statewide BPS | ≥50,000 SF | Commercial, multifamily, public | GHG reduction from 2021 baseline |

#### Canadian Programs

| Jurisdiction | Min Size | Building Types | Notes |
|---|---|---|---|
| Ontario EWRB (O. Reg. 506/18) | ≥50,000 SF (4,645 m²) provincial; ≥10,000 SF Toronto (from 2027) | Commercial, MURB >10 units, industrial | Reporting only; BEPS developing |
| Toronto Green Standard v4 | All mid/high-rise new construction | New construction only | Legally contested post-Bill 98 (May 2026) |
| Vancouver GHG Limits By-law | ≥9,290 m² (100,000 SF) for GHGI limits | Commercial D+E, multifamily ≥4 storeys | GHG limits 2026; penalties 2027 |
| BC Step Code / Zero Carbon | All new Part 3 buildings ≥600 m² or ≥4 storeys | New construction only | Zero Carbon EL-1 mandatory Mar 2025 |
| Quebec (Bill 41 / NECB 2020) | Existing: ≥5,000 m² or ≥50 units + institutional; New: ≥600 m² Part 3 | All | Mandatory disclosure from 2027 |

#### UK / EU Programs

| Jurisdiction | Min Size | Building Types | Notes |
|---|---|---|---|
| UK MEES (E&W) | All leased non-domestic; EPC B applies to >1,000 m² | Privately rented non-domestic | EPC E now; B by 2031 for >1,000 m² |
| Scotland AEPNDB | >1,000 m² GIA | Non-domestic | Action Plan at sale/letting |
| UK SECR | Company-level (>250 employees OR >£36M turnover OR >£18M balance sheet) | Any company meeting thresholds | Directors' Report, not building-level |
| EU Taxonomy | No building floor area threshold | All real estate activities | EPC A or top-15% for acquisition |
| CSRD / ESRS E1 | >250 employees OR >€40M revenue OR >€20M balance sheet | Reporting company, all building types | EPC portfolio breakdown required |
| EPBD 2024 | Member state MEPS cover worst 16% of non-res floor area by 2030 | All building types | Transposition deadline May 2026 |
| ETS2 | No building threshold — upstream fuel distributor obligation | All fossil-fuel-heated buildings (indirect) | Cost reaches buildings via fuel prices 2027 |
| Germany GEG | All buildings with new heating installations | Residential + commercial | 65% renewable heating from Jan 2024 |
| Netherlands Office Label | Office buildings ≥100 m² | Offices only | Label C enforced; A by 2030 (proposed) |
| France Décret Tertiaire | Tertiary activities ≥1,000 m² usable floor area | Offices, retail, hotels, restaurants, schools, hospitals | Annual OPERAT filing; -40% by 2030 |

---

## Step 3 — How Compliance is Measured (by Regulation)

### NYC Local Law 97 (LL97)

**Metric:** Annual GHG emissions in tCO2e per gross SF per year, by occupancy group per Certificate of Occupancy.

**Emission Calculation:**
```
Annual Building Emissions (tCO2e) =
  (Electricity kWh × 0.000288962 tCO2e/kWh)
+ (Natural gas therms × 0.00005311 tCO2e/therm)
+ (ConEd steam klbs × 0.04493 tCO2e/klb)
+ (Other fuels per DOB table 1 RCNY §103-14)
```
Note: The electricity emission factor (~0.000288962 tCO2e/kWh) is updated annually by NYC DOB.

**Annual Building Cap (tCO2e):**
```
Annual Cap = Σ [Intensity Factor (tCO2e/SF/yr) × Gross Floor Area (SF)]
             for each occupancy group
```

**Intensity Factors by Occupancy Group:**

| Occupancy | 2024–2029 (tCO2e/SF/yr) | 2030–2034 (tCO2e/SF/yr) |
|---|---|---|
| A — Assembly | 0.01074 | 0.00420 |
| B — Business (general office, civic) | 0.00846 | 0.00453 |
| B — Business (civic emergency, nonproduction lab, ambulatory healthcare) + H + I-2 + I-3 | 0.02381 | 0.01193 (verify against DOB Table 320.7.6b) |
| E — Educational + I-4 | 0.00758 | 0.00344 |
| F — Factory | 0.00574 | 0.00167 |
| I-1 — Institutional (supervised env.) | 0.01138 | 0.00598 |
| M — Mercantile (retail) | 0.01181 | 0.00403 |
| R-1 — Hotel | 0.00987 | 0.00526 |
| R-2 — Multifamily residential | 0.00675 | 0.00407 |
| S — Storage (S-1 and S-2 combined) + U — Utility | 0.00426 | 0.00110 |

Note: There is no occupancy group "D" in NYC Building Code or LL97. S-1 and S-2 are combined as "S".

**Example Calculation — 100,000 SF General Office (B-general, 2024–2029):**
```
Cap = 0.00846 × 100,000 = 846 tCO2e/yr
If actual emissions = 1,000 tCO2e/yr
Excess = 154 tCO2e
Annual penalty = 154 × $268 = $41,272
```

**Mixed-Use Buildings:** Cap = Σ(intensity_i × area_i) for each occupancy zone.

---

### Boston BERDO 2.0

**Metric:** Absolute GHG intensity in kgCO2e/SF/yr, by building use type.

**Emissions Standard Table (kgCO2e/SF/yr):**

| Building Use | 2025–2029 | 2030–2034 | 2035–2039 | 2040–2044 | 2045–2049 | 2050+ |
|---|---|---|---|---|---|---|
| Office | 5.3 | 3.2 | 2.4 | 1.6 | 0.8 | 0 |
| Multifamily housing | 4.1 | 2.4 | 1.8 | 1.1 | 0.6 | 0 |
| Lodging (Hotel) | 5.8 | 3.7 | 2.7 | 1.8 | 0.9 | 0 |
| Retail | 7.1 | 3.4 | 2.4 | 1.5 | 0.7 | 0 |
| Technology/Science (Lab, Data Center) | 19.2 | 11.1 | 7.8 | 5.1 | 2.5 | 0 |
| Healthcare | 15.4 | 10.0 | 7.4 | 4.9 | 2.4 | 0 |
| College/University | 10.2 | 5.3 | 3.8 | 2.5 | 1.2 | 0 |
| Education (K-12, Daycare) | 3.9 | 2.4 | 1.8 | 1.2 | 0.6 | 0 |
| Assembly (Museum, Theater, Arena, Gym, Worship) | 7.8 | 4.6 | 3.3 | 2.1 | 1.1 | 0 |
| Food Sales & Service (Restaurant, Supermarket) | 17.4 | 10.9 | 8.0 | 5.4 | 2.7 | 0 |
| Services (Library, Courthouse, Fire/Police) | 7.5 | 4.5 | 3.3 | 2.2 | 1.1 | 0 |
| Storage (Warehouse, Parking, Distribution) | 5.4 | 2.8 | 1.8 | 1.0 | 0.4 | 0 |
| Manufacturing/Industrial | 23.9 | 15.3 | 10.9 | 6.7 | 3.2 | 0 |

**Grid Emission Factors (Appendix B, used to convert electricity kWh to kgCO2e):**
- 2025: 249 kg/MWh (0.249 kgCO2e/kWh)
- 2050: 150 kg/MWh (0.150 kgCO2e/kWh)
Factors decline annually per official BERDO Appendix B.

**Mixed-use buildings:** Blended standard weighted by SF of each use (each use must be ≥10% of SF or ≥10% of energy/emissions to qualify for blending).

---

### DC Building Energy Performance Standards (BEPS)

**Metric:** Energy Star score (primary for eligible types) OR Site EUI adjusted to current year (most common).

**Cycle 1 Standard Targets (2021–2026):**

| Property Type | Energy Star Score Target | Source EUI Target |
|---|---|---|
| Hospital | 50 | 426.9 kBtu/SF/yr |
| Hotel | 54 | 183.9 kBtu/SF/yr |
| K-12 School | 36 | 139 kBtu/SF/yr |
| Multifamily | 66 | 110.7 kBtu/SF/yr |
| Office | 71 | 153.7 kBtu/SF/yr |
| College/University | Custom per campus | — |

**Performance Pathway alternative:** 20% reduction in site EUI from 2018–2019 baseline by December 31, 2026.

---

### Maryland BEPS (COMAR 26.28)

**Metric:** Net direct GHG emissions (kgCO2e/SF) — onsite fuel combustion only (natural gas, fuel oil). Electricity emissions are excluded from current standards.

**Multifamily Targets (confirmed):**

| Period | Target |
|---|---|
| 2030–2034 | 0.82 kgCO2e/SF/yr |
| 2035–2039 | 0.41 kgCO2e/SF/yr |
| 2040+ | 0 kgCO2e/SF/yr (net-zero direct GHG) |

Note: Building-type-specific targets for office, retail, hotel, and others exist in COMAR 26.28 but were not fully published in accessible sources as of July 2026. (verify against full COMAR 26.28 text or contact BEPS.MDE@maryland.gov)

---

### Energize Denver — Phase 1 (≥25,000 SF)

**Metric:** Site EUI (weather-normalized, kBtu/SF/yr) from 2019 ENERGY STAR Portfolio Manager baseline.

**EUI Targets (kBtu/SF/yr) — Final Targets:**

| Building Type | Final EUI Target |
|---|---|
| Office | 48.3 |
| Hotel | 61.1 |
| Multifamily | 44.2 |
| Retail Store | 43.5 |
| Hospital | 165.2 |
| Fast Food Restaurant | 311.3 |
| Aquarium, Convention Center, Museum, Ice Rink | 30% reduction from 2019 baseline |

**Interim target:** 30% reduction from 2019 baseline by 2030 (standard timeline) or 2032 (extended timeline). Buildings may not be required to reduce more than 42%.

---

### Washington State CBPS — Tier 1 (>50,000 SF non-residential)

**Metric:** Weather-Normalized Energy Use Intensity (WNEUI) in kBtu/SF/yr per WAC 194-50, based on ASHRAE Standard 100-2018 with WA amendments.

**EUI Targets by Building Type — WAC 194-50-150 Table 7-2a (Climate Zone 4C / 5B):**

| Building Type | CZ 4C Target | CZ 5B Target |
|---|---|---|
| Adult Education | 49 | 51 |
| College/University | 102 | 102 |
| K-12 Elementary/Middle | 49 | 50 |
| K-12 High School | 48 | 49 |
| Preschool/Daycare | 59 | 59 |
| Convention Center | 50 | 52 |
| Fitness Center | 73 | 78 |
| Ice/Curling Rink | 73 | 78 |
| Indoor Arena | 67 | 70 |
| Movie Theater | 67 | 70 |
| Museum | 67 | 70 |
| Performing Arts | 55 | 59 |
| Swimming Pool | 73 | 78 |
| Fast Food Restaurant | 427 | 454 |
| Full-Service Restaurant/Bar | 361 | 378 |
| Grocery/Food Market | 191 | 198 |
| Convenience Store w/Gas | 260 | 269 |
| Convenience Store w/o Gas | 244 | 253 |
| Hospital (General Medical/Surgical) | 69 | 72 |
| Medical Office | 40 | 41 |
| Senior Care Community | 56 | 58 |
| Hotel/Motel | 59 | 61 |
| Multifamily Housing / Dormitory | 56 | 58 |
| Admin/Professional Office | 40 | 41 |
| Bank/Financial | 69 | 71 |
| Government Office | 49 | 50 |
| Retail Store / Enclosed Mall / Strip Mall | 49 | 50 |
| Supermarket/Grocery Store | 191 | 198 |
| Wholesale Club/Supercenter | 49 | 50 |
| Self-Storage | 20 | 20 |
| Distribution Center | 49 | 50 |
| Nonrefrigerated Warehouse | 38 | 38 |
| Refrigerated Warehouse | 101 | 101 |

Note: Office target is 40/41 kBtu/SF/yr per official WAC 194-50-150. Some industry summaries cite ~63 kBtu/SF/yr, which appears to be the national ASHRAE 100-2018 pre-WA-adjustment figure. Always use the WAC official value. (verify against WAC 194-50-150 Table 7-2a directly)

Most of western Washington (including Seattle) is Climate Zone 4C. Eastern Washington is primarily Climate Zone 5B.

---

### UK MEES (Minimum Energy Efficiency Standards)

**Metric:** EPC rating (A through G scale based on primary energy demand per m²/yr).

**Current requirement (2026):** EPC E or better — F/G-rated non-domestic lettings are unlawful.

**Proposed trajectory:**
- EPC B by 2031 for buildings >1,000 m² (confirmed in June 2026 government interim response)
- Buildings ≤1,000 m² remain at EPC E with no further escalation confirmed as of July 2026

**EPC bands by primary energy demand (approximate; varies by building type and assessment method):**
- A: ≤25 kWh/m²/yr
- B: 26–50 kWh/m²/yr
- C: 51–75 kWh/m²/yr
- D: 76–100 kWh/m²/yr
- E: 101–125 kWh/m²/yr
- F: 126–150 kWh/m²/yr
- G: >150 kWh/m²/yr
(verify exact band boundaries for specific commercial assessment tool and property type)

---

### France — Décret Tertiaire (DEET)

**Metric:** Final energy consumption (kWh/m²/yr) — percentage reduction versus a 2010 reference year baseline, OR compliance with ADEME-published absolute consumption targets by building activity type and climate zone.

**Reduction Targets:**
- **By December 31, 2030:** −40% from 2010 baseline
- **By December 31, 2040:** −50% from 2010 baseline
- **By December 31, 2050:** −60% from 2010 baseline

**Absolute Targets (valeurs absolues):** Published by ADEME per building activity type (office, retail, hotel, education, etc.) and French climate zone — use when no valid 2010 baseline can be established. (verify current valeurs absolues table from ADEME/OPERAT for each property type)

---

## Step 4 — Penalty Calculation

### Penalty Formulas by Regulation

#### NYC LL97

```
Annual Penalty = MAX(0, Actual tCO2e − Building Cap tCO2e) × $268/tCO2e
```
No statutory maximum. Accrues each compliance year. First compliance year: 2024.

**Example — 100,000 SF Multifamily (R-2), 2030–2034:**
```
Cap = 0.00407 × 100,000 = 407 tCO2e/yr
If actual = 600 tCO2e: Penalty = 193 × $268 = $51,724/yr
```

**AHRF Offset (affordable housing only):** Purchase at $268/tCO2e; capped at 10% of annual building emissions limit.
**REC credit:** Offsets electricity emissions only; blocked for good-faith-effort filers in 2024–2029.

---

#### Boston BERDO 2.0

**Three violation types:**

1. **Reporting non-compliance:**
   - Tier 1 (≥35,000 SF / ≥35 units / ≥100,000 SF parcel aggregate): $300/day after 30-day cure
   - Tier 2 (20,000–34,999 SF / 15–34 units): $150/day after 30-day cure

2. **Emissions standard exceedance:**
   - Tier 1: $1,000/day (no cap; full year = up to $365,000)
   - Tier 2: $300/day
   - Cure period: 30 days from Notice of Violation

3. **Inaccurate reporting (third-party verification finds discrepancy):** $1,000–$5,000 per instance at Review Board discretion.

**Alternative Compliance Payment (ACP):** $234/tCO2e above limit. Paid into the Equitable Emissions Investment Fund. Not a fine — a compliance mechanism. Rate reviewed every 5 years.

```
ACP Payment = (Actual kgCO2e/SF/yr − Standard kgCO2e/SF/yr) × Gross SF × $0.234/kg
            = Excess kgCO2e × $234/tonne
```

**Example — 50,000 SF Office building, 2025 data:**
```
Standard: 5.3 kgCO2e/SF/yr × 50,000 SF = 265,000 kgCO2e = 265 tCO2e
If actual = 350 tCO2e: Excess = 85 tCO2e
ACP = 85 × $234 = $19,890
OR fine exposure: up to $1,000/day = $365,000/yr
```

---

#### DC BEPS (Cycle 1)

```
Performance Penalty = $10.00/SF × Gross SF × (1 − Actual Progress Fraction)
Maximum = $7,500,000 per property
```

Progress fraction = actual EUI improvement ÷ required EUI improvement (linear interpolation).

**Civil infractions (independent of performance):**
- $2,000 for health/safety threat
- $1,000 for pathway non-submission
- $500 for missing required documents

**Benchmarking non-compliance:** Up to $100/day after 30-day post-Notice of Violation period.

**Example — 100,000 SF Office, zero progress:**
```
Penalty = $10.00 × 100,000 × 1.0 = $1,000,000
```
**Example — 50% progress made:**
```
Penalty = $10.00 × 100,000 × 0.5 = $500,000
```

---

#### Maryland BEPS

```
ACF (Alternative Compliance Fee) = Excess tCO2e × $230/tCO2e (2030, in 2020 dollars)
                                   + $4/tCO2e per year after 2030
```

First compliance period begins January 1, 2030. Net-zero direct GHG required by 2040.

---

#### Energize Denver — Phase 1

**Standard timeline (2030 final target):**
```
Annual Penalty = $0.35/kBtu × (Actual EUI − Target EUI) × Gross SF
```
If within 5% of target: reduced rate applies; corrective action plan option.

**Extended timeline (2032 final target, opt-in):**
```
Annual Penalty = $0.70/kBtu × (Actual EUI − Target EUI) × Gross SF
```

**Maintenance penalty (after meeting target):**
```
Maintenance Penalty = $0.05/kBtu × (Actual EUI − Target EUI) × Gross SF
```

**Never benchmarked / no pre-2019 data:**
```
Flat Penalty = $10.00/SF × Gross SF (one-time)
```

**Benchmarking non-submission:** $2,000/year.

**Example — 100,000 SF Office, 2030 standard timeline, 20 kBtu above target:**
```
Penalty = $0.35 × 20 × 100,000 = $700,000/yr
```

---

#### Washington State CBPS — Tier 1

```
Base penalty = $5,000
Annual accrual = $1.00/SF/yr × Gross SF (accrues daily for up to 18 months)
Maximum = $5,000 + $1.50/SF
Mitigated (if non-compliance mitigation plan filed) = 30% of base + $0.20/SF/yr
```

**Example — 100,000 SF Office, full 18-month non-compliance, no mitigation plan:**
```
Max penalty = $5,000 + ($1.50 × 100,000) = $155,000
```

---

#### Washington State CBPS — Tier 2

```
Flat penalty = $0.30/SF per compliance cycle (not annual; per compliance period)
```

---

#### Oregon BPS

```
Full non-compliance: $5,000 + $1.00/SF/yr
Reporting failure only (EUI exceeded): $1,500 + $0.20/SF/yr
Portland municipal non-compliance: up to $500 per 90-day period
```

**Example — 200,000 SF Building, full non-compliance:**
```
Annual penalty = $5,000 + ($1.00 × 200,000) = $205,000/yr
```

---

#### LA EBEWE

**Base fine:** $202 per building per violation period.
**Late fee escalation:** 250% of fine if unpaid after 30 days = $202 × 3.5 = **$707** per violation period after 30-day late escalation. (verify: some sources describe this as per-day; confirm from LAMC Division 97)

---

#### San Francisco EBEO

```
Buildings 10,000–49,999 SF: $50/day up to a maximum of $1,250
Buildings 50,000+ SF: $100/day up to a maximum of $2,500
```

---

#### San Jose EWBPO

```
$25–$50/day for annual benchmarking non-compliance
Maximum: $5,000/calendar year
```

---

#### St. Louis BEPS

**Written warning first. Then after 60-day cure period:**
```
$50–$200/day fine, capped at $1,000/year
Denial of new occupancy permits for non-compliant properties
```

---

#### Philadelphia BEPP

**Benchmarking non-compliance:**
```
$300 first month + $100/day thereafter
```

**BEPP violation (tune-up not completed):**
```
$2,000 initial fine + $500/day beginning 30 days after tune-up deadline
```

---

#### Colorado Statewide BPS

**Benchmarking non-compliance:** $500 first occurrence; $2,000 each subsequent occurrence.
**Performance non-compliance:** Monthly penalties from June 2027. (verify per-unit rate from AQCC Rule)

---

#### UK MEES

**Breach <3 months:**
```
Fine = 10% of property's rateable value
Minimum: £5,000 | Maximum: £50,000
+ publication penalty (public register listing)
```

**Breach ≥3 months:**
```
Fine = 20% of property's rateable value
Minimum: £10,000 | Maximum: £150,000
+ publication penalty
```

---

#### France — Décret Tertiaire

**Stage 1 — Name-and-shame:** Non-compliant entities listed on public government website.

**Stage 2 — Administrative fine:**
```
Natural person (individual owner): up to €1,500/building/year
Legal entity (corporate): up to €7,500/building/year
```

No annual cap on total portfolio exposure.

**Example — 10-building portfolio, all non-compliant, legal entity:**
```
Maximum annual fine = 10 × €7,500 = €75,000/year
```

---

#### Vancouver GHG Limits By-law

**Reporting violation (failure to file, incomplete, inaccurate):**
```
Flat fine: $500 per violation
```

**Emissions exceedance (from 2027):**
```
Carbon Emissions Operating Permit fee = $350/tonne CO2e above annual GHGI limit
```

**GHGI Limits (effective 2026):**
- Office (D Major Occupancy): ≤25 kg CO2e/m²/yr
- Retail (E Major Occupancy): ≤14 kg CO2e/m²/yr
- 2040+: 0 kg CO2e/m²/yr (zero-emission)

---

#### Netherlands Office Energy Label

**Non-compliance with C-label mandate:**
- Local authority issues closure order (cessation of office use) — ultimate sanction
- Administrative penalty charge (dwangsom) set per case by municipality
- No published national fixed fine schedule; enforcement escalates to closure (verify current municipality-specific fine schedules)

---

### Penalty Exposure Summary Calculation (for a given property)

For each applicable regulation, calculate:

```
Current Annual Exposure (2025-2026):
  = Sum of penalties for current non-compliance across all applicable regulations

Near-Term Exposure (2030):
  = Sum of penalties if building still non-compliant at 2030 targets
  Note: NYC LL97 2030–2034 limits affect ~57% of buildings; BERDO tightens every 5 years

Medium-Term Exposure (2035):
  = Sum of penalties at 2035 regulatory targets
  Note: Boston BERDO 2035–2039 standards roughly halve from 2030–2034 levels

Long-Term Exposure (2040–2050):
  = Sum of penalties as net-zero targets take effect across all jurisdictions
```

---

## Step 5 — Compliance Pathways and Cost

### NYC LL97 Compliance Pathways

1. **Operational Optimization** — Controls tuning, recommissioning, load elimination. Typical reduction: 10–20%. Lowest cost; implement first.
2. **Equipment Upgrades** — High-efficiency HVAC, heat pumps, LED retrofits, envelope improvements. Eligible for Con Edison and NYSERDA incentives.
3. **Fuel Switching / Electrification** — Converting from fossil fuels to electric/hybrid heat. Dominant lever for 2030 compliance. Grid upgrade lead time: 18–36 months through Con Edison.
4. **Class I RECs** — Offset electricity emissions only; blocked for good-faith-effort filers in 2024–2029 period.
5. **AHRF Offsets** — Affordable Housing Reinvestment Fund; capped at 10% of annual building emissions limit; $268/tCO2e.
6. **Beneficial Electrification Credit** — Early installation of qualifying electric equipment before compliance deadline.
7. **Distributed Energy Resources** — Onsite/offsite solar, battery storage; deductions available.
8. **Good Faith Effort Pathway (2024–2029 only):** Three prerequisites must ALL be met:
   - (a) Submit LL97 annual compliance report
   - (b) File LL84 benchmarking for same year
   - (c) Document LL88 lighting upgrade and sub-metering completion
   PLUS at least one of: approved alteration permit with contractor agreement; approved electrical alteration filing; decarbonization plan filed with DOB; critical facility operational constraint documentation.

---

### Boston BERDO 2.0 Compliance Pathways

1. **Direct building retrofits** — Electrification, insulation, envelope improvements.
2. **On-site solar generation** — Boston or community solar.
3. **Boston Community Choice Electricity (CCE) Green 100 plan** — 100% renewable.
4. **MA Class I RECs** — Generated within 12 months before or during compliance year; retired within 6 months of compliance year end. For 2025: eligible RECs generated Jan 2024–Jun 2026.
5. **Alternative Compliance Payment (ACP)** — $234/tCO2e above limit; paid into Equitable Emissions Investment Fund.
6. **Blended Emissions Standard** — Mixed-use buildings; each use ≥10% of SF or 10% of energy/emissions.
7. **Building Portfolio** — Multiple buildings under same owner; allows averaging; requires Review Board approval.
8. **Individual Compliance Schedule** — Alternative timeline; must achieve 50% reduction by 2030, 100% by 2050 from baseline; Review Board approval required.
9. **Hardship Compliance Plan** — Short-term (1–3 yr) or long-term (4+ yr); financial/contractual/technical hardship qualifies.

---

### DC BEPS Compliance Pathways (Cycle 1)

1. **Standard Target Pathway** — Achieve Energy Star score or site EUI target for property type.
2. **Performance Pathway** — Achieve 20% site EUI reduction from 2018–2019 baseline.
3. **Prescriptive Pathway (Cycle 1 only)** — Complete energy audit, submit implementation action plan, verify completion.
4. **Alternative Compliance Pathway** — DOEE-approved custom plan demonstrating comparable savings.
5. **Trajectory Pathway (Cycle 2+, 2028)** — Building-specific long-term improvement targets.
Delays up to 3 years available for major renovations, financial distress, vacant buildings, pending demolition. COVID-adjusted delays no longer count toward 3-year maximum (BEPS Amendment Act of 2024).

---

### Energize Denver Compliance Pathways

1. **Meet EUI target outright.**
2. **Corrective Action Plan** — Available if within 5% of target.
3. **Timeline Extension** — Submit with 2025 benchmarking report; shifts to extended timeline (2032 final, higher penalty rate $0.70/kBtu).
4. **Renewable Energy Credits** — Used to offset EUI.
5. **Target Adjustment** — For inaccurate 2019 baseline or non-representative operating years.
HOAs: greater flexibility introduced under April 2025 rules update.

---

### Washington CBPS Tier 1 Compliance Pathways

1. **Meet EUI target** — WNEUI ≤ EUIt (primary path).
2. **Investment Criteria Pathway** — Perform energy audit and implement all cost-effective measures; available if EUI target cannot be met.
Both paths require: O&M program, energy maintenance plan, designated energy manager, annual ENERGY STAR Portfolio Manager benchmarking.
**Early Adopter Incentive:** $0.85/SF for Tier 1 buildings that adopt O&M program early.

---

### UK MEES Exemptions and Compliance

**Valid exemptions (must be registered on the PRS Exemptions Register):**
- 7-year simple payback test: all relevant improvements fail to pay back within 7 years
- Third-party consent refused by tenant, lender, or superior landlord
- Wall/roof/floor improvements would devalue the property by ≥5%
- All relevant improvements already installed
- Temporary buildings; buildings used <4 months/year
- Listed buildings where compliance would unacceptably alter character

**Compliance upgrade pathway:**
1. Obtain a current EPC from an accredited assessor.
2. Identify which measures improve the EPC band.
3. Implement (insulation, HVAC, lighting, controls).
4. Obtain a new EPC demonstrating E or better (current), B or better (by 2031 for >1,000 m²).
5. Register on landlord portal.

---

### France Décret Tertiaire Compliance Pathways

1. **Energy reduction pathway** — Achieve −40% by 2030 vs 2010 baseline via retrofits, controls optimization, behavioral change.
2. **Absolute consumption target** — Comply with ADEME-published kWh/m²/yr targets by building type if no valid 2010 baseline.
3. **Modulation (target adjustment)** — Formally document constraints that make the standard target unreachable: heritage building, atypical occupancy intensity, activity change. Must apply through OPERAT with supporting evidence.
4. **Annual OPERAT submission** — Mandatory by September 30 each year; failure triggers immediate name-and-shame exposure.

---

## Step 6 — Key Deadlines Reference

### 2025 Active Deadlines

| Deadline | Regulation | What is Due |
|---|---|---|
| May 1, 2025 | NYC LL84 | Annual benchmarking submission (2024 data) |
| May 1, 2025 | NYC LL97 | Annual compliance report (2024 data) — extended to Dec 31, 2025 for most buildings (verify current DOB Service Notice) |
| May 1, 2025 | DC Benchmarking | Annual benchmarking (2024 data, formerly April 1) |
| May 4, 2025 | St. Louis BEPS | First compliance deadline for standard buildings |
| May 15, 2025 | Boston BERDO 2.0 | Annual report for 2024 — extended to Aug 15, 2026 for 2025 data |
| June 1, 2025 | MN Statewide | First benchmarking for 100,000+ SF buildings |
| June 1, 2025 | WA CBPS | Annual benchmarking (2024 data) |
| June 1, 2025 | Energize Denver | Annual benchmarking + timeline election window |
| June 1, 2025 | OR BPS | Annual benchmarking |
| June 1, 2025 | CO Statewide BPS | Annual benchmarking |
| June 1, 2025 | AB 802 (CA) | Annual benchmarking (2024 data) |
| June 30, 2025 | Honolulu | Annual benchmarking for 25,000–50,000 SF buildings (first year) |
| July 1, 2025 | NJ Clean Energy Act | Annual benchmarking (2024 data) |
| July 1, 2025 | Ontario EWRB | Annual reporting (2024 data) |
| July 1, 2025 | MD BEPS | Annual benchmarking (2024 data) |
| July 2, 2025 | Toronto EWRB | Annual reporting (2024 data) |
| September 1, 2025 | MD BEPS | Initial benchmarking report (first year, extended deadline) |
| September 15, 2025 | New Orleans | First benchmarking for buildings ≥100,000 SF |
| September 30, 2025 | Décret Tertiaire | Annual OPERAT declaration (2024 energy consumption) |
| December 31, 2025 | NYC LL87 | Audit/RCx for buildings with tax block last digit 5 |
| December 31, 2025 | Atlanta CBEEO | Annual audit deadline for buildings with Atlanta Building ID ending in 5 |
| December 31, 2025 | NYC LL97 | Extended compliance report deadline (most buildings) — verify against current DOB notice |

### 2026 Key Deadlines

| Deadline | Regulation | What is Due |
|---|---|---|
| January 1, 2026 | Germany GEG | 65% renewable heating rule in effect for all new installations in cities with completed heat plans |
| May 1, 2026 | NYC LL84 | Annual benchmarking (2025 data) |
| May 1, 2026 | Cambridge BEUDO | Annual benchmarking (2025 data) |
| May 1, 2026 | DC Benchmarking | First filing for buildings 10,000–25,000 SF (new threshold); 2025 data |
| May 15, 2026 | Boston BERDO | Annual report for 2025 data — extended to Aug 15, 2026 |
| June 1, 2026 | WA CBPS Phase A | **EUI compliance deadline for buildings >220,000 SF** (first enforcement) |
| June 1, 2026 | Energize Denver | Third-party data verification (first year) |
| June 1, 2026 | MD BEPS | Third-party verified benchmarking (2025 data) |
| June 1, 2026 | OR BPS | Annual benchmarking |
| June 30, 2026 | NYC LL97 | Filing fee extension application deadline ($60 fee; allows submission to Aug 29, 2026) |
| August 1, 2026 | CA SB48 Study | CEC final BPS study report due |
| August 15, 2026 | Boston BERDO | Annual report 2025 (extended deadline) |
| September 1, 2026 | Boston BERDO | Deadline to apply for Building Portfolio or Individual Compliance Schedule for 2026 relief |
| September 15, 2026 | New Orleans | First benchmarking for 20,000–99,999 SF buildings |
| September 29, 2026 | CSRD Phase 2 | Large EU companies file FY2025 ESRS E1 disclosures |
| September 30, 2026 | Décret Tertiaire | Annual OPERAT declaration (2025 data) |
| October 31, 2026 | Boston BERDO | MA Class I REC purchase deadline for 2025 compliance |
| December 31, 2026 | DC BEPS Cycle 1 | **Compliance deadline — buildings that have not completed their pathway by Dec 31, 2026 face enforcement assessment in 2027** |
| December 31, 2026 | NYC LL87 | Audit/RCx for buildings with tax block last digit 6 |

### 2027–2032 Major Milestones

| Date | Regulation | Milestone |
|---|---|---|
| Jan 1, 2027 | Vancouver GHG | Penalty fees for GHGI exceedances begin ($350/tCO2e above limit) |
| Jan 1, 2027 | ETS2 | EU ETS2 trading begins; fuel costs rise for building heating |
| Jun 1, 2027 | WA CBPS Phase B | EUI compliance deadline for buildings 90,001–220,000 SF |
| Jun 1, 2027 | CO Statewide BPS | Monthly performance penalties begin for non-compliant buildings |
| Jul 1, 2027 | WA CBPS Tier 2 | Benchmarking compliance deadline for 20,001–50,000 SF non-res + multifamily >20,000 SF |
| 2027 | DC BEPS | Enforcement assessments issued for Cycle 1 non-compliant buildings |
| 2027 | Toronto EWRB | Phase 2 reporting (10,000–49,999 SF Toronto) begins |
| 2027 Q1 | Toronto BEPS | Council reconsideration of BEPS performance standard framework (expected) |
| 2027 | Quebec | Mandatory environmental performance disclosure for large existing buildings begins |
| Jun 1, 2028 | WA CBPS Phase C | EUI compliance deadline for buildings 50,001–90,000 SF |
| Jun 1, 2028 | OR BPS Tier 1 | First compliance deadline — buildings ≥200,000 SF |
| Jul 2, 2028 | NYC LL154 | Fossil fuel prohibition effective for all remaining occupancies (all heights) |
| Jul 1, 2028 | OR BPS Tier 2 | Initial data submission deadline |
| 2028 | DC BEPS Cycle 2 | Begins — expands to ≥25,000 SF private buildings |
| Jan 1, 2030 | NYC LL97 | **2030–2034 limits take effect — ~57% of NYC buildings projected non-compliant** |
| Dec 31, 2030 | Boston BERDO | 2030–2034 standards begin (tighter; Tier 2 buildings join) |
| Dec 31, 2030 | Cambridge BEUDO | Medium non-residential (25,000–99,999 SF) begin reductions |
| Jan 1, 2030 | MD BEPS | **First performance standard compliance period begins** |
| Dec 31, 2030 | Energize Denver | Final EUI target deadline (standard timeline buildings) |
| Dec 31, 2030 | EU EPBD | MEPS worst-performing 16% of non-res floor area must be renovated |
| Dec 31, 2030 | SF EBEO | Renewable electricity mandate for 50,000+ SF buildings |
| Dec 31, 2030 | France Décret Tertiaire | **−40% energy consumption target** |
| Jan 1, 2030 | Netherlands | Office label A target (proposed — formal legislation pending as of Jul 2026) |
| Dec 31, 2031 | UK MEES | EPC B required for buildings >1,000 m² in England/Wales (proposed) |
| Dec 31, 2032 | Energize Denver | Final EUI target deadline (extended timeline opt-in buildings) |

---

## Step 7 — Output: Structured Compliance Report

When this skill produces a BPS analysis, output the following structured report:

### Required Output Fields

```
PROPERTY INFORMATION
  Property address:
  Gross floor area (SF / m²):
  Primary occupancy / use type:
  Secondary occupancies (if mixed-use):
  Year built:
  Current heating fuel(s):
  Current energy benchmarking status (Energy Star score, EUI if known):

APPLICABLE REGULATIONS
  [List every applicable regulation across all jurisdictions with:]
    - Regulation name and jurisdiction
    - Size/type qualification basis
    - Status: CURRENTLY APPLICABLE / UPCOMING / NOT APPLICABLE
    - Enforcement start date for this property

CURRENT COMPLIANCE STATUS (2025–2026)
  For each applicable regulation:
    - Current compliance: COMPLIANT / NON-COMPLIANT / UNKNOWN (benchmarking required)
    - If non-compliant: current annual penalty exposure (calculated from formula)
    - Filing deadlines missed (if any)

PROJECTED PENALTY EXPOSURE
  2025 scenario:  $___/year
  2030 scenario:  $___/year (if no action taken)
  2035 scenario:  $___/year (if no action taken)
  Notes on which tightening steps drive the largest increases

COMPLIANCE PATHWAYS
  For each regulation, ranked by cost-effectiveness:
    Pathway 1 — [name]: Estimated cost $___, Expected reduction ___, Timeline ___
    Pathway 2 — [name]: Estimated cost $___, Expected reduction ___, Timeline ___
    Alternative Compliance Payment / ACP: $___/yr at current excess
  Recommended action sequence:
    Immediate (0–12 months): [actions]
    Near-term (1–3 years): [actions]
    Long-term (3–10 years): [actions]

KEY UPCOMING DEADLINES
  [Sorted chronologically — next 5 deadlines with dates and actions required]

INCENTIVES AND OFFSETS
  [List applicable incentive programs, REC options, AHRF, ACP for each jurisdiction]

DATA GAPS AND VERIFICATION FLAGS
  [Any numbers marked (verify) or data needed to complete the analysis]
  [If benchmarking data not available, note this as the first required action]
```

---

## Exemptions Quick Reference

### NYC LL97 Article 321 (reduced pathway)
Buildings with ≥35% rent-regulated units; NYCHA developments; HDFC co-ops; houses of worship under NYC Admin Code §420-a; city-owned buildings. These follow a prescriptive pathway: complete 13 prescribed energy conservation measures OR meet 2030 carbon limits.

### Boston BERDO 2.0
Buildings with zoning approval post-ordinance implementation comply with zoning-specified standards (supersede Table 1). Deed-restricted affordable housing ≥50% of units at ≤80% AMI: streamlined hardship provisions. Emergency backup generation exempt through 2030 (except healthcare). EVSE energy permanently deductible from building totals. City buildings: same emissions standards but exempt from fines.

### DC BEPS
Delays available (up to 3 years) for: major renovations, financial distress, unoccupied buildings, pending demolition. Affordable housing may qualify for delays >3 years. COVID-adjusted delays no longer count toward 3-year maximum (BEPS Amendment Act of 2024).

### Maryland BEPS
Excluded building types: agricultural, K-12 schools, manufacturing, federally-owned buildings, individually-designated historic properties, hospitals (added by HB49, 2025), Montgomery County buildings (covered by separate county program), buildings <35,000 SF.

### WA CBPS
Buildings demolishing within 5 years; historic structures (case-by-case); certain religious/nonprofit exemptions; financial hardship waiver (must apply 180 days before deadline).

### UK MEES
Must be registered on PRS Exemptions Register. Seven-year payback test is the most commonly used exemption. New exemption rules apply from 2025 for some property types. Exemptions last 5 years; must be re-registered.

### France Décret Tertiaire
Modulation (target adjustment) — not a full exemption — available for heritage buildings, activity intensity changes, and economic hardship. Must be formally documented in OPERAT with supporting evidence.

---

## Jurisdiction-Specific Notes and Active Legislative Risks

### NYC
- **Occupancy group "D" does not exist** in NYC Building Code or LL97. Any analysis referencing occupancy D is in error.
- **S-1 and S-2 are combined as "S"** in LL97 emission tables.
- **NYC Council Intro 772** proposes weakening LL97 for co-ops, condos, and garden apartments — track via Urban Green Council. Active as of July 2026.
- **LL154 (fossil fuel ban, new construction)** upheld by SDNY in March 2025; Second Circuit appeal pending — law remains in full effect.
- **2030–2034 B-special/H/I-2/I-3 limit of 0.01193:** Two sources corroborate this; UpCodes shows 0.01330 as a discrepant outlier. Always verify against official DOB Table 320.7.6b before using in enforcement calculations.
- **BEAM portal** is the required filing platform for LL97 compliance reports and LL84 benchmarking.

### Boston
- **BERDO 2.0 grid factor:** 249 kg/MWh in 2025; declining to 150 kg/MWh by 2050 per Appendix B.
- **2026 extended deadline:** Annual report for 2025 data extended from May 15 to August 15, 2026.
- **Third-party verification years:** 2022, 2026, and every 5 years thereafter.

### DC
- **BEPS Amendment Act of 2024** signed January 2025: moved annual benchmarking deadline from April 1 to May 1; removed COVID-adjusted delays from the 3-year delay cap.
- **EPA 2025 CBECS dataset update** may shift Energy Star scores and complicate Cycle 2 planning.

### Maryland
- **Tier 1/Tier 2 terminology does NOT apply to Maryland.** That structure belongs to Washington State's Clean Buildings Act. Maryland covers all buildings ≥35,000 SF under a single threshold.
- **Montgomery County buildings** are exempt from state BEPS under HB49 (2025) — they fall under a separate county program.
- **EUI standards** were postponed; MDE intends to reinstate in 2027 based on verified 2025 baseline data.
- **Legal challenges** citing EPCA preemption are pending as of July 2026.

### California
- **No enforceable statewide BPS as of July 2026.** CEC SB48 study due August 2026; any resulting legislation unlikely before 2027.
- **CARB has no commercial building BPS program** — CARB's building-sector work is appliance standards, refrigerants, and air district rules.
- **SF BPS** (proposed): not yet enacted; expected adoption 2026 with first enforceable deadline 2028.

### Washington State CBPS
- **Two tiers only — not three.** What some sources call "Tier 1/2/3" are actually: compliance Phase A/B/C within Tier 1, plus Tier 2.
- **Office EUI target is 40/41 kBtu/SF/yr** (WAC 194-50-150 official value). Industry summaries sometimes cite ~63 kBtu/SF/yr — this is the pre-WA-adjustment ASHRAE figure. Use the WAC value.
- **Multifamily residential ≥20,000 SF is Tier 2 regardless of total building size.** A mixed-use building with >50,000 SF of nonresidential space would be Tier 1 for the nonresidential portion.

### Chicago
- **CABO (Clean and Affordable Buildings Ordinance) is stalled in committee** as of mid-2026. No enacted performance standard for existing Chicago buildings.
- **Chicago Benchmarking** was relaunched December 2025 under a new support team. 2024 data deadline was extended to January 15, 2026.

### Canada
- **Toronto BEPS** (GHG caps for existing buildings) is in technical development; Council return expected Q1 2027. Current obligation is EWRB reporting only.
- **Toronto Green Standard v4 Tier 1** is legally contested following Ontario Bill 98 (May 2026) eliminating mandatory sustainable design requirements from provincial planning law. TGS v5 indefinitely paused.
- **Vancouver is the only Canadian city with a financial-penalty BPS for existing commercial buildings** as of July 2026.
- **Alberta has no BPS for existing commercial buildings** and no announced plan to develop one.

### UK
- **Scotland is NOT covered by England/Wales MEES.** Scotland operates a separate Action Plan regime under AEPNDB Regulations 2016 / EPC Regs 2025.
- **UK SRS (UK Sustainability Reporting Standards, ISSB-aligned)** expected to be mandated for large listed companies from 2026–2027, augmenting SECR.

### EU
- **ETS2 first compliance surrender: 2028** (one-year delay from original 2027). Trading begins 2027. Cost reaches building owners through fuel bills, not as a direct fine on building owners.
- **EU Taxonomy:** Even if a renovation achieves 30% PED reduction, the loan is non-Taxonomy-aligned if post-renovation EPC fails to reach class A or top-15% threshold.
- **Germany GEG:** No EPC letter system in Germany — EU Taxonomy's "top-15% EPC" criterion requires alternative evidence. (verify current alternative evidence guidance from German taxonomy legal counsel)
- **France Décret Tertiaire:** Buildings that miss the September 30 OPERAT deadline trigger immediate name-and-shame exposure before any fine is issued.

---

## Verification Flags

The following values should be independently verified before use in a legal or financial closing context:

1. **(verify)** NYC LL97 emission factor for electricity (~0.000288962 tCO2e/kWh) — updated annually by NYC DOB. Always pull current year factor from 1 RCNY §103-14.
2. **(verify)** NYC LL97 2030–2034 B-special/H/I-2/I-3 limit: 0.01193 vs. UpCodes discrepant figure of 0.01330 — verify against official DOB Table 320.7.6b.
3. **(verify)** LA EBEWE penalty: $202/violation or $202/day — confirm interpretation from LAMC Division 97 directly.
4. **(verify)** Netherlands office label C fine: no published national fixed schedule; confirm with relevant municipality's enforcement authority.
5. **(verify)** Maryland BEPS building-type-specific targets for office, retail, hotel beyond multifamily — consult full COMAR 26.28 text or BEPS.MDE@maryland.gov.
6. **(verify)** WA CBPS office EUI target: use 40/41 kBtu/SF/yr (official WAC 194-50-150), not the ~63 figure that appears in some secondary sources.
7. **(verify)** France Décret Tertiaire absolute consumption targets (valeurs absolues): current published values by building type and climate zone from ADEME/OPERAT.
8. **(verify)** Colorado Statewide BPS per-unit monthly penalty rate: final per-kBtu rate from AQCC Rule 5 CCR 1001-32 rulemaking documentation.
9. **(verify)** NYC LL97 compliance report deadlines: current DOB Service Notice may update the December 31, 2025 extension date. Confirm via BEAM portal.
10. **(verify)** Germany GEG EU Taxonomy alignment: guidance on alternative evidence for "top-15% EPC" criterion in Germany (where letter EPCs do not exist).

---

## Data Sources

- NYC: nyc.gov/buildings, DOB BEAM portal, 1 RCNY §103-14, NYC Admin Code §320
- Boston BERDO: boston.gov/departments/environment/berdo, Official Regulations (Dec 2023), Policies and Procedures v3 (Sep 2025)
- Cambridge BEUDO: cambridgema.gov/CDD/zoninganddevelopment/sustainabilitybeudo, Phase 3 Regulations (Apr 2026)
- DC BEPS: dcgreenbank.com/beps, doee.dc.gov, BEPS Amendment Act of 2024
- Maryland BEPS: mde.maryland.gov/programs/air/climatechange/pages/mdbeps.aspx, COMAR 26.28, HB49 (2025)
- Energize Denver: denvergov.org/energizedenver, April 2025 rules update
- WA CBPS: commerce.wa.gov/growing-the-economy/energy/buildings/clean-buildings/, WAC 194-50
- Oregon BPS: oregon.gov/energy/Residential-Renewable/Pages/Building-Performance-Standards.aspx, ORS 330-300
- California: energy.ca.gov (AB 802), labuildings.lacity.gov/ebewe (LA EBEWE), sfenvironment.org/ebeo (SF EBEO), sanjoseca.gov/ewbpo (San Jose)
- UK MEES: gov.uk/guidance/domestic-private-rented-property-minimum-energy-efficiency-standard
- France: operat.ademe.fr, Légifrance (Décret n°2019-771)
- EPBD 2024: EUR-Lex (EU) 2024/1275
- EU Taxonomy: EUR-Lex Delegated Regulation (EU) 2026/73
- CSRD/ESRS: efrag.org, EUR-Lex
- ETS2: EUR-Lex (EU) 2023/959
- Germany GEG: gesetze-im-internet.de/geg
- Netherlands: wetten.overheid.nl (Activiteitenbesluit milieubeheer)
- Vancouver: vancouver.ca/green-vancouver/annual-greenhouse-gas-and-energy-limits-bylaw.aspx
- Toronto EWRB: toronto.ca/services-payments/water-environment/environmental-reporting-disclosure/building-energy-benchmarking/
- Canada Federal: nrc.canada.ca/en/certifications-evaluations-standards/codes-canada/national-model-construction-codes
