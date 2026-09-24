# CCS Documentation Portfolio

Technical writing samples for a Common Control System (CCS) software technical writing role, prepared by Nathan B. Smith for the SAIC Senior Software Technical Writer interview (CCS, NIWC Pacific).

**Live page:** https://nbsmith-dev.github.io/ccs-documentation-portfolio/

> **Disclaimer.** No CUI, classified, proprietary, or export-controlled information is contained in these documents. Provided as technical writing samples — Nathan B. Smith. All content is illustrative and built only from publicly available press and web content. Screens, labels, values, procedures, document and contract numbers, ticket numbers, and names are invented. Not affiliated with or endorsed by the U.S. Navy, NAVAIR, NIWC Pacific, or SAIC.

## Sources

| Source | Purpose |
|---|---|
| [NAVAIR — Common Control System](https://www.navair.navy.mil/product/CCS) | Mission, open architecture, platforms |
| [NAVAIR — CCS first live demonstration](https://www.navair.navy.mil/node/23331) | Cross-domain use (surrogate LDUUV); PMA-281 |
| [C4ISRNET — Navy moves closer to common control system](https://www.c4isrnet.com/unmanned/uas/2016/12/13/navy-moves-closer-to-common-control-system/) | The three core functions |
| [USNI News — Common standards, software key to Navy's future unmanned systems](https://news.usni.org/2020/09/10/common-standards-software-key-to-navys-future-unmanned-systems) | Why common control matters to operators |
| [Forward Slope — NIWC Pacific CCS Software Support Activity](https://www.forwardslope.com/news/fsi-awarded-naval-information-warfare-center-pacific-contract-provide-software-support) | NIWC Pacific's sustainment role |
| [Aviation Week](https://aviationweek.com/defense/sensors-electronic-warfare/us-navy-remove-retire-remaining-mq-8c-fleet) / [FlightGlobal](https://www.flightglobal.com/helicopters/us-navys-mq-8c-fire-scouts-fly-into-retirement-just-two-years-after-entering-operational-service/158500.article) | MQ-8C retirement |
| SAIC public job posting, Job ID 2616178 | Duties the samples are organized around |
| MIL-STD-498 DI-IPSC-81443A; OASIS DITA 1.3; DITA Open Toolkit; DoDI 5200.48; NAVEDTRA 130 | Structure, markup, markings, lesson format |

## Contents

| ID | Sample | Files |
|---|---|---|
| CCS-01 | CCS overview for technical writers (10 slides) | PDF, PPTX |
| CCS-02 | Software User Manual outline in DITA (11 slides) | PDF, PPTX |
| CCS-03 | Software User Manual, formal deliverable (22 pages) | PDF |
| CCS-04 | How-To Guides plan (12 slides) | PDF, PPTX |
| CCS-05 | Training lesson 2.1: Build and validate a route (5 pages) | PDF |
| CCS-06 | Site installation and configuration guide, formal deliverable (16 pages) | PDF |
| CCS-07 | DITA source for CCS-06, commented; DITA-OT build output | Folder, ZIP, PDF |
| CCS-08 | Sprint documentation status report (3 pages) | PDF |

## Structure

```
index.html        Portfolio page (static HTML/CSS, no build step)
samples/          All samples, numbered CCS-01 to CCS-08
.nojekyll         Serve files as-is on GitHub Pages
```

## Building the DITA source (CCS-07)

Validated with DITA Open Toolkit 4.2.4 in strict mode:

```
cd samples/CCS-07_Installation_Guide_DITA_Source
dita -i ccs-install-guide.bookmap -f pdf  --filter=admin-land.ditaval --processing-mode=strict
dita -i ccs-install-guide.bookmap -f html5 --filter=admin-ship.ditaval --processing-mode=strict
```

© 2026 Nathan B. Smith. All rights reserved. Shared for review.
