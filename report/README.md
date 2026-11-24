# Report draft

`report.html` is the source and `report.pdf` is the output. The figures come straight from `../models/outputs/figures/`.

Current draft: 855 words (this includes the title and headings; tables, figures, captions and references are excluded). The body fills 4 pages and the references end on page 5. It is A4, two columns, with everything at 11 pt or above.

## Rebuild after editing

Run this from the `report/` folder:

```bash
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless=new --no-pdf-header-footer --print-to-pdf="$PWD/report.pdf" "file://$PWD/report.html"
```

## Still to do before submitting (Fri 27 Nov, 11:59 PM)

1. **Make the repo public** (or give the lecturer access). It is private, so the code link in the report won't open.
2. **Farhana:** add the IMF historical comparison where the yellow box in Section 5 sits.
3. **Parthiban:**
   - Add 2-3 papers to Section 3.
   - Add error by income group and region to Section 6, using `models/outputs/predictions_all_models.csv`.
   - Verify the references.
4. **Sukesh:** check the EDA numbers in Section 2 against a fresh run of his notebook.
5. **Everyone:**
   - Rewrite your own section in your own words.
   - Stay under 1,000 words (about 140 are left).
   - Remove every yellow box, rebuild, and check the page count is still 5 or fewer.
