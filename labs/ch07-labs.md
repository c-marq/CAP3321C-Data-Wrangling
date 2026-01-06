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

## Lab 7-1: Prepare the ramen data
**File:** `ramen-ratings.csv`

**Tasks**
1. Read data and show first five rows.
2. Add column with country average rating.
3. Group by Country & Style → mean → unstack Style (show Stars).
4. Write function: shorten Variety to first two words + " …".
5. Apply function → new column ShortVariety.
6. Set Brand as index.
7. Reset index.

## Lab 7-2: Prepare the avocado data
**File:** `avocado.csv`

**Tasks**
1. Read data and show first five rows.
2. Standardize column names to Title Case (no spaces).
3. Add columns: % XLarge, % Large, % Small of TotalBags.
4. Show first five rows with new columns.
5. New DataFrame: Region, Type, Year, TotalBags.
6. Group, sum, unstack to match book table (refer to image).
