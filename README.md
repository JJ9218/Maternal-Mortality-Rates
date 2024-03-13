# Racial Disparities in Maternal Mortality Rates in the US

## Table of Contents

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

### Project Overview

This project highlights major racial disparities in maternal mortality rates in the United States from 2019-2023. Consistent with existing literature, it was found that Native Americans and Black Americans have drastically higher maternal mortality rates compared to other races and ethnicities.

### Data Sources

The dataset used for this analysis is the "VSRR Provisional Maternal Death Counts and Rates" csv file from the National Center for Health Statistics (NCHS). This dataset was last updated in January 2024, and provides provisional maternal mortality rates in the United States from 2019-2023 based on mortality and natality data from the National Vital Statistics System. 

### Tools

  - Excel- Data Inspection
      - [Download here](https://data.cdc.gov/resource/e2d5-ggg7.csv)
  - R - Data Cleaning, Data Analysis, and Visualizations
    
### Data Cleaning and Preparation

The following was perfored for data cleaning and preparation:
1. Data loading and inspection
2. Handling missing values
3. Data cleaning and formatting

### Exploratory Data Analysis

The data analysis measured statiscital significance of matetnal maternality rates across several races/ethnicities in the United States, answering key questions such as:

- Which races/ethnicities have disproportionately higher maternal mortality rates in the United States?
- Has there been an increase in maternal mortality rates in the United States since 2019?

### Data Analysis

#### ANOVA test
When measuring all races/ethnicities in the dataset, it was found that there is a statistical signifcance in the differences of maternal mortality rates among all races and ethnicities. 

|table|table|
|-----|-----|
|work|work2|

To identify any potential outliers within the study, the Tukey's Honest Significance test confirmed that there is a statisical difference in maternal mortality rates among all races/ethnicities, except between Hispanic and White people. 

Code

```R

```
#### T-Test

### Results
Despite American Indians and Black people representing less of the US population, both Black and Brown populations accounted for higher maternal mortality rates. American Indians with 95.7 maternal mortality rate, and Black people with 53.2 maternal mortality rate. This data remains consistent with previous literature which indicates that American Indian and Black populations have a drastically higher maternal mortality rate in comparison to other races/ethnicities

In short, the results indicate:
1. Native Americans and Black people have drastically higher maternal mortality rates compared to other races/ethnicities, where Native Americans have 5X the MMR compared to White people, and Black people have 3X the MMR compared to White people.
2. 
3. 

<img width="581" alt="Maternal Deaths Graph" src="https://github.com/JJ9218/Maternal-Mortality-Rates/assets/163039134/695423b2-1ebc-445c-9052-a5f87d0258d8">

### Recommendations


### Limitations

After removing missing values, there was limited data for Native Americans. Specifically, there was not any data recorded from 2019,2020, and 2023 compared to other races/ethnicities. This potentially could impact accuracy of drastic differences. 

### References

1. f
2. p

  |table|table|
  |-----|-----|
  |work|work2|

  **bold**
  *italic*
