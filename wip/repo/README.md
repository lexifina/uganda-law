# Uganda: law history in git

The law of Uganda as a git history: one file per provision, one commit per law on the day it took effect, and the law that made each change as the commit's author. `git blame` names the law behind every paragraph; `git log` lists every change to a provision; `tools/on.py` gives the text in force on any day.

It follows the shared design of [lexifina/global-law](https://github.com/lexifina/global-law), which places it at `ug/`. Every version is a dated point-in-time version published by [ULII](https://ulii.org) on the Laws.Africa Peachjam platform.

**What is in it now**

| Folder | Act | Versions | History |
| --- | --- | ---: | --- |
| `constitution/` | [Constitution of the Republic of Uganda](https://ulii.org/akn/ug/act/statute/1995/constitution) | 6 | 2000-12-31 to 2023-12-31 |
| `penal-code/` | [Penal Code Act](https://ulii.org/akn/ug/act/ord/1950/12) | 8 | 2000-12-31 to 2024-12-23 |

**Constitution of the Republic of Uganda**

| In force | Author |
| --- | --- |
| 2000-12-31 | publisher (ULII): oldest version available |
| 2005-09-30 | Act 11 of 2005 |
| 2005-12-30 | Act 21 of 2005 |
| 2015-08-24 | Act 12 of 2015 |
| 2018-01-05 | Act 1 of 2018 |
| 2023-12-31 | publisher (ULII): 255 provision(s) unexplained |

**Penal Code Act**

| In force | Author |
| --- | --- |
| 2000-12-31 | publisher (ULII): oldest version available |
| 2002-06-07 | Chapter 120 |
| 2007-08-17 | Act 8 of 2007 |
| 2009-08-25 | Chapter 116 |
| 2010-09-03 | Act 17 of 2010 |
| 2014-05-09 | Act 1 of 2014 |
| 2023-12-31 | publisher (ULII): 389 provision(s) unexplained |
| 2024-12-23 | General Notice 2917 of 2024 |

Each folder's `README.md` lists every provision, how often it changed and when.

## A lawyer's questions as git commands

| Question | Command |
| --- | --- |
| What did sec-005 say on 2000-12-31? | `python tools/on.py 2000-12-31 constitution sec-005` |
| The same, with raw git (bash) | `git show $(git rev-list -1 --before="2000-12-31T23:59:59Z" main -- constitution/sec-005.md):constitution/sec-005.md` |
| The same, in PowerShell | `$r = git rev-list -1 --before="2000-12-31T23:59:59Z" main -- constitution/sec-005.md; git show "$($r):constitution/sec-005.md"` |
| Which law wrote each line? | `git blame constitution/sec-005.md` |
| Every change, word by word | `git log -p --word-diff constitution/sec-005.md` |
| Every law in the record, in order | `git log --reverse --format="%ad %an" --date=short main` |
| Everything one law changed | `git show law/<key>` (tags `law/<key>` mark each law's commit) |
| The whole act on a date | `python tools/on.py 2000-12-31 constitution` |
| Which law gave a provision its wording on a date | `python tools/on.py --law 2000-12-31 constitution sec-005` |

After a rebuild, refresh tags with `git fetch --force --tags`: a plain fetch keeps stale tags.

## Dates

- Each commit is dated at **noon, Africa/Kampala, on the day the change took effect**. The day is also in the `In-force:` trailer, which the tools read; enactment (assent) and Gazette publication dates are trailers too, where ULII states them.
- **The day is ULII's.** Each version is a Laws.Africa expression, and its date is the day the amendment it takes in came into force, as the amendment list says ("[Amended by <Act> on <date>]"). For a consolidation (a revised edition) it is the date the edition is as at. An act's original expression is dated by its Gazette publication; where ULII gives a later commencement date ("Commenced on ..."), the first version is dated by that instead (see REPRODUCE.md, decisions).
- `--before="YYYY-MM-DD"` alone uses your clock's time of day, so a law that took effect that day may be missed before noon. Use `T23:59:59Z` as above, or the tool.

## How it is checked

- Every version is read back from git on the day it took effect and on the day before (`tools/check_repo.py`); both must match `corpus.json`. Results are in `REPRODUCE.md`.
- **Against ULII today:** the last version of each act is ULII's current expression, as named by its own legislation listing on the retrieval day, and is the text of that expression page.
- **Every version is its own dated expression**: each was parsed from an archived copy of exactly that expression's page, whose sha256 is recorded with the version.
- The repository is rebuilt from the same data a second time and must give identical hashes.

## What "author" means

The author of a commit is the law that made the change, with an e-mail address that cannot exist, so `git blame` and `git log --author` name laws. The committer is always Lexifina.

- **Credits come only from ULII's own notes.** A version whose History entry names one amending Act is credited to it. Where one version takes in several Acts, or a revised edition, a provision is credited to an Act only if ULII's editorial note in that provision names it ("[section 5 amended by section 2 of Act 3 of 2020]"); the rest are committed by the publisher and labelled "unexplained", and the commit message names the Acts the version takes in.
- **The first commit** is the act as enacted where that is the oldest version; otherwise it is the oldest version available (a consolidation), credited to the publisher.
- Blame credits whole lines (one paragraph per line). Use `git log -p --word-diff` to see exactly which words each change made.

## What it does not show

- **Only the versions ULII publishes.** Changes before its oldest version are not separate commits.
- **Editorial notes.** ULII's bracketed notes ("[Act No. 18 of 1996]", "[section 5 amended by ...]") are left out of the text and used only for credits, except where a provision has no other text (repealed or spent), where the note is what ULII prints and is kept.
- **Headings above the provision** (Part, Chapter, Division) are left out; each file starts with its own number and heading. Footnotes are kept at the end of the file.
- **Amendments not yet applied.** Where the LII lists an amendment as not yet applied to its consolidated text, it is not in this history; REPRODUCE.md lists each one.
- **No OCR.** Acts the LII shows only as scanned PDFs are not included.

## How it is built


## Sources

| Source | What it gives | Used for |
| --- | --- | --- |
| [ULII](https://ulii.org) | Dated point-in-time versions (expressions) of each act, its History and amendment list, and per-provision editorial notes; its listing page names the current version | The text and dates of every version |
| [Internet Archive](https://web.archive.org/) | Archived copies of those expression pages | Reading them |

## Licence

See [LICENSE](LICENSE). Source: ULII, the Uganda Legal Information Institute (https://ulii.org), licensed under the Creative Commons Attribution-NonCommercial 4.0 International licence (CC BY-NC 4.0).

ULII's terms: CC BY-NC 4.0, crediting ULII as the source (https://ulii.org/en/terms-of-use/). Lexifina's arrangement, messages, tables and tools are CC0.

This repository is not legal advice. Uganda's laws are published in English, so there is no separate summary in another language.
