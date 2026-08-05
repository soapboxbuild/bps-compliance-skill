> # DO NOT USE
>
> **Status: superseded.** This skill now lives in the Soapbox plugin
> marketplace, which is the single distribution point for every Soapbox skill.
>
> **Use instead:** `soapbox-build/soapbox-marketplace` →
> `plugins/soapbox-compliance/skills/bps-compliance`
>
> The marketplace version is a rewrite rather than a copy, and it is the larger
> of the two: `SKILL.md` plus five references (metrics and penalties, compliance
> pathways and exemptions, deadline calendar, jurisdiction notes, applicability
> thresholds), 62.7 KB against 61.3 KB here. Verified before this repo was marked
> deprecated.
>
> Nothing here is unique. Edit the marketplace copy.

---

## Historical README

Kept for provenance. Everything below describes the deprecated implementation.

# BPS Compliance Skill

A Claude Code skill for Building Performance Standards (BPS) compliance, covering Local Law 97 (NYC), BEPS ordinances across US/Canada/EU, BERDO 2.0 (Boston), carbon penalty calculations, and fine mitigation strategies.

## Install

```bash
npx skills add soapboxbuild/bps-compliance-skill
```

## Commands

### `/ll97`
Calculate Local Law 97 carbon penalties and compliance gap for a NYC property. Identifies occupancy group, computes the threshold, calculates current penalty exposure, and projects 2030-2034 liability.

**Usage:** `/ll97 123 Main St, 50,000 sf office, 450 tCO2e annual emissions`

### `/berdo`
Calculate BERDO 2.0 compliance for a Boston property. Converts energy data to GHG intensity, compares against the applicable BERDO limit for the compliance period, calculates annual penalty ($1,000/tCO2e over limit), and recommends compliance pathways.

**Usage:** `/berdo 200 State St Boston, 80,000 sf office, 650,000 kgCO2e annual`

### `/beps`
Check Building Energy Performance Standards compliance across multiple jurisdictions (NYC, DC, Denver, Boston, Chicago, Toronto, and more). Maps city ordinance to applicable standard and computes compliance gap.

**Usage:** `/beps Denver office building, 80 kBtu/sf EUI`

### `/penalty`
Model carbon penalty scenarios and mitigation ROI. Compares pay-penalty vs. retrofit vs. RECs/offsets strategies with NPV analysis across multiple capex scenarios.

**Usage:** `/penalty 500 tCO2e current, 300 tCO2e target, $2M retrofit budget`

## Skill

The `bps-compliance` skill is available for use in any conversation. It provides:

- LL97 carbon thresholds by occupancy group (2024-2029 and 2030-2034 periods)
- BERDO 2.0 GHG intensity limits by building type (2025–2050 compliance schedule)
- BERDO emissions conversion factors and alternative compliance pathways
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
