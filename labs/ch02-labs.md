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
