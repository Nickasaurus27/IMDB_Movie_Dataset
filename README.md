# Movies – Correlation & Box Office Performance

This project explores what drives box office performance for movies using a dataset of ~5,000 films.  
The goal is to **identify which features (budget, genre, IMDb score, votes, runtime, etc.) are most strongly associated with box office gross** and to practice a full end-to-end analytics workflow in Python.

> **Tech stack:** Python, pandas, NumPy, seaborn, matplotlib, Jupyter Notebook

---

## Project Overview

As part of my data portfolio, this project demonstrates how I:

- Clean and prepare a real-world dataset with missing values and mixed data types  
- Engineer features and convert columns into analysis-friendly formats  
- Explore relationships between variables using visual and statistical correlation analysis  
- Communicate insights with clear visuals and narrative commentary

The central question:

> **Which movie characteristics are most closely associated with higher box office revenue?**

---

## Dataset

The dataset (`movies.csv`) contains one row per movie with the following selected columns:

- `name` – Movie title  
- `rating` – MPAA rating (e.g., PG, R)  
- `genre` – Primary genre  
- `year` – Original year field  
- `released` – Release date  
- `year_new` – Cleaned year extracted from `released`  
- `score` – IMDb user rating  
- `votes` – Number of IMDb votes (popularity proxy)  
- `director`, `writer`, `star` – Key creative roles  
- `country` – Country of origin  
- `budget` – Production budget  
- `gross` – Worldwide box office gross  
- `company` – Production company or studio  
- `runtime` – Movie runtime in minutes  

---

## Key Questions

In the notebook, I explore:

1. **Do bigger budgets actually lead to higher box office revenue?**  
2. **Are higher IMDb scores associated with higher revenue?**  
3. **Is popularity (number of votes) a better predictor than the score itself?**  
4. **How do different genres compare in terms of average budget and gross?**  
5. **Have movies tended to get bigger (budget/gross) over time?**

---

## Methods & Approach

1. **Data loading & initial inspection**
   - Load `movies.csv` into a pandas DataFrame
   - Inspect schema, data types, and missing values with `.info()`, `.describe()`, and `.head()`

2. **Data cleaning**
   - Handle missing values: drop rows with critical nulls in `budget`, `gross`, `votes`, or `score`
   - Convert numeric columns (`budget`, `gross`, `votes`) to integer types
   - Replace inconsistent `year` values with the corrected `year_new` and drop the original `year` column
   - Check for and remove duplicate rows

3. **Exploratory data analysis (EDA)**
   - Sort by `gross` to inspect top-earning films
   - Summarize distributions for `budget`, `gross`, `score`, `votes`, and `runtime`
   - Group by `genre` to compare average budget, gross, and score

4. **Correlation analysis**
   - Compute a correlation matrix for numeric features (`budget`, `gross`, `votes`, `score`, `runtime`, `year_new`)
   - Visualize correlations with a heatmap
   - Flatten and sort correlation pairs to identify the strongest relationships (e.g. `budget` vs `gross`, `votes` vs `gross`, `votes` vs `score`)

5. **Visualization**
   - Scatter plots with regression lines for:
     - `budget` vs `gross`
     - `votes` vs `gross`
     - `score` vs `gross`
   - Bar charts comparing average `gross` and `score` across genres

---

## Key Findings (Story Highlights)

Some of the main takeaways from the analysis:

- 🎬 **Budget and box office revenue are strongly correlated.**  
  Movies with higher production budgets tend to earn more at the box office (correlation ~0.74 between `budget` and `gross`).

- ⭐ **Popularity (votes) is more predictive of gross than the IMDb score itself.**  
  - `votes` vs `gross` shows a strong positive relationship (~0.61)  
  - `score` vs `gross` is noticeably weaker (~0.22)  
  This suggests that how many people watch and rate a movie matters more for revenue than the average rating they give.

- 🍿 **Well-rated movies do tend to attract more engagement.**  
  There is a moderate positive correlation between `score` and `votes` (~0.47), indicating well-rated films usually have more audience traction.

- 🎭 **Genres differ in financial profile.**  
  - Action, Adventure, and Animation titles typically have **higher budgets and higher average gross**  
  - Drama and Comedy are more numerous but generally operate with **lower budgets and lower gross** on average

These relationships are illustrated and discussed in detail in the Jupyter notebook.

---

## Repository Structure

Suggested structure for this project:

```text
.
├── data
│   └── movies.csv
├── notebooks
│   └── movies_correlation.ipynb
└── README.md
