# BPS Compliance Skill

A Claude Code skill for Building Performance Standards (BPS) compliance, covering Local Law 97 (NYC), BEPS ordinances across US/Canada/EU, carbon penalty calculations, and fine mitigation strategies.

## Install

```bash
npx skills add soapboxbuild/bps-compliance-skill
```

## Commands

### `/ll97`
Calculate Local Law 97 carbon penalties and compliance gap for a NYC property. Identifies occupancy group, computes the threshold, calculates current penalty exposure, and projects 2030-2034 liability.

**Usage:** `/ll97 123 Main St, 50,000 sf office, 450 tCO2e annual emissions`

### `/beps`
Check Building Energy Performance Standards compliance across multiple jurisdictions (NYC, DC, Denver, Boston, Chicago, Toronto, and more). Maps city ordinance to applicable standard and computes compliance gap.

**Usage:** `/beps Denver office building, 80 kBtu/sf EUI`

### `/penalty`
Model carbon penalty scenarios and mitigation ROI. Compares pay-penalty vs. retrofit vs. RECs/offsets strategies with NPV analysis across multiple capex scenarios.

**Usage:** `/penalty 500 tCO2e current, 300 tCO2e target, $2M retrofit budget`

## Skill

The `bps-compliance` skill is available for use in any conversation. It provides:

- LL97 carbon thresholds by occupancy group (2024-2029 and 2030-2034 periods)
- BEPS ordinance reference table for 8 major cities
- Step-by-step compliance calculation workflow
- EPC rating context for European properties
- Key reporting deadlines and compliance calendar

## Jurisdictions Covered

| Region | Law/Standard |
|--------|-------------|
| NYC | Local Law 97 (LL97) |
| Washington DC | BEPS |
| Denver | BEPO |
| Boston | BERDO 2.0 |
| Chicago | CBEPS |
| St. Louis | BEPS |
| Seattle | Building Tune-Ups |
| Toronto | EWRB |
| UK | MEES / EPC |
| EU | EU Taxonomy / NZEB |

## License

Apache-2.0
