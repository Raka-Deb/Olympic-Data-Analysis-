# Olympic Dataset Exploratory Data Analysis (EDA) Report

## Overview
This report presents the findings from an exploratory data analysis (EDA) conducted on the Olympic dataset (`dataset_olympics.csv`) using a Jupyter Notebook (`Olympic_Data.ipynb`). The dataset contains information about Olympic athletes, their participation, and medal achievements across various years, sports, and events. The analysis focuses on understanding the dataset's structure, identifying data quality issues, and exploring patterns in medal distributions using statistical summaries and visualizations.


![image alt](https://github.com/Raka-Deb/Olympic-Data-Analysis-/blob/48473e0759c1aaac9e398ce33488d8568779e41c/Olympic_rings_without_rims.svg.png)



## Dataset Description
The Olympic dataset consists of 70,000 records with 15 columns, capturing details about athletes and their Olympic participation. Below is a detailed description of the columns:

- **ID**: Unique identifier for each athlete (int64).
- **Name**: Athlete's name (object).
- **Sex**: Athlete's gender (object, 'M' or 'F').
- **Age**: Athlete's age (float64, with missing values).
- **Height**: Athlete's height in centimeters (float64, with missing values).
- **Weight**: Athlete's weight in kilograms (float64, with missing values).
- **Team**: Country or team the athlete represents (object).
- **NOC**: National Olympic Committee code (object).
- **Games**: Specific Olympic event (e.g., '1992 Summer') (object).
- **Year**: Year of the Olympic event (int64).
- **Season**: Season of the Olympics (Summer or Winter) (object).
- **City**: Host city of the Olympics (object).
- **Sport**: Sport category (object).
- **Event**: Specific event within the sport (object).
- **Medal**: Medal type (Gold, Silver, Bronze, or NaN for no medal) (object).

## Key Findings

### 1. Data Structure and Summary Statistics
- **Dataset Size**: The dataset contains 70,000 entries with 15 columns.
- **Data Types**:
  - Numeric: `ID` (int64), `Age`, `Height`, `Weight` (float64), `Year` (int64).
  - Categorical: `Name`, `Sex`, `Team`, `NOC`, `Games`, `Season`, `City`, `Sport`, `Event`, `Medal` (object).
- **Summary Statistics for Numeric Columns**:
  - **ID**: Ranges from 1 to 35,658, with a mean of approximately 18,082.
  - **Age**: Ranges from 11 to 88 years, with a mean of 25.64 and a standard deviation of 6.49. Approximately 2,732 missing values.
  - **Height**: Ranges from 127 cm to 223 cm, with a mean of 175.51 cm and a standard deviation of 10.38. Approximately 16,254 missing values.
  - **Weight**: Ranges from 25 kg to 214 kg, with a mean of 70.90 kg and a standard deviation of 14.22. Approximately 17,101 missing values.
  - **Year**: Ranges from 1896 to 2016, with a mean of 1977.77 and a standard deviation of 30.10.
- **Summary Statistics for Categorical Columns**:
  - **Name**: 35,556 unique names, with Oksana Aleksandrovna Chusovitina appearing most frequently (29 times).
  - **Sex**: Two unique values ('M' and 'F'), with males (51,877) outnumbering females.
  - **Team**: 827 unique teams, with the United States appearing most frequently (4,979 times).
  - **NOC**: 226 unique National Olympic Committee codes, with the USA appearing most frequently (5,216 times).
  - **Games**: 51 unique Olympic events, with the 2016 Summer Olympics having the most entries (3,675).
  - **Season**: Two unique values (Summer: 58,467, Winter: remaining entries).
  - **City**: 42 unique host cities, with London being the most frequent (6,034 times).
  - **Sport**: 65 unique sports, with Athletics being the most common (10,629 entries).
  - **Event**: 744 unique events, with Football Men's Football being the most frequent (1,738 times).
  - **Medal**: Three unique values (Gold, Silver, Bronze), with Gold being the most frequent (3,292 times). Approximately 60,310 entries have no medal (NaN).

### 2. Data Quality Issues
- **Missing Values**:
  - `Age`: 2,732 missing values (3.9% of entries).
  - `Height`: 16,254 missing values (23.2% of entries).
  - `Weight`: 17,101 missing values (24.4% of entries).
  - `Medal`: 60,310 missing values (86.2% of entries), indicating that most athletes did not win a medal.
- **Duplicates**: 383 duplicate rows were identified and removed, ensuring data integrity. No duplicates remained after cleaning.
- **Potential Outliers**:
  - **Age**: The range (11 to 88 years) suggests potential outliers, particularly at the higher end (e.g., 88 years seems unusual for an Olympic athlete).
  - **Height**: The range (127 cm to 223 cm) is plausible but includes extreme values that may warrant further investigation.
  - **Weight**: The range (25 kg to 214 kg) also includes extreme values, particularly at the lower and upper ends, which may reflect data entry errors or exceptional cases.

### 3. Data Distribution and Patterns
- **Temporal Distribution**:
  - The dataset spans from 1896 to 2016, covering both Summer and Winter Olympics.
  - The majority of entries are from Summer Olympics (58,467 entries), reflecting the larger scale of Summer Olympic events.
- **Medal Distribution**:
  - Only 13.8% of entries (9,690 out of 70,000) have a medal, indicating a competitive environment where most participants do not win medals.
  - Gold medals are the most common among awarded medals, followed by Silver and Bronze.
- **Demographic Insights**:
  - The average athlete age is approximately 25.6 years, with a relatively narrow standard deviation (6.49), suggesting most athletes are in their 20s.
  - The dataset is male-dominated (51,877 males vs. fewer females), which may reflect historical participation trends in the Olympics.
- **Geographical Insights**:
  - The United States (USA) and its NOC code dominate in terms of participation (4,979 Team entries, 5,216 NOC entries).
  - London is the most frequent host city, likely due to multiple Olympic events held there (e.g., 1908, 1948, 2012).

### 4. Visualization Insights
- **Heatmap of Medal Counts by Country and Year**:
  - A pivot table was created to aggregate medal counts by National Olympic Committee (NOC) and Year.
  - The heatmap (using the 'YlOrRd' color map) visualizes the distribution of medals across countries and years.
  - Key observations:
    - Certain countries (e.g., USA, USSR/RUS) consistently show higher medal counts across multiple years, indicating sustained Olympic success.
    - Recent years (e.g., 2000–2016) show denser medal distributions, likely due to increased participation and event categories.
    - Some countries have sporadic high medal counts in specific years, possibly due to hosting advantages or exceptional performances.
    - Gaps in the heatmap (white areas) indicate years or countries with no medals, which may reflect non-participation or lack of success.

## Visualizations
- **Heatmap**:
  - The heatmap provides a clear visual representation of medal counts by country (NOC) and year.
  - Countries with consistent Olympic participation (e.g., USA, RUS, GER) show strong patterns of medal wins, while smaller or newer NOCs have fewer or no medals in certain years.
  - The rotated x-axis labels (45 degrees) improve readability for the years, and the linewidths (0.5) enhance the clarity of the grid structure.

## Recommendations for Further Analysis
1. **Handling Missing Values**:
   - Impute missing `Age`, `Height`, and `Weight` values using techniques like mean/median imputation or predictive modeling based on `Sport`, `Sex`, or `Event`.
   - For `Medal`, the high percentage of missing values is expected (non-medalists), but further analysis could categorize these as a separate 'No Medal' group for clarity.
2. **Outlier Investigation**:
   - Investigate extreme values in `Age`, `Height`, and `Weight` to determine if they are valid (e.g., young gymnasts or heavyweight athletes) or data entry errors.
3. **Temporal Trends**:
   - Analyze trends in participation and medal wins over time, particularly to identify how events or participation have evolved (e.g., increased female participation, new sports).
4. **Demographic Analysis**:
   - Explore gender-based differences in participation and success rates across sports and years.
   - Investigate age distributions within specific sports to identify optimal age ranges for success.
5. **Geographical Analysis**:
   - Perform a deeper analysis of medal counts by country, considering factors like population size, economic status, or hosting effects.
   - Compare Summer vs. Winter Olympics performance by country.
6. **Sport and Event Analysis**:
   - Examine which sports or events have the highest medal opportunities or participation rates.
   - Analyze the relationship between athlete characteristics (e.g., height, weight) and success in specific sports.

## Conclusion
The EDA provides a comprehensive overview of the Olympic dataset, highlighting its structure, quality issues, and key patterns. The dataset is rich with information but has challenges like missing values and potential outliers that require further cleaning. The heatmap visualization reveals significant trends in medal distribution, with dominant countries and recent years standing out. These findings lay the groundwork for more advanced analyses, such as predictive modeling of medal outcomes or detailed demographic studies. The cleaned dataset (with duplicates removed) is ready for further exploration to uncover deeper insights into Olympic performance trends.
