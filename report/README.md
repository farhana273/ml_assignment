# Report

`report.html` is the source and `report.pdf` is the output. The figures come straight from `../models/outputs/figures/`.

Current version: 978 words (title, headings and abstract included; tables, figures, captions and references excluded). 5 pages, A4, two columns, everything at 11 pt or above.

## Rebuild after editing

Run this from the `report/` folder:

```bash
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless=new --no-pdf-header-footer --print-to-pdf="$PWD/report.pdf" "file://$PWD/report.html"
```

## Before submitting (Fri 27 Nov, 11:59 PM)

1. Make sure the marker can open the code link (public repo or lecturer access).
2. Everyone: read your own section and reword it in your own words; stay under 1,000 words and 5 pages.
