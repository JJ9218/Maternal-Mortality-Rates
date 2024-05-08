# Racial Disparities in Maternal Mortality Rates in the US
by J.Jones, MPH

## Table of Contents

- [Background](#background)
- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Tools](#tools)
- [Data Cleaning and Preparation](#data-cleaning-and-preparation)
- [Key Aims](#key-aims)
- [Data Analysis](#data-analysis)
- [Results](#results)
- [Recommendations](#recommendations)
- [Limitations](#limitations)
- [References](#references)

### Background

Maternal mortality rates (MMR) in the United States continues to be major public health issue, as recent studies show that rates have nearly doubled from 2018 to 2021. Among this crisis, literature have revealed that Black and American Indian and Alaska Native (AIAN) people have drastically higher maternal mortality rates compared to other races and ethnicities. Perpetuation of racial disparities in maternal and child health indicate that these stem from broader underlying social and economic inequities. Structural and systemic racism and discrimination and its association with disproportionate impacts on access to health care and health insurance coverage play a major role in disparities. Studies have also found that disparate racial outcomes persist even when social and economic factors are measured, underscoring the importance of addressing racism and discrimination for Black and AIAN people in the U.S. healthcare system and improving policies to move towards equitable maternal health outcomes. 


### Project Overview

This project highlights major racial disparities in maternal mortality rates in the United States from 2019-2023. Consistent with existing literature, it was found that American Indian and Alaska Native (AIAN) and Black people have drastically higher maternal mortality rates compared to other races and ethnicities. This project can be used to suggest public policies related to access to health care and insurance, and a call to action to close the gap in racial disparities in maternal and child health. 

### Data Sources

The dataset used for this analysis is the "VSRR Provisional Maternal Death Counts and Rates" csv file from the National Center for Health Statistics (NCHS). This dataset was last updated in January 2024, and provides provisional maternal mortality rates in the United States from 2019-2023 based on mortality and natality data from the National Vital Statistics System. ***include how MMR is measured in this dataset

### Tools

  - Excel- Data Inspection
      - [Download here](https://data.cdc.gov/resource/e2d5-ggg7.csv)
  - R - Data Cleaning, Data Analysis, and Visualizations
    
### Data Cleaning and Preparation

The following was performed for data cleaning and preparation:
1. Data inspection
2. Handling missing values
3. Data cleaning and formatting

### Key Aims

The data analysis measured statistical significance of matetnal maternality rates across several races/ethnicities in the United States, answering key questions such as:

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

#### Tukey's Honest Signficance Test
To identify any potential outliers within the study, the Tukey's Honest Significance test confirmed that there is a statisical difference in maternal mortality rates among all races/ethnicities, except between Hispanic and White people. 


```R
mmrfa %>%
  aov(Maternal.Mortality.Rate ~ Subgroup, data = .) %>%
  TukeyHSD()
```
#### T-Test
T- tests measured statistical significance in MMR when measuring AIAN and White people, and Black and White people. 

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
Despite American Indian and Alaska Native (AIAN) and Black people representing a smaller percentage of the US population, both Black and AIAN populations accounted for higher maternal mortality rates. The MMR for American Indian and Alaska Native people was 95.7 and 53.2 for Black people. This data remains consistent with previous literature which indicates that AIAN and Black populations have a drastically higher maternal mortality rate in comparison to other races/ethnicities, especially when comparing to White populations. 

Summary of results:
1. AIAN and Black people have drastically higher maternal mortality rates compared to other races/ethnicities, where AIAN have 5X the MMR compared to White people, and Black people have almost 3X the MMR compared to White people.
2. From 2021-2022, maternal mortality rates were among the highest within the 5 years measured, among most races/ethnicities in the United States. 

<img width="581" alt="Maternal Deaths Graph" src="https://github.com/JJ9218/Maternal-Mortality-Rates/assets/163039134/695423b2-1ebc-445c-9052-a5f87d0258d8">

### Recommendations
The continuing increase of MMR in the United States, especially racial disparities for AIAN and Black people, indicate the need to address and enact poliies that influence equitable maternal and child health outcomes.

Recommendations include:
1. Enhancing and creating federal and state social programs which address racial disparities in maternal health and provide affordable services to populations found to be disproportionately impacted by MMR's.
2. Continuing research and expanding data for AIAN and Native Hawaiin or Other Pacific Islanders to have a better representation of populations in the U.S., and better accuracy of MMR data.
3. Incorporating required trainings and evaluations in medical schools and health systems which acknowledge the impact of racism and discrimination on disparate outcomes, and enact methodologies that close the gap to progress into equitable health conditions. 

### Limitations

After removing missing values, there was limited data for AIAN and Native Hawaiian or Other Pacific Islanders. Missing values were present in MMR data as the NCHS indicates that rates for deaths counts <20 are unreliable, as well as data counts between 1-9 are suppressed according to their confidentiality standards. This led to missing data in the study from Native Hawaiian or Other Pacific Islanders, and MMR data for AIAN in 2019, 2020, and 2023. Limited data for these two groups could potentially impact the accuracy of drastic differences particular in this project, as data may not be the best representation of groups within the population. However, MMR's remain consistent with existing studies on racial disparities in maternal and child health. 

### References

1. Joseph, K.S., et al. “Maternal mortality in the United States: Are the high and rising rates due to changes in obstetrical factors, maternal medical conditions, or maternal mortality surveillance?” American Journal of Obstetrics and Gynecology, Mar. 2024, https://doi.org/10.1016/j.ajog.2023.12.038. 
2. Latoya Hill, Samantha Artiga, and Nov 2022. “Racial Disparities in Maternal and Infant Health: Current Status and Efforts to Address Them.” KFF, 15 June 2023, www.kff.org/racial-equity-and-health-policy/issue-brief/racial-disparities-in-maternal-and-infant-health-current-status-and-efforts-to-address-them/.
3. Fleszar, Laura G., et al. “Trends in state-level maternal mortality by racial and ethnic group in the United States.” JAMA, vol. 330, no. 1, 3 July 2023, p. 52, https://doi.org/10.1001/jama.2023.9043.
4. Leonard, Stephanie A., et al. “Racial and ethnic disparities in severe maternal morbidity prevalence and trends.” Annals of Epidemiology, vol. 33, May 2019, pp. 30–36, https://doi.org/10.1016/j.annepidem.2019.02.007.
5. Trost, Susanna, et al. “Pregnancy-Related Deaths among American Indian or Alaska Native Persons: Data from Maternal Mortality Review Committees in 36 US States, 2017–2019.” Centers for Disease Control and Prevention, Centers for Disease Control and Prevention, 19 Sept. 2022, www.cdc.gov/reproductivehealth/maternal-mortality/erase-mm/data-mmrc-aian.html.
6. Kozhimannil, Katy B et al. “Severe Maternal Morbidity and Mortality Among Indigenous Women in the United States.” Obstetrics and gynecology vol. 135,2 (2020): 294-300. doi:10.1097/AOG.0000000000003647
7. Hoyert DL. Maternal mortality rates in the United States, 2020. NCHS Health E-Stats. 2022.
DOI: https://dx.doi.org/10.15620/cdc:113967.
8. Njoku, Anuli et al. “Listen to the Whispers before They Become Screams: Addressing Black Maternal Morbidity and Mortality in the United States.” Healthcare (Basel, Switzerland) vol. 11,3 438. 3 Feb. 2023, doi:10.3390/healthcare11030438
9. Berg, Cynthia J., et al. “Pregnancy-related mortality in the United States, 1998 to 2005.” Obstetrics &amp; Gynecology, vol. 116, no. 6, Dec. 2010, pp. 1302–1309, https://doi.org/10.1097/aog.0b013e3181fdfb11.
10. Crear-Perry, Joia et al. “Social and Structural Determinants of Health Inequities in Maternal Health.” Journal of women's health (2002) vol. 30,2 (2021): 230-235. doi:10.1089/jwh.2020.8882
11. NCHS. “VSRR Provisional Maternal Death Counts and Rates.” Centers for Disease Control and Prevention, Centers for Disease Control and Prevention, 2024, data.cdc.gov/NCHS/VSRR-Provisional-Maternal-Death-Counts-and-Rates/e2d5-ggg7/about_data. 
