# seaice-product-repo: the founding plan and running record

**Satellite sea ice**, from the Copernicus Marine Service. Created on GitHub by the owner and given its documents by the site's
`pipeline/scaffold/new-origin.py`. **Publishing since 2026-10-17, every three hours.**

## What it is for

Satellite sea ice from the Copernicus Marine Service, each grid reaching as far toward its pole as its satellites see, published to Cloudflare R2 alone: **EUMETSAT OSI SAF**'s daily concentration from the AMSR radiometer at 10 km (`sic-osisaf.json`), ice edge (`siedge-osisaf.json`: open water, open ice, closed ice) and ice type (`sitype-osisaf.json`: open water, first-year, multi-year, ambiguous), each both poles on one 0.1° grid, and its 48-hour drift at 62.5 km (`sidrift-osisaf.json`, east and north components); **DTU Space**'s Sentinel-1 SAR drift at 10 km, a 24-hour composite every 12 hours (`sidrift-dtu.json`); **DMI**'s 1 km concentrations, the Arctic's daily (`sic-dmi-arctic.json`) and the Antarctic's as the newest of 7 days with each cell's age (`sic-dmi-antarctic.json`, `sic-dmi-antarctic-age.json`), and the Arctic's sea and ice surface temperature (`ist-dmi.json`); **AWI**'s CryoSat-2 and SMOS thickness, 7-day means, each pole's (`sit-cs2smos-arctic.json`, October to April; `sit-cs2smos-antarctic.json`); **FMI and SMHI**'s Baltic ice charts in the ice season (`sic-fmi.json`, `sit-fmi.json`). Each overview root points at its finer tiles.

## Where the data comes from

The Copernicus Marine Service's sea ice catalogue (SEAICE_GLO_SEAICE_L4_NRT_OBSERVATIONS_011_001 and 011_006, SEAICE_ARC_PHY_AUTO_L4_MYNRT_011_024, SEAICE_ANT_PHY_AUTO_L3_NRT_011_012, SEAICE_ARC_SEAICE_L4_NRT_OBSERVATIONS_011_008, SEAICE_GLO_PHY_L4_NRT_011_014, SEAICE_BAL_SEAICE_L4_NRT_OBSERVATIONS_011_004), read through the Copernicus Marine toolbox from its map-shaped stores. **Their terms were read before a line was written** (2026-10-17): the Copernicus Marine Service licence, crediting the Copernicus Marine Service and each product's DOI, and OSI SAF's products EUMETSAT's, *Copyright © EUMETSAT* shown with them. OSI SAF's radiometer products take AMSR3 (GOSAT-GW) since 2026-09-01 under their datasets' old "amsr2" names.

## Record

**2026-10-17: the first dispatched run, 39044822092, green** (15:23-15:29 UTC): all twelve
products fresh, none refused, 38 published files matching the contract; the drifts held to
their frames on the runner (OSI SAF's end positions turned +0.6 and +0.1 degrees, DTU's
against OSI SAF's +1.4 over 4,250 cells); the 1 km Arctic 308 tiles, 295 MB, in 23 s;
R2 equal to the build, 846 files uploaded, none deleted. **Scheduled the same hour**, every
three hours at 17 past.

## Open

1. The Arctic thickness's season: its first October day (due around the 18th-20th), and in April its last.
2. The Baltic's ice season: the charts' first ice, and the Bothnia control observed.
