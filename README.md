# seaice-product-repo

**Satellite sea ice**, from the Copernicus Marine Service: a data repository of the oceansensing ocean map system, with its own
Pages site, its own schedule and its own gigabyte, and no code of its own.

**Nothing is published yet.** `PLAN.md` is the founding plan; `CLAUDE.md` carries what must not be
got wrong and the shared doc doctrine.

## What it publishes

Satellite sea ice from the Copernicus Marine Service, each grid reaching as far toward its pole as its satellites see, published to Cloudflare R2 alone: **EUMETSAT OSI SAF**'s daily concentration from the AMSR radiometer at 10 km (`sic-osisaf.json`), ice edge (`siedge-osisaf.json`: open water, open ice, closed ice) and ice type (`sitype-osisaf.json`: open water, first-year, multi-year, ambiguous), each both poles on one 0.1° grid, and its 48-hour drift at 62.5 km (`sidrift-osisaf.json`, east and north components); **DTU Space**'s Sentinel-1 SAR drift at 10 km, a 24-hour composite every 12 hours (`sidrift-dtu.json`); **DMI**'s 1 km concentrations, the Arctic's daily (`sic-dmi-arctic.json`) and the Antarctic's as the newest of 7 days with each cell's age (`sic-dmi-antarctic.json`, `sic-dmi-antarctic-age.json`), and the Arctic's sea and ice surface temperature (`ist-dmi.json`); **AWI**'s CryoSat-2 and SMOS thickness, 7-day means, each pole's (`sit-cs2smos-arctic.json`, October to April; `sit-cs2smos-antarctic.json`); **FMI and SMHI**'s Baltic ice charts in the ice season (`sic-fmi.json`, `sit-fmi.json`). Each overview root points at its finer tiles.

These products are published **operationally but not drawn on the website's map**; the map's status
line still reports them when they fall behind, which is how their health stays visible.

## Where the data comes from

The Copernicus Marine Service's sea ice catalogue (SEAICE_GLO_SEAICE_L4_NRT_OBSERVATIONS_011_001 and 011_006, SEAICE_ARC_PHY_AUTO_L4_MYNRT_011_024, SEAICE_ANT_PHY_AUTO_L3_NRT_011_012, SEAICE_ARC_SEAICE_L4_NRT_OBSERVATIONS_011_008, SEAICE_GLO_PHY_L4_NRT_011_014, SEAICE_BAL_SEAICE_L4_NRT_OBSERVATIONS_011_004), read through the Copernicus Marine toolbox from its map-shaped stores. **Their terms were read before a line was written** (2026-10-17): the Copernicus Marine Service licence, crediting the Copernicus Marine Service and each product's DOI, and OSI SAF's products EUMETSAT's, *Copyright © EUMETSAT* shown with them. OSI SAF's radiometer products take AMSR3 (GOSAT-GW) since 2026-09-01 under their datasets' old "amsr2" names.

## How it runs

The orchestrator (the site's private `pipeline/`), the fetchers and the
published-file contract all come from `oceansensing.github.io`, checked out at
run time. This repository carries `pipeline/products.toml` and its publish
workflow, and nothing else executable. Each run publishes to GitHub Pages and
to Cloudflare R2 from one build. Related repositories: `mercator-model-fields-repo` (Mercator's modelled sea ice) and `espc-model-fields-repo` (ESPC's), which draw the same quantities from models.

**Which document gets what, and what "update docs" means across all
twenty-eight repositories, is the doctrine block at the top of `CLAUDE.md`**: the
same text in all twenty-eight, held equal by the site's `check:docs`.

## Structure

```
README.md       what this is
CLAUDE.md       what must not be got wrong, and the shared doc doctrine
PLAN.md         the founding plan and running record
DECISIONS.md    dated one-way decisions, D1 onward
pipeline/       products.toml, the declaration the orchestrator reads
.github/        the publish workflow
```
