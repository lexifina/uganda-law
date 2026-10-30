# How this repository was made (Uganda)

This file is written by the build on 2026-10-30, the day the source data was retrieved.

## Sources

| Source | Address | Retrieved | Licence |
| --- | --- | --- | --- |
| ULII, the Uganda Legal Information Institute (Judiciary of Uganda, on the Laws.Africa Peachjam platform) | <https://ulii.org> | 2026-10-28 | CC BY-NC 4.0, crediting ULII as the source (https://ulii.org/en/terms-of-use/) |
| Internet Archive Wayback Machine | <https://web.archive.org> | 2026-10-28 | Archived copies of ULII pages; the content licence is ULII's |
| ULII, the Uganda Legal Information Institute (Judiciary of Uganda, on the Laws.Africa Peachjam platform) | <https://ulii.org> | 2026-10-30 | CC BY-NC 4.0, crediting ULII as the source (https://ulii.org/en/terms-of-use/) |

Every word of law in this repository comes from these sources. Lexifina reads them and records each act's dated versions, and the laws that made each change, in one corpus file. This repository is built from that file.

## What is in it

| Act | Title | Versions | Span |
| --- | --- | ---: | --- |
| `constitution` | Constitution of the Republic of Uganda | 6 | 2000-12-31 to 2023-12-31 |
| `penal-code` | Penal Code Act | 8 | 2000-12-31 to 2024-12-23 |
| `evidence` | Evidence Act | 2 | 2000-12-31 to 2023-12-31 |
| `criminal-procedure-code` | Criminal Procedure Code Act | 2 | 2000-12-31 to 2023-12-31 |
| `trial-on-indictments` | Trial on Indictments Act | 6 | 2000-12-31 to 2023-12-31 |
| `magistrates-courts` | Magistrates Courts Act | 5 | 2000-12-31 to 2023-12-31 |
| `companies` | Companies Act | 3 | 2013-07-01 to 2023-12-31 |
| `insolvency` | Insolvency Act | 2 | 2013-07-01 to 2023-12-31 |
| `registration-of-titles` | Registration of Titles Act | 4 | 2000-12-31 to 2023-12-31 |
| `marriage` | Marriage Act | 4 | 2000-12-31 to 2023-12-31 |
| `divorce` | Divorce Act | 2 | 2000-12-31 to 2023-12-31 |
| `succession` | Succession Act | 2 | 2000-12-31 to 2023-12-31 |
| `interpretation` | Interpretation Act | 3 | 2000-12-31 to 2023-12-31 |
| `advocates` | Advocates Act | 3 | 2000-12-31 to 2023-12-31 |
| `arbitration-and-conciliation` | Arbitration and Conciliation Act | 4 | 2000-12-31 to 2024-12-23 |
| `anti-corruption` | Anti-Corruption Act | 3 | 2009-08-25 to 2023-12-31 |
| `anti-money-laundering` | Anti-Money Laundering Act, 2013 | 3 | 2013-11-01 to 2020-11-27 |
| `computer-misuse` | Computer Misuse Act | 2 | 2011-04-15 to 2023-12-31 |
| `access-to-information` | Access to Information Act | 2 | 2006-04-20 to 2023-12-31 |
| `presidential-elections` | Presidential Elections Act | 5 | 2005-11-21 to 2023-12-31 |
| `local-governments` | Local Governments Act | 2 | 2000-12-31 to 2023-12-31 |
| `limitation` | Limitation Act | 2 | 2000-12-31 to 2023-12-31 |
| `bank-of-uganda` | Bank of Uganda Act | 2 | 2000-12-31 to 2023-12-31 |
| `anti-terrorism` | Anti-Terrorism Act, 2002 | 3 | 2002-06-07 to 2024-12-23 |
| `traffic-and-road-safety` | Traffic and Road Safety Act, 1998 | 6 | 2000-12-31 to 2020-05-22 |
| `land-acquisition` | Land Acquisition Act | 2 | 2000-12-31 to 2023-12-31 |
| `public-health` | Public Health Act | 2 | 2000-12-31 to 2023-12-31 |
| `political-parties` | Political Parties and Organisations Act | 1 | 2023-12-31 to 2023-12-31 |
| `human-rights-enforcement` | Human Rights (Enforcement) Act | 2 | 2019-11-15 to 2023-12-31 |
| `excise-duty` | Excise Duty Act | 2 | 2014-07-01 to 2023-12-31 |
| `ngo` | Non-Governmental Organisations Act | 2 | 2016-03-14 to 2023-12-31 |
| `anti-homosexuality` | Anti-Homosexuality Act, 2023 | 2 | 2023-05-30 to 2023-12-31 |

The build made 95 commits:

| Commits | Kind |
| ---: | --- |
| 32 | first version of an act |
| 34 | one law on its in-force day |
| 29 | changes no amendment note explains, credited to the publisher |

Other counts:
- 0 commits on the branch `future`: laws not yet in force on 2026-10-30.
- 0 commits dated 1 January 1970: in force before 1970, with the real day in their `In-force` trailer.
- 68 laws in the record.
- 143 tags.

## Dates

Each commit is dated at noon (Africa/Kampala) on the day the change took effect. The other dates, enacted and published, are trailers.

When a law gives no date of its own, the default rule applies: Not applied: every version is dated by ULII's own expression date, the day the amendment it incorporates took effect as Laws.Africa records it (for a consolidation, the date the revised edition is as at). No date is computed from a default rule. https://ulii.org/en/legislation/

## How the history is built

`tools/build.py` turns the corpus into this history in one pass: one commit per law, on the day it took effect. The same corpus always gives the same commit hashes. `tools/check_repo.py` reads every version back from git and compares it with the corpus. `tools/on.py` shows the law as it stood on any date. The corpus format is described in `tools/SCHEMA.md`.

- Corpus: sha256 `2d39900cfb162bbcddb97493e8f696cff3ba55988580656be4c48027aa8b5789` (8379263 bytes).
- Builder blob hashes (`git hash-object`): `build.py` `a4faa25af85facb64b956b372f6b528aafdd7ec1`, `check.py` `3d00541d258745461ab52b1b0cb4e1716a27a95d`, `on.py` `644a6c0857fbcc72562032b58d57aa113fee0641`.
- Python 3.12.10; git version 2.46.0.windows.1.

## Checks

99 versions of 32 acts read back from git on the day each took effect and on the day before: 0 mismatches. Trailers: 0 commits whose trailers git cannot parse. Health: 0 merge commits on main, 0 commit dates that go backwards, 0 commits dated after the build.

A second build from the same corpus into an empty folder gave identical hashes for all 95 history commits and 143 tags (history tip `5dba065ebc3427c36523d6994cea773569d379a5`).

## Decisions made by hand

- Acts were chosen by what the archived sources support: every expression ULII lists for the Constitution (6) and the Penal Code Act (8) has an archived copy, so each version is read from its own dated expression.
- The Revised Laws 2023 (the Law Reform Commission's revised edition, as at 31 December 2023) renumbered chapters and revised wording throughout; ULII publishes it as a consolidation, and its changes are committed as the publisher's, not credited to any Act, unless ULII's own note names the Act.
- The Data Protection and Privacy Act 2019 was tried and dropped: ULII's current version of it is the Revised Laws 2023 expression (2023-12-31), which has no usable archived copy, so today's text could not be checked.
- Licence: ULII licenses its content CC BY-NC 4.0 with attribution; CC BY-NC allows only non-commercial use. Every version is read from an archived copy, for the configured acts only. No legal text was given to a model.
- Version dates are ULII's expression dates. Laws.Africa's terminology guide (https://docs.laws.africa/getting-started/terminology-guide) says "Amendments to Principal works come into force on the Commencement date of the Amending work" and that the first point in time is "the work as originally published"; so an amendment's expression is dated by its commencement (in force), and an act's original expression by its publication, which is replaced by the commencement date the page states.
- Credits: a version whose History names exactly one amending law (and no consolidation) between it and the previous version is credited to that law for every provision that changed. Otherwise a provision is credited only to laws that ULII's editorial note inside that provision links to; the rest are unexplained (publisher).
- Editorial notes (akn-remark) are left out of the text and used only as credit evidence, except where a provision has no other text (repealed or spent), where the note is the provision's whole printed content.
- Part, Chapter and Division headings are left out; each provision file starts with its own number and heading. Every other text of each version is in a provision file: this is checked per version (verification.json, fidelity).
- Batch 2 acts were chosen among the principal national Acts for which every point-in-time version ULII lists is available: Evidence Act, Criminal Procedure Code Act, Trial on Indictments Act, Magistrates Courts Act, Companies Act, 2012, Insolvency Act, 2011, Registration of Titles Act, Marriage Act, Divorce Act, Succession Act, Interpretation Act, Advocates Act, Arbitration and Conciliation Act, Anti-Corruption Act, 2009, Anti-Money Laundering Act, 2013, Computer Misuse Act, 2011, Access to Information Act, 2005, Presidential Elections Act, 2005, Local Governments Act, Limitation Act, Bank of Uganda Act, Anti-Terrorism Act, 2002, Traffic and Road Safety Act, 1998, Land Acquisition Act, Public Health Act, Political Parties and Organisations Act, 2005, Human Rights (Enforcement) Act, 2019, Excise Duty Act, 2014, Non-Governmental Organisations Act, 2016, Anti-Homosexuality Act, 2023.
- Batch 2 left out, because a version ULII lists was not available: the Tax Appeals Tribunals Act (2000-12-31, 2021-07-01), the Public Procurement and Disposal of Public Assets Act 2003 (2003-01-17, 2006-02-10, 2014-03-03), the Parliamentary Elections Act 2005 (2023-12-31), the Pensions Act (2000-12-31), the Companies Act of 1958 (2000-12-31) and the Children Act (2000-12-31, 2006-06-08).
- Most batch 2 histories start with the Revised Edition of the Laws of Uganda 2000 (expression 2000-12-31), the oldest version ULII publishes for those Acts, and end with the Revised Laws 2023 (2023-12-31); both are consolidations, so wording they changed is committed as the publisher's unless ULII's own note names an Act.
- Companies Act: the first version is dated 2013-07-01, the commencement date ULII states ("Commenced on 1 July 2013 by Companies Act, 2012 (Commencement) Instrument, 2013"), not 2012-09-18, the date of its expression (Gazette publication).
- Insolvency Act: the first version is dated 2013-07-01, the commencement date ULII states ("Commenced on 1 July 2013 by Insolvency Act, 2011 (Commencement) Instrument, 2013"), not 2011-09-23, the date of its expression (Gazette publication).
- Computer Misuse Act: the first version is dated 2011-04-15, the commencement date ULII states ("Commenced on 15 April 2011 by Computer Misuse Act, 2011 (Commencement) Instrument, 2011"), not 2011-02-14, the date of its expression (Gazette publication).
- Access to Information Act: the first version is dated 2006-04-20, the commencement date ULII states ("Commenced on 20 April 2006 by Access to Information (Commencement) Instrument, 2006"), not 2005-07-19, the date of its expression (Gazette publication).
- Excise Duty Act: the first version is dated 2014-07-01, the commencement date ULII states ("Commenced on 1 July 2014"), not 2014-10-24, the date of its expression (Gazette publication).
- Non-Governmental Organisations Act: the first version is dated 2016-03-14, the commencement date ULII states ("Commenced on 14 March 2016 by Non-Governmental Organisations Act (Commencement) Instrument, 2016"), not 2016-03-03, the date of its expression (Gazette publication).

## What AI did and did not do

The scripts that read the sources and build this repository were written by Claude Code running Claude Opus 5.5 (`claude-opus-5-5`) under Lexifina's direction.

No model wrote, translated or corrected legal text. No model runs at build time. Every word of law in this repository comes from the official sources above.

The commit messages are written by `build.py` from the source data.

Model use at data-build time:
- Claude Code (Claude Opus 5.5, claude-opus-5-5) wrote the adapter and configuration and chose the acts. No model wrote, summarised or transformed legal text: the text is parsed by deterministic code.
- Claude Code (Claude Opus 5.5, claude-opus-5-5) wrote the adapter and configuration and chose the acts. No model wrote, summarised or transformed legal text: Lexifina's code is deterministic code.
