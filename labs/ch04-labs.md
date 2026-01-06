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

- **Exams** (`exams.csv`)  
  Math, reading, and writing scores with student demographics (gender, race/ethnicity, parental education, lunch type, test prep course).

## Lab 4-1: Plot the ramen data with Seaborn
**File:** `ramen-ratings.csv`

**Tasks**
1. Read data and show first five rows.
2. Bar plot: Stars by Style (Seaborn-specific method).
3. Same bar plot using Seaborn generic method.
4. Add custom title and x-axis label to previous plot.
5. Filter to Japan, India, Taiwan, United States → subplot (2 per row) of stars by style per country.
6. Add custom title to each subplot (use `enumerate()`).

## Lab 4-2: Plot the avocado data with Seaborn
**File:** `avocado.csv`

**Tasks**
1. Read data and show first five rows.
2–5. Create the specified Seaborn plots (refer to book images for exact appearance, including hue=year and size variation).

## Lab 4-3: Plot the exam data with Seaborn
**File:** `exams.csv`

**Tasks**
1. Read data and show first five rows.
2. `catplot()` count plot (refer to book image).
3. Rotate x-labels for readability.
4. Scatter: writing vs reading score, hue by test prep course (specific method).
5. Same scatter using general Seaborn method.
6. Adjust figure size of general method plot to match specific method.
