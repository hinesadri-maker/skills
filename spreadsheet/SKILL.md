---
name: "spreadsheet"
description: "Use whenever building, editing, or cleaning up a spreadsheet — a budget, tracker, applicant list, content calendar, or any tabular data in Google Sheets, Excel, or CSV. Trigger on 'make a spreadsheet', 'track this in a sheet', 'clean up this data', 'build me a tracker', or any request whose deliverable is rows and columns someone will sort, filter, or calculate with. Covers structure, formulas, and formatting so the result is usable, not just filled in."
---

# Spreadsheet

## Why this skill exists

A spreadsheet that just holds data is a table. A spreadsheet that's actually useful lets someone sort it, filter it, trust the totals, and hand it to someone else without a walkthrough. The gap between those two is a handful of habits — not talent, not a fancy template. This skill is that checklist.

## Step 1 — Decide the shape before typing a single cell

Ask (of yourself, or the user if it's not obvious): what will this sheet be used for six weeks from now? A one-time list needs none of this. A tracker someone will update weekly needs a structure that survives new rows without breaking.

- **One row = one thing.** Each row is a single record (one job application, one task, one expense). Never merge two records into one row to save space.
- - **One column = one fact, atomic.** Split "Sept 12, follow-up sent" into a date column and a status column. You cannot filter or sum a mixed field.
  - - **Headers are short and literal.** "Status" not "Current Status As Of Last Update." Match whatever term the user already uses out loud for that field.
    - - **No merged cells in the data body.** Merged cells break sorting and filtering silently. Reserve merges (if any) for a title row above the table, never inside it.
     
      - ## Step 2 — Build the columns that make it trackable, not just descriptive
     
      - Most sheets that fail to get used are missing one of these:
     
      - - **A status or stage column** with a fixed, short list of allowed values (e.g. `Applied / Interviewing / Offer / Rejected / Closed`), not free text. Free text status columns drift into ten spellings of the same thing within a month.
        - - **A date column** for anything with a timeline — applied date, due date, last updated. Use a real date type, not a typed string, so it sorts and calculates correctly.
          - - **An owner column** if more than one person touches the sheet.
            - - **A running total or count** if the point of the sheet is to know "how many" or "how much" at a glance — put it at the top in a summary row/cell, not buried at the bottom where it's easy to miss.
             
              - ## Step 3 — Formulas over hardcoded numbers
             
              - If a number can be calculated from other cells in the sheet, it should be a formula, not a typed-in result. A hardcoded total silently goes stale the moment a row changes.
             
              - - Totals, counts, and percentages: `SUM`, `COUNTIF`/`COUNTIFS`, `AVERAGE` referencing the actual range, not retyped numbers.
                - - Status-based counts (e.g. "how many applications are still open"): `COUNTIF(StatusColumn, "Applied")`.
                  - - Lookups across sheets: `VLOOKUP`/`INDEX+MATCH` in Excel, `VLOOKUP`/`QUERY` in Google Sheets — reference the source sheet, don't copy-paste values that will drift.
                    - - If you must hardcode a number because it came from outside the sheet (a quote, a fixed budget cap), label it clearly as an input — different color or a note — so it's not mistaken for a calculated cell.
                     
                      - ## Step 4 — Formatting that earns its keep, nothing decorative
                     
                      - Formatting should carry information, not just look nice.
                     
                      - - **Conditional formatting for status**, not manual cell coloring: color follows the status value automatically (e.g. green when Status = "Offer"), so it never goes stale when the value changes.
                        - - **Freeze the header row** on anything with more than ~15 rows, so headers stay visible while scrolling.
                          - - **Number formats match meaning**: currency as currency, percentages as percentages stored as true fractions (0.15, not 15, if the cell is percent-formatted), dates as dates.
                            - - **Column widths fit content** — no truncated headers, no giant empty columns.
                              - - Skip borders, background colors, and fonts that don't map to a piece of information. If you can't say what a formatting choice communicates, cut it.
                               
                                - ## Step 5 — Sanity-check before handing it over
                               
                                - - Do the totals/counts actually match a manual spot-check of a few rows?
                                  - - Sort and filter by every column that should be sortable — does it behave sensibly, or does a merged cell or mixed data type break it?
                                    - - Would a new column heading make sense to someone who didn't build the sheet?
                                      - - If it's a template for someone else to fill in, is there one example row showing the expected format, clearly marked as an example (not real data)?
                                       
                                        - ## The boundary of this skill
                                       
                                        - This skill covers structure, formulas, and formatting for a usable spreadsheet. It does not cover:
                                        - - Building charts or dashboards from the data — that's a data visualization task.
                                          - - Complex financial modeling (scenario analysis, multi-tab models with cross-links) — that calls for a dedicated financial-model workflow.
                                            - - Automating a sheet with scripts (Apps Script, macros) — that's a scripting task layered on top of a well-structured sheet, which is what this skill gets you to first.
