# Project Notes — Hypermarket Store Data Analysis

These are my personal working notes while doing this project. Keeping this mainly for my own
reference (and in case I forget why I did something a particular way when I revisit this later 😅).

---

## Why I picked this project

Wanted a project for my resume/portfolio that shows I can take raw, messy-ish sales data and turn
it into something a store manager could actually look at and understand in 2 minutes. Most of my
coursework this sem is heavy on theory (DBMS, ML math etc.), so I wanted something practical on
the side. Excel felt like the right starting point before jumping into Power BI/Tableau — almost
every company still uses Excel somewhere, so better to be solid at it first.

Dataset: found a fashion/apparel store sales dataset (~31k rows, year 2022). Renamed the project
"Hypermarket Store Data Analysis" for my own notes since the process is basically identical to
what you'd do for a general retail/hypermarket store — not specific to clothing.

---

## Step-by-step log

### Day 1 — Getting familiar with the data
- Opened raw file, ~31k rows, 19 columns.
- First instinct: just eyeball it. Noticed:
  - Some state names had inconsistent casing (e.g., mixed with extra spaces).
  - `Date` column wasn't uniformly formatted.
  - Age column had some outliers (need to sanity check later — is age 90+ realistic for this
    kind of store? probably a few odd entries, didn't remove them since they weren't clearly
    wrong, just unusual).
  - `B2B` column is mostly False — very few B2B orders, could exclude from "customer" analysis
    later but decided to keep in for now since it doesn't change insights much.

**Doubt to self:** should missing/blank cells be dropped or imputed? → Decided: for this dataset,
almost all key columns (gender, amount, category) were complete, so didn't need heavy imputation.
Just cleaned text formatting mostly.

### Day 2 — Cleaning
- Made a copy of the raw sheet → `Data Cleaning` sheet, never touched the raw sheet again
  (good habit, always keep raw data untouched, learned this the hard way on a previous
  assignment where I overwrote original data 🙃).
- Standardized `ship-state` text (trim spaces, consistent uppercase).
- Converted `Date` to proper Excel date type using Data > Text to Columns (some dates were
  stored as text, took me a while to realize why my pivot table dates weren't sorting right —
  classic mistake, should check data types FIRST next time before building anything on top).
- Added `Month` column using `=TEXT(Date,"mmm")` — needed this for the monthly trend chart.
- Added `Age Type` column using nested `IF` to bucket ages into Teenager / Adult / Senior. Had to
  decide age cutoffs myself since dataset didn't specify — went with a reasonable split.

### Day 3 — PivotTables
- Built pivots one at a time on separate sheets instead of cramming everything onto one pivot —
  much easier to manage and debug.
- Learned: `Sum of Amount` vs `Count of Order ID` give very different stories — a channel might
  have more orders but lower total revenue. Kept both wherever it made sense (esp. Channels
  sheet).
- Order Status pivot: good reminder that "Cancelled" and "Returned"/"Refunded" are different
  things and should be reported separately, not clubbed as "not delivered."

### Day 4 — Dashboard
- Combined everything onto one dashboard sheet with charts + slicers.
- Struggled a bit with chart formatting — default Excel chart colors don't look great, spent
  more time than expected making it presentable (fonts, colors, alignment). Worth it though,
  looks way more "dashboard-like" now instead of a random pile of charts.
- Added slicers so the dashboard is filterable by month/channel — makes it interactive instead
  of static.

### Day 5 — Wrap-up
- Recorded a small walkthrough video (linked inside the workbook) explaining the dashboard —
  good practice for explaining insights out loud, something I need to get better at for
  interviews.
- Wrote this README + notes, pushed to GitHub.

---

## Things I'd do differently next time

- Do data type checks (dates, numbers stored as text) as the very FIRST step, before anything
  else. Wasted time debugging a pivot table issue that was actually a data type issue.
- Maybe use Power Query instead of manual formulas for cleaning — more scalable and repeatable
  if data updates.
- Document formulas better as I go, instead of at the end (had to re-derive what a couple of
  formulas were doing when writing this file).

---

## Random learnings / TIL

- `TEXT()` formula is super useful for extracting Month/Year from a date without changing the
  underlying date value.
- Pivot tables refresh needs a manual "Refresh All" if source data changes — doesn't auto-update.
- Slicers only work properly when connected to a proper Table/PivotTable, not raw ranges.
- Keeping raw data, cleaned data, and dashboard in separate sheets (not overwriting anything)
  makes the whole project much easier to explain to someone else later.

---

## To-do / ideas for v2

- [ ] Try the same analysis in Power BI, compare how much faster/cleaner it is
- [ ] Learn Python (pandas) to automate the cleaning step
- [ ] Add YoY comparison once more years of data are available
- [ ] Get feedback from seniors on dashboard design (colors/layout)
