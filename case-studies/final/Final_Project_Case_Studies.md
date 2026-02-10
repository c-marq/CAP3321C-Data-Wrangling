# CAP3321C — Data Wrangling with Python

## Final Project: Case Study Assignments

This document describes three case study options for your final project. You and your partner will select **one** case study and complete both Section 1 and Section 2 for that case study. Each case study asks you to apply the data wrangling and analysis skills covered in Chapters 1–8 of the course. You will also present your findings to the class in a 10-minute presentation. This project is worth **200 points**.

---

## Contents

1. [General Guidelines](#general-guidelines)
2. [The Airports Case Study — Section 1](#the-airports-case-study--section-1)
3. [The Airports Case Study — Section 2](#the-airports-case-study--section-2)
4. [The Laptops Case Study — Section 1](#the-laptops-case-study--section-1)
5. [The Laptops Case Study — Section 2](#the-laptops-case-study--section-2)
6. [The Medical Costs Case Study — Section 1](#the-medical-costs-case-study--section-1)
7. [The Medical Costs Case Study — Section 2](#the-medical-costs-case-study--section-2)

---

## General Guidelines

### Partner Selection

- This is a **partner project**. Select one partner to work with for the duration of the final project.
- Together, decide which case study you will work on.
- Each partner is responsible for contributing meaningfully to the shared Notebook.

### Choosing a Case Study

- With your partner, choose **one** of the three case studies: **Airports**, **Laptops**, or **Medical Costs**.
- Your chosen case study has two sections. One partner will complete Section 1 and the other will complete Section 2.

### Data Files Supplied by Your Instructor

- The data files needed for each case study are identified in the specifications below. These files will be made available to you on the course site.

### Notebook Created by You

- All work must be completed in **Google Colab**.
- Create **one shared Notebook** in Google Colab for your team. One partner should create the Notebook and share it with the other partner so both can edit it — just like a Google Doc.
- It is recommended that you begin the assignment together — review the data, discuss your approach, and agree on how you will clean and prepare the data. Then, divide the work so that **one partner completes Section 1** and the **other partner completes Section 2**.
- Use **Code cells** to store the code for your analysis.
- Use **Markdown cells** to create headings that organize your Notebook and to provide short answers to questions.
- Use **Raw cells** to store longer sections of raw text.
- Use comments or raw text to describe your thought process and to document any code that is hard to understand.

### Submission

- When the Notebook is complete, each partner downloads their own copy: go to **File > Download > Download .ipynb**.
- Rename the downloaded file using this convention: **first_last_CAP3321_final.ipynb** (e.g., **maria_garcia_CAP3321_final.ipynb**).
- Each partner submits their own renamed copy individually.
- In a Markdown cell at the top of your Notebook, include: both partners' names, the case study title, and who was responsible for which section.

### Presentation

- Each team will present their findings to the class. Presentations should be **10 minutes maximum**.
- Both partners must participate in the presentation, but the split does not need to be equal — as long as both contribute meaningfully.
- You may present using your Notebook directly (scrolling through code and output) or prepare a few summary slides — whichever best communicates your findings.
- Focus on **what you found**, not just **what you did**. Walk the audience through your key insights, not every line of code.

### Grading

- This project is worth **200 points**. See the accompanying **Final Project Rubric** for a detailed breakdown of how your Notebook and presentation will be evaluated.

---

## The Airports Case Study — Section 1

**Prerequisite chapters:** 2–4

### Data File

[tsa_claims1.csv](https://drive.google.com/file/d/1dhzcM38W6QHUoetkFgT-epZR6tVdwY_U/view?usp=sharing)

### Scenario

You are analysts employed by the U.S. Transportation Security Administration (TSA). Your boss has asked you to produce a report that answers the following questions about insurance claims against airports in the U.S.

### Questions

- What is the most common type of insurance claim?
- Which claim site within the airport are claims most commonly filed for?
- What type of claim is made most at each claim site?
- What is the typical claim amount?
- What is the overall claim approval rate for the entire U.S.?

### Instructions

1. Create a Notebook for the study.
2. Clean the data and explain why you cleaned it the way you did.
3. Create a heading for the first question.
4. If necessary, perform additional cleaning or preparation for the question.
5. Create a table or plot that answers the question and use a heading or raw text to summarize what the table or plot tells you.
6. Repeat steps 3–5 for each question.

> **Note:** If you encounter warnings or errors as you work on this case study, search the Internet for a solution to the problem and implement it.

---

## The Airports Case Study — Section 2

**Prerequisite chapters:** 2–8

### Data Files

- [tsa_claims2.csv](https://drive.google.com/file/d/1hIOkuqUjSEhv1nWq753lJlc1E3FMIyun/view?usp=sharing)
- [GlobalAirportDatabase.txt](https://drive.google.com/file/d/1mLNP6DuwpNRLPVtigcvCdzxTXnB_U4Nh/view?usp=sharing)
- [maps/states](https://drive.google.com/drive/folders/14HbcVp1DMF9Iq3RmFpogohE0ZyFEBJmX?usp=sharing) (the shape files for the U.S. map)

### Scenario

Your boss liked your previous report so much that he wants you to expand on it by completing the specified tasks and answering some additional questions!

### Tasks and Questions

- Read the data from the **tsa_claims2.csv** file, not the tsa_claims1.csv file.
- Clean the data more thoroughly:
  - Drop all rows that contain NA values.
  - Store the numeric columns with the float type.
  - Store the date columns with the datetime type.
- Make sure the questions you answered for Section 1 still work.
- Answer these new questions:
  - If a claim is approved or settled, what percent of the claim amount do the airports pay?
  - What are the five airports with the most claims?
  - Has the total close amount increased or decreased over time?
- Create a map that shows the location of each airport in the continental U.S. and changes the size of the airport's dot depending on its number of claims. To do that, use GeoPandas as described in the course materials.

### Instructions

1. Add heading and code cells to the Notebook that you created for Section 1 so that it answers the questions shown above.
2. Improve the Notebook that you created for Section 1. To do that, you can use skills that you learned in Chapters 5–8 to simplify the earlier code you wrote that answers the Section 1 questions.

---

## The Laptops Case Study — Section 1

**Prerequisite chapters:** 2–4

### Data File

[laptops.csv](https://drive.google.com/file/d/1TorYOf9hRtIMp_L8jVniiaSFtBtlc5Ou/view?usp=sharing)

### Scenario

You are analysts employed by a computer hardware company. Your company will be entering the laptop market soon. Your boss has asked you to produce a report that answers the following questions about laptops to help your company better understand the market.

### Questions

- How many different laptop brands are there?
- What are the names and prices of the most and least expensive laptops?
- How are laptop prices distributed?
- What are the min, max, and mean display sizes?
- What is the average price for each brand?

### Instructions

1. Create a Notebook for the study.
2. Add a heading for the first question.
3. If necessary, perform additional cleaning or preparation for the first question.
4. Create a table or plot that answers the question and use a heading or raw text to summarize what the table or plot tells you.
5. Repeat steps 2–4 for each question.

---

## The Laptops Case Study — Section 2

**Prerequisite chapters:** 2–8

### Data File

[laptops.csv](https://drive.google.com/file/d/1TorYOf9hRtIMp_L8jVniiaSFtBtlc5Ou/view?usp=sharing)

### Scenario

Your boss liked your previous report so much that she wants you to expand it by completing the following tasks and answering the following questions.

### Tasks and Questions

- Clean the data.
- What is the average laptop price for each processor brand?
- What are the average ratings for each laptop brand?
- What is the average laptop price for each graphics card brand?
- How many laptops have a discount price?
- How is disk space related to the price?
- How is display size related to price?

### Instructions

Add heading and code cells to the Notebook that you created for Section 1 so that it completes the tasks and answers the questions shown above.

---

## The Medical Costs Case Study — Section 1

**Prerequisite chapters:** 2–4

### Data File

[insurance.csv](https://drive.google.com/file/d/1AnNsDBCn0T_HFINVxp2a7RdxvOP5x6Vt/view?usp=sharing)

### Scenario

You are analysts employed by a health care company. Your boss has asked you to produce a report that answers the following questions about medical insurance charges.

### Questions

- How is age related to medical costs?
- How is number of children related to medical costs?
- How is the number of people distributed by region?
- How is the number of people distributed by age?
- How are the charges distributed?

### Instructions

1. Create a Notebook for the study.
2. Create a heading for the question.
3. If necessary, perform additional cleaning or preparation for the first question.
4. Create a table or plot that answers the question and use a heading or raw text to summarize what the table or plot tells you.
5. Repeat steps 2–4 for each question.

> **Note:** If you encounter warnings or errors as you work on this case study, search the Internet for a solution to the problem and implement it.

---

## The Medical Costs Case Study — Section 2

**Prerequisite chapters:** 2–8

### Data File

[insurance.csv](https://drive.google.com/file/d/1AnNsDBCn0T_HFINVxp2a7RdxvOP5x6Vt/view?usp=sharing)

### Scenario

Your boss liked your previous report so much that he wants you to expand on it by completing the following tasks and answering the following questions.

### Tasks and Questions

- Bin the bmi column. To do that, search the Internet to determine how you should bin and label the data.
- How are the charges related to the bmi?
- How is the smoker status related to the charges?
- How are the charges related to the region?
- Which region has the highest obesity percentage?

### Instructions

Add heading and code cells to the Notebook that you created for Section 1 so that it completes the tasks and answers the questions shown above.
