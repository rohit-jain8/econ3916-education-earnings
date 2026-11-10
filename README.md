# Education and Annual Earnings in Massachusetts, 2024

**ECON 3916 – Applied Econometrics | Midterm Project | November 2026**

## Research Question

How is educational attainment associated with annual earnings among Massachusetts adults ages 25–64 with positive earnings in 2024, controlling for age and sex?

For this project, I wanted to look at how much annual earnings differ across education levels in Massachusetts. More specifically, I wanted to see whether people with higher levels of education tend to earn more, even after accounting for differences in age and sex.

The goal is to examine the relationship between education and earnings, not to claim that education directly causes higher earnings.

## Data

I used the **2024 American Community Survey (ACS) 1-Year Public Use Microdata Sample (PUMS)** for Massachusetts, provided by the U.S. Census Bureau.

Data source: https://www2.census.gov/programs-surveys/acs/data/pums/2024/1-Year/

The original dataset had 74,617 observations. After limiting the sample to adults ages 25–64 with positive annual earnings and complete information for the variables I needed, I was left with **31,442 observations**.

The main variables I used were:

- **Annual earnings (PERNP):** My dependent variable, which I converted to log earnings for the regression.
- **Education (SCHL):** Divided into five groups: less than high school, high school/GED, some college or an associate degree, bachelor's degree, and graduate education.
- **Age (AGEP):** Included age and age squared to account for how earnings might change throughout someone's career.
- **Sex (SEX):** Included as another control variable.
- **Person weights (PWGTP):** Used in an additional weighted regression.

I used high school/GED as the reference group when comparing education levels.

## Method

I started by looking at summary statistics and graphs to get a better understanding of the data. I then ran an OLS regression with log annual earnings as the dependent variable and education, age, age squared, and sex as the explanatory variables.

I used HC3 robust standard errors because my diagnostic tests showed evidence of heteroskedasticity.

I also ran two additional regressions to see how much my results changed:

- A weighted regression using the ACS person weights.
- A regression that only included full-time, year-round workers (at least 35 hours per week and 50 weeks per year).

Finally, I checked the model using residual plots, the Breusch–Pagan test, VIFs, and Cook's distance.

## Results

Overall, I found a pretty clear positive relationship between education and annual earnings.

Compared with someone whose highest education level is high school/GED, holding age and sex constant:

- People with a **bachelor's degree** had approximately **99.3% higher annual earnings**.
- People with **graduate education** had approximately **152.1% higher annual earnings**.
- People with **some college or an associate degree** had approximately **17.9% higher annual earnings**.
- People with **less than a high school education** had approximately **30.6% lower annual earnings**.

The main regression had an R-squared of **0.171**, meaning the variables in the model explained about 17.1% of the variation in log annual earnings.

The relationship was still positive in the weighted and full-time regressions, although the estimated differences were somewhat smaller.

One important thing to keep in mind is that these results show an association, not necessarily a causal relationship. Other factors, like family background, work experience, and career choices, could also affect someone's earnings.

## Files

| File | What it contains |
|---|---|
| `midterm_analysis.ipynb` | My completed notebook with the analysis, regressions, graphs, and diagnostic tests |
| `ma_acs_2024_analysis.csv` | The cleaned dataset used for the project |
| `summary_statistics.csv` | Summary statistics for the sample |
| `Education Earnings Report.pdf` | My final written report |
| `README.md` | Overview of the project and instructions for running the analysis |

## How to Run the Notebook

Google Colab link:

[https://colab.research.google.com/drive/1lhMf-s9C-BmkkWNxUKEhS1AplfIzkrh_?usp=sharing
](https://colab.research.google.com/drive/1lhMf-s9C-BmkkWNxUKEhS1AplfIzkrh_?usp=sharing)

To reproduce my results:

1. Open the Colab notebook using the link above, or open `midterm_analysis.ipynb` from this repository.
2. Run the cells in order, starting from the top.
3. The notebook downloads the cleaned dataset directly from this GitHub repository.
4. Running the notebook produces the summary statistics, regression results, and diagnostic plots used in my report.

I used Python with pandas, NumPy, Matplotlib, and statsmodels.

## Limitations

There are a few limitations worth mentioning. First, the analysis only includes Massachusetts adults ages 25–64 who had positive earnings in 2024, so the results don't necessarily apply to everyone.

Also, annual earnings depend on both how much someone gets paid and how much they work. This means some of the differences between education groups could reflect differences in hours or weeks worked.

Finally, I couldn't control for everything that might affect earnings, including ability, family background, or career choices. Because of this, I interpret the results as associations rather than causal effects.

## Data Source

U.S. Census Bureau. (2024). *American Community Survey, 2024 1-Year Public Use Microdata Sample, Massachusetts person-level data.*

https://www2.census.gov/programs-surveys/acs/data/pums/2024/1-Year/
