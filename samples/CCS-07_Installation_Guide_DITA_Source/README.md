# CCS Site Installation and Configuration Guide — DITA source

A worked example of how the installation guide is built in DITA 1.3. Every file carries
XML comments that explain which DITA feature it uses and why. All CCS values (paths,
versions, commands, settings) are illustrative.

> No CUI, classified, proprietary, or export-controlled information is contained in this
> document. Provided as a technical writing sample — Nathan B. Smith.

## Where each part of the guide lives

| Guide part | File | DITA type | What it demonstrates |
|---|---|---|---|
| Whole book, order, front/back matter | `ccs-install-guide.bookmap` | bookmap | Map controls structure; topics don't know which book they're in |
| Release number, build, paths | `keydefs.ditamap` | map (keys) | Change a value once, every page updates |
| Title page metadata | `<bookmeta>` in the bookmap | bookid, bookchangehistory | Document number, revision, review/approval |
| Disclaimer, "illustrative" notice | `reuse/notices.dita` | topic (reuse) | Pulled in by conref |
| Approval page | `fm_approval.dita` | topic | Signature blocks |
| Record of changes | `fm_record-of-changes.dita` | topic | Front-matter revision history |
| Contents, figures, tables lists | `<booklists>` | generated | No files; built from titles |
| Preface | `fm_preface.dita` | concept | Purpose, audience, conventions |
| Overview + flow figure | `c_install_overview.dita` | concept | Explanation kept apart from steps |
| References | `r_install_references.dita` | reference | Look-up table |
| Before you begin | `r_install_prerequisites.dita` | reference | `@product` rows filtered per station type |
| Sections 3, 4, 6, 7, 8 | `t_install_*.dita` | task | prereq → steps → result; one `<cmd>` per step |
| Section 5 | `t_config_configure-site.dita` | task | Links to the property reference instead of repeating it |
| Site properties table | `r_config_site-properties.dita` | reference | `<properties>`: semantic name / value / meaning |
| Warnings and cautions | `reuse/warnings.dita` | topic (reuse) | Written once, conref'd into steps |
| Smoke test (air vs. UUV) | `t_install_verify-installation.dita` | task | `@platform` on steps; one topic, no forks |
| Appendix A, Troubleshooting | `tr_*.dita` | troubleshooting | condition → cause → remedy, one symptom per topic |
| Appendix B, Glossary | `glossary/g_*.dita` | glossentry | One term per file; first use prints long form |
| Index | `<indexterm>` in task prologs | generated | Index built from tagged terms |
| Per-site editions | `admin-land.ditaval`, `admin-ship.ditaval` | DITAVAL | Same source, different builds |

## Build

Tested with DITA Open Toolkit 4.2.4 in **strict** processing mode (DTD-validated):

```
dita -i ccs-install-guide.bookmap -f pdf   --filter=admin-land.ditaval --processing-mode=strict
dita -i ccs-install-guide.bookmap -f html5 --filter=admin-ship.ditaval --processing-mode=strict
```

Checked in the output: the land build shows "Two monitors" and the ship build shows "Two
ruggedized monitors"; `ccs-build` resolves to 4.2.0-1187; the shared warning appears
through conref.

## What strict validation caught (and what it teaches)

1. `<appendices>` is not allowed inside `<backmatter>`; it sits directly in the bookmap.
2. A `<mapref>` can't sit between `<bookmeta>` and `<frontmatter>`; it goes inside front matter.
3. A reference body can't hold a bare `<note>`; it must be inside a `<section>`.
4. In a task step, a `<note>` is only allowed **before** `<cmd>`. The schema enforces the
   writing rule "put the warning before the action it protects."
5. `<bookid>` and `<bookmeta>` children have a fixed order; `<amendments>` is back-matter only.
