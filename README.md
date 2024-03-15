# Racial Disparities in Maternal Mortality Rates in the US

## Table of Contents

- [Background](#background)
- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Tools](#tools)
- [Data Cleaning and Preparation](#data-cleaning-and-preparation)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Data Analysis](#data-analysis)
- [Results](#results)
- [Recommendations](#recommendations)
- [Limitations](#limitations)
- [References](#references)

### Background

Maternal mortality rates (MMR) in the United States continues to be major public health issue, as a most recent study shows that rates have nearly doubled from 2018 to 2021. Among this crisis, literature have revealed that American Indian and Alaska Native (AIAN) and Black people have drastically higher maternal mortality rates compared to White people. Perpetuation of racial disparities in maternal and child health indicate that these stem from broader underlying social and economic inequities. Structural and systemic racism and discrimination and its association with disproportionate impacts on access to health care and health insurance coverage play a major role in racial health disparities. Literature also highlights that even when social and economic factors are measured, these racial disparities persist, indicating racism and discrimination playing a major role in health disparities.  

### Project Overview

This project highlights major racial disparities in maternal mortality rates in the United States from 2019-2023. Consistent with existing literature, it was found that American Indian and Alaska Native (AIAN) and Black people have drastically higher maternal mortality rates compared to other races and ethnicities. This project can be used to suggest public policies related to access to health care and insurance, and a call to action to close the gap in racial disparities in maternal and child health. 

### Data Sources

The dataset used for this analysis is the "VSRR Provisional Maternal Death Counts and Rates" csv file from the National Center for Health Statistics (NCHS). This dataset was last updated in January 2024, and provides provisional maternal mortality rates in the United States from 2019-2023 based on mortality and natality data from the National Vital Statistics System. ***include how MMR is measured in this dataset

### Tools

  - Excel- Data Inspection
      - [Download here](https://data.cdc.gov/resource/e2d5-ggg7.csv)
  - R - Data Cleaning, Data Analysis, and Visualizations
    
### Data Cleaning and Preparation

The following was perfored for data cleaning and preparation:
1. Data inspection
2. Handling missing values
3. Data cleaning and formatting

### Exploratory Data Analysis

The data analysis measured statiscital significance of matetnal maternality rates across several races/ethnicities in the United States, answering key questions such as:

- Which races/ethnicities have disproportionately higher maternal mortality rates in the United States?
- Has there been an increase in maternal mortality rates in the United States since 2019?

### Data Analysis
Data analyses included finding the mean mortality rate of each race and ethnicity from 2019 to 2023.  Additionally, an ANOVA, Tukey's Honest Signifcance, and T-tests were conducted to determine the statisctal difference of maternal mortality rates among all races and ethnicities, and between races/ethnicities most impacted compared to White people. 

#### ANOVA Test
When measuring all races/ethnicities in the dataset, it was found that there is a statistical signifcance in the differences of maternal mortality rates among all races and ethnicities. 

```R
install.packages("tidyverse")
library (tidyverse)
mmrfa <- maternal_final %>%
  select (Subgroup, Maternal.Mortality.Rate) %>%
  filter(Subgroup %in% c("Hispanic", "American Indian or Alaska Native, Non-Hispanic", 
                         "Asian, Non-Hispanic", "Black, Non-Hispanic", "White, Non-Hispanic"))

anovat1 <- aov(Maternal.Mortality.Rate ~ Subgroup, data = mmrfa)

summary (anovat1)
```
|table|table|
|-----|-----|
|work|work2|

#### Tukey's Honest Signficance Test
To identify any potential outliers within the study, the Tukey's Honest Significance test confirmed that there is a statisical difference in maternal mortality rates among all races/ethnicities, except between Hispanic and White people. 


```R
mmrfa %>%
  aov(Maternal.Mortality.Rate ~ Subgroup, data = .) %>%
  TukeyHSD()
```
#### T-Test

```R
aiw1 <- maternal_final %>% 
  select(Subgroup, Maternal.Mortality.Rate) %>%
  filter(Subgroup == "American Indian or Alaska Native, Non-Hispanic" |
           Subgroup == "White, Non-Hispanic")
t.test (data = aiw1, Maternal.Mortality.Rate ~ Subgroup)

bw1 <- maternal_final %>% 
  select(Subgroup, Maternal.Mortality.Rate) %>%
  filter(Subgroup == "Black, Non-Hispanic" |
           Subgroup == "White, Non-Hispanic")
t.test (data = bw1, Maternal.Mortality.Rate ~ Subgroup)
```

### Results
Despite American Indian and Alaska Native (AIAN) and Black people representing a smaller percentage of the US population, both Black and AIAN populations accounted for higher maternal mortality rates. The maternal mortality rate for American Indian and Alaska Native people was 95.7 and 53.2 for Black people. This data remains consistent with previous literature which indicates that AIAN and Black populations have a drastically higher maternal mortality rate in comparison to other races/ethnicities, especially when comparing to White populations. 

Summary of results:
1. AIAN and Black people have drastically higher maternal mortality rates compared to other races/ethnicities, where AIAN have 5X the MMR compared to White people, and Black people have 3X the MMR compared to White people.
2. From 2021-2022, maternal mortality rates were among the highest within the 5 years measured, among most races/ethnicities in the United States. 

<img width="581" alt="Maternal Deaths Graph" src="https://github.com/JJ9218/Maternal-Mortality-Rates/assets/163039134/695423b2-1ebc-445c-9052-a5f87d0258d8">

### Recommendations
Things to condiser, how policies (Roe v wade) can impact maternal child health outcomes, increase of maternal child health outcomes from COVID-19, 

Expand access to health isurance coverage and health care, increase in specialized care related to maternal and child health, 

### Limitations

After removing missing values, there was limited data for Native Americans. Specifically, there was not any data recorded from 2019,2020, and 2023 compared to other races/ethnicities. This potentially could impact accuracy of drastic differences. 

### References

1. Joseph, K.S., et al. “Maternal mortality in the United States: Are the high and rising rates due to changes in obstetrical factors, maternal medical conditions, or maternal mortality surveillance?” American Journal of Obstetrics and Gynecology, Mar. 2024, https://doi.org/10.1016/j.ajog.2023.12.038. 
2. Latoya Hill, Samantha Artiga, and Nov 2022. “Racial Disparities in Maternal and Infant Health: Current Status and Efforts to Address Them.” KFF, 15 June 2023, www.kff.org/racial-equity-and-health-policy/issue-brief/racial-disparities-in-maternal-and-infant-health-current-status-and-efforts-to-address-them/.
3. 


  **bold**
  *italic*
