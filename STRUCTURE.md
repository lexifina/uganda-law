# Structure

| Folder | What it holds |
| --- | --- |
| `constitution/` | The Constitution of the Republic of Uganda, 1995 |
| `laws/cap-NNN-<slug>/` | A chapter of the Revised Edition of the Laws of Uganda, 2000, by its chapter number, e.g. `laws/cap-266-accountants/` (Acts already filed under `acts/` from ULII are not repeated here) |
| `acts/<year>/<NNN>-<slug>/` | An Act (or an Ordinance or Decree still in force), by the year and number of the law that made it, e.g. `acts/1950/012-penal-code/`, `acts/2006/011-employment/` |

Each folder holds one file per section or article (`sec-102.md`; `sec-012-a.md` is section 12A) and per schedule
(`sch-01.md`), `long-title.md`, and a `README.md` listing its provisions. Acts whose PDF gives no number are filed as
`acts/<year>/<slug>/`. No folder holds more than 1,000 entries.

## Dates

Each version is one commit, dated 12:00 Africa/Kampala on the day it took effect, which its `In-force:` trailer
repeats. For the Acts from Parliament's PDFs, `In-force-basis:` says where that day comes from:

- `commencement`: the Act's own "Date of Commencement" line;
- `section-1`: the day section 1 names for the Act's coming into force;
- `revised-edition`: a chapter of the Revised Edition 2000, dated 31 December 2000, the day the edition is as at
  (its original commencement is in the `Commencement:` trailer).

An Act with neither (commencement by statutory instrument, or no date printed) is held until a reliable day is
found. No date in this repository is the day we downloaded anything.

## Text

`Text-source: publisher text layer` is the PDF's own text; `Text-source: publisher OCR` is the Parliament Library's
OCR layer over page images, taken as supplied (it may carry OCR errors). No OCR is run by us; PDFs that are page
images with no text layer are not included.
