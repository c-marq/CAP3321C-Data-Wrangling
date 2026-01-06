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

## Lab 6-1: Clean the ramen data
**File:** `ramen-ratings.csv`

**Tasks**
1. Read data; note row count.
2. Rename Stars → Rating.
3. Convert Style to category type.
4. Drop Country column.
5. Verify changes.
6. Rename Brand → Company, Variety → Product.
7. Show duplicate Company/Product rows.
8. Drop duplicates (keep first), compare row count.
9. Drop rows with any missing values.
10. Final verification.

## Lab 6-2: Clean the avocado data
**File:** `avocado.csv`

**Tasks**
1. Read data and show first five rows.
2. Check for missing values.
3. Show unique regions (note TotalUS).
4. Drop TotalUS rows; report rows dropped.
5. Drop columns: Unnamed: 0, 4046, 4225, 4770.
6. Convert Date to DateTime.
7. Verify changes.
