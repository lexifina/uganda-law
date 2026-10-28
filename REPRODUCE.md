# How this repository was made (Uganda)

This file is written by the build on 2026-10-28, the day the source data was retrieved. Everything below is enough to rebuild this repository hash for hash.

## Sources

| Source | Address | Retrieved | Requests | Licence |
| --- | --- | --- | ---: | --- |
| ULII, the Uganda Legal Information Institute (Judiciary of Uganda, on the Laws.Africa Peachjam platform) | <https://ulii.org> | 2026-10-28 | 147 | CC BY-NC 4.0, crediting ULII as the source (https://ulii.org/en/terms-of-use/) |
| Internet Archive Wayback Machine | <https://web.archive.org> | 2026-10-28 | None | Archived copies of ULII pages; the content licence is ULII's |

Every response is cached by the sha256 of its URL, and the table above lists every source with its retrieval date. Lexifina keeps its fetch scripts privately; `tools/parse.py` reads only the cache and writes `corpus.json`, so the same cache always gives the same corpus.

## What is in it

| Act | Title | Versions | Span |
| --- | --- | ---: | --- |
| `constitution` | Constitution of the Republic of Uganda | 6 | 2000-12-31 to 2023-12-31 |
| `penal-code` | Penal Code Act | 8 | 2000-12-31 to 2024-12-23 |

The build made 14 commits:

| Commits | Kind |
| ---: | --- |
| 2 | first version of an act |
| 10 | one law on its in-force day |
| 2 | changes no amendment note explains, credited to the publisher |

Other counts:
- 0 commits on the branch `future`: laws not yet in force on 2026-10-28.
- 0 commits dated 1 January 1970: in force before 1970, with the real day in their `In-force` trailer.
- 12 laws in the record.
- 24 tags.

## Dates

Each commit is dated at noon (Africa/Kampala) on the day the change took effect. The other dates, enacted and published, are trailers.

When a law gives no date of its own, the default rule applies: Not applied: every version is dated by ULII's own expression date, the day the amendment it incorporates took effect as Laws.Africa records it (for a consolidation, the date the revised edition is as at). No date is computed from a default rule. https://ulii.org/en/legislation/

## Commands, in order

```sh
# fill the cache from the sources listed above (network; Lexifina's fetch scripts are kept privately)
python -X utf8 tools/parse.py                  # cache -> corpus.json (no network)
python -X utf8 tools/build.py <folder> --repo <empty folder> --docs-date 2026-10-28
python -X utf8 tools/check_repo.py <repo> --corpus <folder>/corpus.json --write
python -X utf8 tools/build.py <folder> --repo <another empty folder> --docs-date 2026-10-28 --compare <repo>
```

In the main Lexifina repository these files live as follows:
- `fetch.py`, `parse.py` and `repo/`: in `scripts/uganda-law/`.
- `build.py`, `check_repo.py` (`check.py` there) and `on.py`: in `scripts/gitlaw_common/`, with the corpus format in `SCHEMA.md`.

## Exact inputs

- `corpus.json` sha256 `8ea8dee86f41670d83de38f15815d2894d4b12f30289b04ffe901559f592a3e1` (1373903 bytes)
- Script blob hashes (`git hash-object`):

| Script | Blob |
| --- | --- |
| build.py | `833a2433a3ea96fd87477ccc7a2ed47dc9e24b48` |
| check.py | `426d4cfb32ce103715be6a00865c0a7bca81a56a` |
| on.py | `644a6c0857fbcc72562032b58d57aa113fee0641` |
| fetch.py | `874ab51b280c3d1004749eb62de27fc7bc7352ec` |
| parse.py | `8e5d87718ac970c66b65f6d6a3ec124eb176f07d` |

- Tools:
  - Python 3.14.0
  - git version 2.52.0.windows.1
  - curl 8.21.0 (Windows) libcurl/8.21.0 Schannel zlib/1.3.2 WinIDN WinLDAP

## Checks

Not yet run for this build.

Not yet run for this build.

These results are from the check run on the build before this one, from the same corpus.

## Decisions made by hand

- Acts were chosen by what the archived sources support: every expression ULII lists for the Constitution (6) and the Penal Code Act (8) has an archived copy, so each version is read from its own dated expression.
- The Revised Laws 2023 (the Law Reform Commission's revised edition, as at 31 December 2023) renumbered chapters and revised wording throughout; ULII publishes it as a consolidation, and its changes are committed as the publisher's, not credited to any Act, unless ULII's own note names the Act.
- The Data Protection and Privacy Act 2019 was tried and dropped: ULII's current version of it is the Revised Laws 2023 expression (2023-12-31), which has no usable archived copy, so today's text could not be checked.
- Version dates are ULII's expression dates. Laws.Africa's terminology guide (https://docs.laws.africa/getting-started/terminology-guide) says "Amendments to Principal works come into force on the Commencement date of the Amending work" and that the first point in time is "the work as originally published"; so an amendment's expression is dated by its commencement (in force), and an act's original expression by its publication, which is replaced by the commencement date the page states.
- Credits: a version whose History names exactly one amending law (and no consolidation) between it and the previous version is credited to that law for every provision that changed. Otherwise a provision is credited only to laws that ULII's editorial note inside that provision links to; the rest are unexplained (publisher).
- Editorial notes (akn-remark) are left out of the text and used only as credit evidence, except where a provision has no other text (repealed or spent), where the note is the provision's whole printed content.
- Part, Chapter and Division headings are left out; each provision file starts with its own number and heading. Every other text of each version is in a provision file: parse.py checks this per version (verification.json, fidelity).

## What AI did and did not do

The fetch, parse and check scripts were written by Claude Code running Claude Opus 5.5 (`claude-opus-5-5`) under Lexifina's direction.

No model wrote, translated or corrected legal text. No model runs at build time. Every word of law in this repository comes from the official sources above, through code that anyone can rerun.

The commit messages are written by `build.py` from the source data.

Model use at data-build time:
- Claude Code (Claude Opus 5.5, claude-opus-5-5) wrote the adapter and configuration and chose the acts. No model wrote, summarised or transformed legal text: parse.py is deterministic code.
