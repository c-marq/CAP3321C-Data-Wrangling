## General Guidelines

### Data files supplied by your instructor
- Each lab uses a data file (usually CSV). Your instructor will provide these files.

### Notebooks created by you
- Create one Google Colab notebook per lab.
- Name notebooks using your instructor's convention or `first_last_lab_X-X`.
- Import required modules at the start.
- Use separate code cells for each task/question.
- Add comments to explain your thinking and complex code.
- Use Markdown cells for headings and organization.

## Dataset Summary

- **Ramen** (`ramen-ratings.csv`)  
  Ratings of ramen by brand, variety, style, and country.

- **Avocado** (`avocado.csv`)  
  Historical avocado prices and sales volume in U.S. markets.  
  Note: Columns `Unnamed: 0`, `4046`, `4225`, and `4770` are irrelevant for these labs. Regions overlap (e.g., TotalUS includes all others), but ignore overlap for these exercises.

## Lab 8-1: Analyze the ramen data
**File:** `ramen-ratings.csv`

**Tasks**
1. Read data and show first five rows.
2. Group to match book average table (refer to image).
3. Same grouping with both mean and count.
4. Pivot table: average stars by style for each country.
5. Total stars per country → rank descending.
6. Bin Stars into 11 bins (0.0–5.0 step 0.5); show counts.
7. Bin Stars into 5 quantiles with descriptive labels; show counts.

**Questions**
1. Top five countries by total stars?
2. Only country producing canned ramen?

## Lab 8-2: Analyze the avocado data
**File:** `avocado.csv`

**Tasks**
1. Read data and show first five rows.
2. Check Date column type.
3. Convert Date to datetime.
4. Filter: 2015, conventional, Albany → keep Date, Total Bags, Small Bags.
5. Melt Total Bags & Small Bags → columns Bags and Count.
6. Line plot of melted data (hue by bag type).
7. Bin Total Volume into 4 quantiles: poor, modest, good, excellent.
8. Count plot of binned volume by year.

**Questions**
1. Which bag size (Small/Large/XLarge) sells most overall?

2. Which avocado type (organic/conventional) sells more?
