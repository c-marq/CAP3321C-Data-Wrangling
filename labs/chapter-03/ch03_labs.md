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

## Dataset Summary (Used in Labs 2–8)

- **Ramen** (`ramen-ratings.csv`)  
  Ratings of ramen by brand, variety, style, and country.

- **Avocado** (`avocado.csv`)  
  Historical avocado prices and sales volume in U.S. markets.  
  Note: Columns `Unnamed: 0`, `4046`, `4225`, and `4770` are irrelevant for these labs. Regions overlap (e.g., TotalUS includes all others), but ignore overlap for these exercises.

- **Exams** (`exams.csv`)  
  Math, reading, and writing scores with student demographics (gender, race/ethnicity, parental education, lunch type, test prep course).

## Lab 3-1: Plot the ramen data with Pandas
**File:** `ramen-ratings.csv`

**Tasks**
1. Read data and show first five rows.
2. Histogram of Stars (bins for every 0.25 stars).
3. KDE plot of Stars.
4. Bar plot: average stars by style (group first).
5. Bar plot: total reviews by style.
6. Bar plot: highest score per style.

**Question**
1. Most common ramen style?

## Lab 3-2: Plot the avocado data with Pandas
**File:** `avocado.csv`

**Tasks**
1. Read data and show first five rows.
2. New DataFrame: total bags (Small + Large + XLarge) grouped by type.
3. Bar plot from grouped data (bag sizes by type).
4. Scatter plot: Total Volume vs AveragePrice.

**Questions**
1. Year with most bags sold?
2. Does higher total volume appear to lower average price?

## Lab 3-3: Plot the exam data with Pandas
**File:** `exams.csv`

**Tasks**
1. Read data and show first five rows.
2. Box plot using pandas `plot()`.
3. Create the specified plot (refer to book image).
4. Group by gender, mean scores, then bar plot.

**Questions**
1. Relationship between reading and writing scores?
2. Does lunch type affect average test scores?
