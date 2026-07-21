# Mapping Affordable Housing Potential in Pittsburgh

**Spatial analysis of housing affordability and city-owned parcels · ArcGIS, U.S. Census ACS, WPRDC open data**

> The places that need the most help are also where the city has the most land to rebuild. 59% of available city-owned parcels sit in Pittsburgh's lowest-income areas.

## Problem

Pittsburgh holds over 12,700 parcels of publicly owned land — much of it vacant, deteriorating, and off the tax rolls while residents across the city face rising housing cost burdens. If the city knew *which* parcels sit where affordable housing is needed most, public land could become a direct pipeline for equitable development. This project identifies priority areas for affordable rental housing by overlaying neighborhood-level affordability indicators with the spatial distribution of city-owned parcels currently available for sale.

## Methodology

- **Data:** ACS 2023 5-Year Estimates (median household income, median gross rent at block-group level), City-Owned Properties dataset from the Western Pennsylvania Regional Data Center, and Census TIGER/Line and city neighborhood shapefiles
- **Parcel filtering:** restricted to buildings and vacant land marked available for public sale, with positive square footage, in residential or mixed/commercial zoning (excluding parks, industrial, and restricted areas) which has 1,890 developable parcels
- **Kernel Density Estimation** to surface concentration hotspots of available parcels across the city
- **Spatial joins and neighborhood aggregation** linking parcels to block groups, then summarizing to neighborhood level
- **Bivariate overlay maps:** choropleths of income and gross rent with proportional-symbol parcel counts, revealing where public land availability intersects economic need

## Key Findings

- **Available parcels cluster in three high-density areas** Homewood (North/South/West, extending to East Hills and Lincoln-Lemington-Belmar), Garfield/Central Lawrenceville, and Beltzhoover. All neighborhoods are shaped by historic disinvestment
- **59% of all available parcels (1,113 of 1,890) fall in the city's lowest-income block groups**; high-income neighborhoods like Squirrel Hill and Shadyside have almost none
- **Parcel distribution is highly right-skewed:** neighborhoods average 45 parcels, but Lincoln-Lemington alone holds 370
- **Comparing income and rent maps shows renters in priority neighborhoods struggle more from low incomes than high rents** — meaning new affordable units there could realistically serve current residents rather than displace them
- **Priority recommendation:** Homewood, East Hills, Beltzhoover, and Lincoln-Lemington-Belmar combine the greatest need with the greatest public-land opportunity

All data sources are public: [data.census.gov](https://data.census.gov) for ACS tables B19013 and B25064, and the [Western Pennsylvania Regional Data Center](https://data.wprdc.org) for the City-Owned Properties dataset and neighborhood shapefiles.

## Reflection

This project taught me to design a spatial analysis around a policy decision. Every methodological choice, from parcel filtering criteria to the level of aggregation, traces back to the question "where should an affordable housing developer look first?" It also reinforced the value of layering multiple views: the KDE, income overlay, and rent overlay each told partial stories, and the actionable insight (low-income, moderate-rent neighborhoods with abundant public land) only emerged from reading them together. To improve, I'd build a composite housing-need score adding housing quality, vacancy, transit access, and proximity to amenities, and I'd address the block groups missing ACS estimates.

---

*Nandita Kannapadi · MPPM, Carnegie Mellon University — Heinz College*
