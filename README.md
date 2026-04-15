# B Corp Performance Analysis

This project analyses B Corp company performance using company assessment data from Data.World.

The goal was to understand how company scores change over time, whether improvement is linked to certification retention, and which structural factors may shape certification outcomes.

## What is a B Corp?

B Corps are companies certified by B Lab, a non-profit organization that evaluates businesses based on their social and environmental impact.

The certification aims to identify companies that meet high standards of accountability, transparency, and performance across multiple dimensions.

## How the B Corp score works

Companies are evaluated across five main impact areas:

- Governance  
- Workers  
- Community  
- Environment  
- Customers  

Each company receives an overall score, which is the sum of these five areas.

To become a certified B Corp, companies must achieve a minimum score of 80 points.

## Certification and re-certification

B Corp certification is not permanent.

Companies must go through periodic re-certification processes, where they are reassessed and receive a new score.

This allows companies to:
- improve their performance over time  
- maintain or lose certification depending on their results  

In this dataset:
- each row represents a certification assessment  
- companies can appear multiple times across different certification cycles

B Corp certification is designed to reflect social and environmental performance.

However, it is not clear whether certification outcomes are driven purely by performance improvement, or whether structural factors such as company size, geography, or resources play a role.

Understanding this distinction is important to correctly interpret what the B Corp score and certification status actually capture.

## Project questions

To explore this, the analysis focuses on three main questions:

1. Do B Corp companies improve over time?
2. Does score improvement increase the likelihood of remaining certified?
3. Does company size change that relationship?


## Dataset

The dataset used in this project comes from Data.World:

https://data.world/blab/b-corp-impact-data

It contains company-level and assessment-level information for B Corp certifications, including:
- overall scores
- impact area scores
- certification status
- company characteristics (size, country, industry)
- certification dates

Due to size constraints, the dataset is not stored in this repository.  
All analysis can be reproduced by downloading the data directly from the source.

It includes:
- 22,613 assessment records
- 13,995 unique companies
- 137 columns
- variables related to certification status, company characteristics, geography, industry, size, assessment year, overall score, and impact area scores

For the main company level analysis, I constructed a dataset comparing each company’s earliest and latest certification records.

This resulted in:
- 5,678 companies with at least 2 certification cycles

## Tools used

- SQL in Data.World for data extraction and company level dataset construction
- Python for cleaning, exploratory analysis, modelling, and visualization
- Jupyter Notebook for analysis workflow
- GitHub for version control and project presentation

## Methodology

### 1. SQL data preparation
I used SQL window functions to:
- identify each company’s first and most recent certification records
- rank certification cycles chronologically
- calculate total certification cycles
- recover the latest valid company size
- construct company level improvement metrics

### 2. Feature construction
At the company level, I created:
- earliest score
- latest score
- improvement margin
- improvement percent
- total certification cycles
- current status
- company size
- country and industry fields

### 3. Analysis
The analysis combines:
- exploratory data analysis
- descriptive comparisons
- correlation analysis
- logistic regression
- subgroup analysis by company size
- exploratory comparisons by region, country, and impact area

## Key findings

### 1. Companies tend to improve over time
Among companies with at least two certification cycles, average scores increased between first and latest certification.

This suggests that repeated certification is generally associated with score improvement, although the dataset is not a full time series of all intermediate score changes.

### 2. Score improvement increases the likelihood of remaining certified, but is far from sufficient to explain certification outcomes
Companies with higher improvement margins were more likely to remain certified, but the relationship was modest.

This suggests that performance improvement matters, but certification outcomes are not driven by score improvement alone.

### 3. Company size changes the relationship
The link between improvement and remaining certified was stronger for smaller companies and much weaker for larger firms.

This points to the possibility that large firms benefit from structural advantages that are not fully captured by score change alone.

### 4. Certification outcomes appear to be shaped by more than performance
A large share of variation remains unexplained by improvement margin alone.

This suggests that factors such as geography, sector, company maturity, assessment timing, or internal certification capacity may play an important role.

## Business implications

- Certification outcomes are not purely performance-driven, suggesting that structural advantages play a key role.
- Smaller companies appear more dependent on continuous improvement to maintain certification.
- Larger firms may benefit from resources, internal processes, and dedicated sustainability functions that support re-certification.
- Improvement metrics alone are insufficient to predict certification outcomes, highlighting the need for broader evaluation frameworks.

## Interesting exploratory insights to investigate further

This analysis opens the door to several additional questions:

- Which industries improve the fastest over time?
- Which countries have the highest re certification rates?
- Which impact areas drive score improvement the most?
- Are some companies improving overall while declining in specific impact areas?
- Does the number of certification cycles affect the probability of staying certified?
- Are early B Corps more likely to drop off than newer cohorts?
- Are some sectors more resilient to de certification than others?

## Files in this repository

- `README.md`  
  Project overview and findings

- `sql/01_build_company_level_dataset.sql`  
  Main SQL query used to build the company level comparison dataset

- `sql/02_exploratory_queries.sql`  
  SQL queries for initial exploration

- `sql/03_follow_up_questions.sql`  
  Additional queries for deeper investigation

- `notebooks/bcorp_analysis.ipynb`  
  Python notebook with cleaning, analysis, modelling, and plots

- `report/bcorp_performance_analysis.pdf`  
  Final presentation version of the analysis

## How to run the project

1. Download the dataset from Data.World  
2. Place the CSV file inside the `data/` folder  
3. Run the notebook in `notebooks/bcorp_analysis.ipynb`


## Next steps

There are several ways this project could be extended:

- build a panel dataset using all certification cycles instead of only first versus latest
- model retention using additional controls such as country, sector, industry, and year
- analyse changes across the five impact areas
- explore outliers and companies with large declines
- build an early warning flag for companies at risk of de certification

## Why this project matters

This project is not only about B Corp performance. It is also an example of how company data can be transformed into decision relevant insights.

It demonstrates a full workflow:
- SQL data extraction
- feature engineering
- business question framing
- statistical analysis
- interpretation for non technical stakeholders

## Author

Carla Pilgram
