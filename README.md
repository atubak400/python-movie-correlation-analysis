# Python Movie Correlation Analysis

This project explores the relationships between movie features such as budget, gross revenue, votes, ratings, and other attributes using exploratory data analysis and correlation techniques in Python.

The aim of this project is to identify which factors are most strongly associated with box office success.

---

## Project Overview

Using a movie dataset, this project performs:

- Exploratory Data Analysis (EDA)
- Scatter plots and regression visualisations
- Correlation analysis using Pearson correlation
- Heatmap visualisation of feature relationships
- Comparison between numeric-only and fully numerized datasets

This repository is structured as a **portfolio-ready data analysis project**, with clear documentation for each stage of the workflow.

---

## Dataset

- **Source:** Movie dataset (CSV format)
- **Location:** `data/movies.csv`

**Key features include:**
- budget  
- gross  
- votes  
- score  
- runtime  
- year  
- genre  
- director  
- writer  
- star  
- company  
- country  

---

## Project Structure

```text
python-movie-correlation-analysis/
│
├── data/
│   └── movies.csv
│
├── doc/
│   ├── 1_initial_setup.md
│   ├── 2_data_cleaning.md
│   ├── 3_analysis.md
│   └── 4_key_insights.md
│
├── images/
│   ├── 1.png
│   ├── 2.png
│   ├── 3.png
│   ├── 4.png
│   ├── 5.png
│   ├── 6.png
│   ├── 7.png
│   └── 8.png
│
├── notebook/
│   └── movie_correlation.ipynb
│
└── README.md
```

---

## Documentation

Each stage of the project is fully documented:

- [Initial Setup](doc/1_initial_setup.md)  
- [Data Cleaning](doc/2_data_cleaning.md)  
- [Exploratory Analysis](doc/3_analysis.md)  
- [Key Insights](doc/4_key_insights.md)  

---

## Tools and Libraries Used

- Python  
- Pandas  
- NumPy  
- Matplotlib  
- Seaborn  
- Jupyter Notebook  

---

## Analysis Workflow

1. Inspected high and low grossing movies by sorting the dataset.
2. Explored budget vs gross revenue using scatter plots.
3. Added regression lines to visualise trends.
4. Generated correlation matrices for numeric features.
5. Visualised correlations using heatmaps.
6. Converted categorical features to numeric codes for exploratory correlation.
7. Analysed relationships between all features and gross revenue.
8. Extracted and documented key insights.

Detailed analysis steps are available in `doc/3_analysis.md`.

---

## Key Findings

- Budget has the strongest positive correlation with gross revenue.
- Audience engagement (votes) strongly relates to box office success.
- Runtime shows a moderate positive relationship with gross.
- IMDb score has a weak relationship with revenue.
- Genre and other categorical features show minimal direct correlation with gross.
- Correlation does not imply causation.

A full breakdown of insights is available in `doc/4_key_insights.md`.

---

## How to Run the Project

1. Clone the repository:
   ```bash
   git clone https://github.com/atubak400/python-movie-correlation-analysis.git
   ```

2. Navigate into the project directory:
   ```bash
   cd python-movie-correlation-analysis
   ```

3. Open the notebook:
   ```bash
   jupyter notebook notebook/movie_correlation.ipynb
   ```

4. Run the notebook cells from top to bottom.

---

## Notes

- Categorical variables were numerized strictly for exploratory correlation analysis.
- Numeric codes do not represent ordinal or ranking relationships.
- Visualisations are stored in the `images/` folder for documentation purposes.

---

## Author

**Kingsley Atuba**  
Data Analyst | Python | SQL | Power BI | Tableau  

---

## License

This project is for educational and portfolio purposes.
