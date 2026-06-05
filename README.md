# healthy-minds-loneliness
QSS 20 final project on loneliness and mental health among emerging adults

🌐 **[View the project website](https://emilyjgarrard28.github.io/healthy-minds-loneliness)**

## Overview
This project examines how loneliness shapes mental health outcomes among U.S. college students using data from the Healthy Minds Study 2024-2025. I investigate how strongly depression (PHQ-9) and anxiety (GAD-7) co-occur with loneliness, whether these patterns differ by identity (sexual orientation, gender, race), and whether campus belonging and perceived stigma act as protective or risk factors. The analysis finds that sexual minority and gender minority students report substantially higher loneliness than their peers, that loneliness is the strongest independent predictor of both depression and anxiety, and that perceived stigma — but not campus belonging broadly — amplifies the loneliness-depression relationship.

## Research Questions
1. How does loneliness relate to depressive and anxiety symptoms among emerging adults?
2. Do these relationships differ by sexual orientation, race, or other identity factors? Do campus belonging and stigma act as protective or risk factors?

## Data
Data come from the [Healthy Minds Study 2024-2025](https://healthymindsnetwork.org/research/data-for-researchers/), a population-level annual survey of college student mental health. The full dataset contains 84,735 respondents across 135 institutions. The analytic sample is restricted to emerging adults aged 18-24.

The raw data file is not stored in this repository. Access has been shared with the instructor via Google Drive:
[HMS 2024-25 dataset](https://drive.google.com/file/d/1ds5qd1x1jbUJimTZFCPhM4TFfXNofNZr/view?usp=sharing)

To replicate, download the file and place it at `data/HMS_2024-2025_PUBLIC_instchars.csv`.

## Repository Structure

```
healthy-minds-loneliness/
├── code/
│   ├── 00_clean_data.ipynb
│   ├── 01_explore_data.ipynb
│   └── 02_analysis.ipynb
├── data/
│   └── README.md         ← data access instructions; raw file not committed
├── output/               ← saved figures (PNG)
├── index.html            ← project website (served via GitHub Pages)
└── README.md
```

## Scripts

### [`00_clean_data.ipynb`](code/00_clean_data.ipynb)
**Input:** `data/HMS_2024-2025_PUBLIC_instchars.csv` (raw HMS survey data)

**What it does:**
- Computes PHQ-9 and GAD-7 composite scores by summing item-level responses, converting from the survey's 1-4 coding back to the standard 0-3 scale
- Creates clinical screening flags (PHQ-9 ≥ 10 for depression, GAD-7 ≥ 10 for anxiety)
- Builds derived categorical variables for gender, sexual orientation (detailed and binary minority status), and race (White vs. racial minority)
- Constructs campus belonging and stigma composites with appropriate reverse-coding
- Filters to emerging adults aged 18-24

**Output:** `data/emerging_adults_clean.csv` (cleaned analytic sample, n = 61,288)

---

### [`01_explore_data.ipynb`](code/01_explore_data.ipynb)
**Input:** `data/emerging_adults_clean.csv`

**What it does:**
- Computes descriptive statistics and clinical screening rates for PHQ-9, GAD-7, and UCLA-3 loneliness
- Computes pairwise Pearson correlations among the three outcomes
- Produces side-by-side bar plots of mean depression and anxiety scores across loneliness levels

**Output:** `output/mental_health_by_loneliness.png`

---

### [`02_analysis.ipynb`](code/02_analysis.ipynb)
**Input:** `data/emerging_adults_clean.csv`

**What it does:**
- Compares mean loneliness across sexual orientation and race groups using Welch's independent-samples t-tests with Cohen's d effect sizes
- Plots loneliness by campus belonging and perceived stigma tertiles
- Estimates four multivariate OLS regression models using `statsmodels`: (1) depression, (2) anxiety, (3) loneliness, and (4) interaction models testing whether stigma amplifies and belonging buffers the loneliness-depression relationship

**Output:** regression coefficient tables, subgroup bar plots

---

## Key Findings
- 31.6% of emerging adults screen positive for depression (PHQ-9 ≥ 10)
- 28.8% screen positive for anxiety (GAD-7 ≥ 10)
- 44.2% meet the loneliness threshold (UCLA-3 ≥ 6)
- Depression and anxiety correlate strongly (r = 0.74); both correlate moderately with loneliness (r = 0.54 and r = 0.47)
- Sexual minority students report nearly 1 full point higher loneliness than heterosexual peers (d = 0.47); racial differences are negligible (d = 0.05)
- Loneliness independently predicts depression (β = 1.26) and anxiety (β = 1.09) after controlling for identity, belonging, stigma, and age
- Perceived stigma significantly amplifies the loneliness-depression relationship; campus belonging reduces depression independently but does not buffer the loneliness pathway
## Website

The project website summarizes the research for a general audience and is live at:

**[https://emilyjgarrard28.github.io/healthy-minds-loneliness](https://emilyjgarrard28.github.io/healthy-minds-loneliness)**

It is served via GitHub Pages from `index.html` in the root of this repository.

## Author

Emily Garrard · Dartmouth College · Psychology '28 · emily.j.garrard.28@dartmouth.edu