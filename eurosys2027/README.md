# EuroSys 2027 revision

This directory is a separate revision of the original CAGE-S manuscript.
The original files at the repository root are unchanged. The revised paper
uses **Sentry** as a provisional review name and a substantially different
title because the original manuscript is publicly accessible.

**Status: edited review draft, not a verified submission-ready research artifact.**
The writing and layout have been revised; the scheduling experiments have
not been rerun. Read `AUTHOR_REVIEW.md` before submitting.

## Files

- `main.tex`: anonymous ACM SIGPLAN manuscript entry point.
- `main.pdf`: compiled review draft.
- `sections/`: revised manuscript text.
- `references.bib`: bibliography used by this version.
- `AUTHOR_REVIEW.md`: scientific findings, unresolved evidence, and submission checks.
- `VALIDATION.md`: build and document checks.

## Build

Upload the contents of this directory to Overleaf, select `main.tex`, and
use pdfLaTeX with the installed `acmart` class. Run BibTeX and compile twice
afterward if building locally. The verified local build used Tectonic:

```text
tectonic -X compile main.tex
```

The template uses two columns, a 7-by-9-inch text block, a 0.34-inch column
gap, and 10-point text with 12-point leading. Captions, tables, and references
use the body font size. The result tables are typeset directly, without
scaling their text. Recheck pagination after changing TeX distributions,
adding evidence, or editing the manuscript.

The original figures are not dependencies of this version: they repeat
tabulated measurements or the decision procedure, and some carry the public
system name. No data were reconstructed from those figures.

Only the PDF belongs in the paper-submission field. This author-facing
directory contains editorial information and is not an anonymous research
artifact. Do not publish a name-mapping README or an author-identifying
repository link as review material. AI assistance is disclosed in the PDF.
