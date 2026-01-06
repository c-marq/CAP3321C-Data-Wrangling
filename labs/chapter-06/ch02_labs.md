# Murach’s Python for Data Analysis - Student Labs (Chapters 2–8)

These labs let you practice the skills from chapters 2 through 8 of *Murach’s Python for Data Analysis*.

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

## Lab 2-1: Analyze the ramen data
**File:** `ramen-ratings.csv`

**Tasks**
1. Read the CSV into a DataFrame.
2. Display the first five rows.
3. Display the last five rows.
4. Use `describe()` for numeric columns.
5. Show unique value counts per column.
6. Filter rows where Country is Vietnam.
7. Select only Brand and Style columns.
8. Select only the Country column.
9. Sort by Stars (high to low).
10. Replace "USA" with "United States" in the Country column (in place) and show first five rows.

**Questions**
1. How many countries are represented?
2. Top three countries by average rating?
3. Bottom three countries by average rating?
4. Top three countries by number of brands (and count)?

## Lab 2-2: Analyze the avocado data
**File:** `avocado.csv`

**Tasks**
1. Read the CSV into a DataFrame.
2. Use `info()` to show types, memory, and null counts.
3. Show unique value counts per column.
4. Display default number of rows shown in Colab.
5. Show first/last five rows and first/last four columns.
6. Select any three columns with bracket notation (first five rows).
7. Select one column with dot notation.
8. Create `EstimatedRevenue` = `Total Volume` × `AveragePrice`; show first five rows.
9. Group by region and type, compute mean price, reset index, show first five rows.
10. Bar plot of mean, median, and std of Total Volume by year.

**Questions**
1. How many unique regions?
2. Average price for organic vs conventional avocados?
3. Region with lowest average price for organic avocados?
4. Has consistency of Total Bags sold per year (by type) increased or decreased?

## Lab 2-3: Analyze the exam data
**File:** `exams.csv`

**Tasks**
1. Read CSV and show first five rows.
2. Use `info()`.
3. Use `describe()` on score columns.
4. Group by race/ethnicity and show mean scores.
5. Select one column as DataFrame (brackets).
6. Select one column as Series (brackets).
7. Select one column as Series (dot notation).
8. Filter females with math score ≥ 90.

**Questions**
1. Does test preparation course improve average scores?
2. Which gender has higher average math score?
3. Which gender has higher average across all subjects? (Hint: add total score column)
4. Does parental education level affect average scores?

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

## Lab 5-1: Get different types of data

**Tasks**
1. Read Thanksgiving 2015 CSV from:  
   https://raw.githubusercontent.com/fivethirtyeight/data/master/thanksgiving-2015/thanksgiving-2015-poll-data.csv
2. Read Stata cancer data:  
   http://www.stata-press.com/data/r8/cancer.dta
3. Read SF Salaries CSV from Kaggle (requires account):  
   https://www.kaggle.com/kaggle/sf-salaries
4. Find and load a Kaggle dataset of personal interest (or a trending one).

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