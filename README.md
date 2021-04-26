# Predicting_infection
Capstone 1 predicting healthcare related infections for MRSA

## Purpose
The goal of this project was to predict MRSA infections at the hospital level in a given year, given data about other hospital associated infections, patient survey scores and sepsis treatment score ratings.  

__Significance:__

"At any given time, about 1 in 25 inpatients have an infection related to hospital care. These infections lead to tens of thousands of deaths and cost the U.S. health care system billions of dollars each year." - https://health.gov/our-work/health-care-quality/health-care-associated-infections

I chose MRSA infections as it seemed the least influenced  by certain medical procedures or medical tools, compared with the other HAI data types (i.e. not related to a specific surgery or device (such as a catheter infection).  Being able to predict either the standardized score OR how many patients may get infections could help hospitals prepare 

## 1. Data Source
All data used in this project are publicly available from the United States CMS (centers for Medicare and Medicaid).  However, the data sets are not restricted to only Medicaid or Medicare patients.  These data are used to rank hospitals nationwide.  I pulled the 2019 data for the 3 data sets below and combined them together for this project.  2019 was the most recent year of complete data due to issues with data collection during the COVID-19 pandemic in 2020.

**Healthcare Associated Infections (HAIs)** (https://data.cms.gov/provider-data/dataset/77hc-ibv8)
<br> - How often patients get an infection while in the hospital. This measure is categorized into several different types and means of infections (related to equipment, procedures, or location of infection).  It is also compared to a national benchmark for that type of hospital, and normalized based to some degree based on things like how many beds at the hospital, lab methods used, affiliation with a medical school, patient age and some others. Top priority HAIs are central line-associated bloodstream infections (CLABSI) and methicillin-resistant Staphylococcus aureus (MRSA) infections.

**Patient survey (HCAHPS)** (https://data.cms.gov/provider-data/topics/hospitals/hcahps#hcahps-star-ratings) 
<br> - this survey is administered to patients at random (not just medicare patients).  This has 19 questions about the hospital + 10 other demographic and screening questions. (details on questions here: https://data.cms.gov/provider-data/topics/hospitals/hcahps#about-the-hcahps-survey) 

Star rating and linear score (part HCAHPS survey results) 
<br> - Star rating summarizes the patient survey responses by category, and is rolled into a single 'summary star' rating per facility. (details here: https://data.cms.gov/provider-data/topics/hospitals/hcahps#hcahps-star-ratings)

**Timely and Effective Care** (https://data.cms.gov/provider-data/dataset/yv7e-xc69)
<br> - Includes several measures about specific topics, each topic is given a rating based off what has been shown to be best practice or most important with that procedure.  Data are collected from records of medicare and non-medicare patients. Measures include:  cataract surgery outcome, colonoscopy follow-up, heart attack care, emergency department care, preventive care, pregnancy and delivery care, and cancer care.  Each category has different measures (percentage, number of minutes, etc...) **Most relevant measures here is sepsis - "percentage of patients with severe sepsis or septic shock for which a hospital provides appropriate care".**. (more details about the data: https://data.cms.gov/provider-data/topics/hospitals/timely-effective-care)

## Data Cleaning

## EDA

## Algorithms and Machine Learning

### Tuning


## Outcomes
The initial goal was to predict the MRSA 'SIR' score (Standardized Infection Ratio) per hospitals.  It turns out the SIR score has so many factors baked into it, I couldn't predict this directly with the information given (my predictions were worse than just guessing the mean).

However, I was able to predict the total number of observed cases at a given hospital before standardization to within __xxx___.

The key controls for this were the HAI_3, 2, 6 and 4 data.  These are 

__More details on SIR score__
The CDC calculates a Standardized Infection Ratio (SIR) which may take into account the type of patient care location, number of patients with an existing infection, laboratory methods, hospital affiliation with a medical school, bed size of the hospital, patient age, and classification of patient health.

## Future Improvements

## Credits

## Appendix
### File overview
Files | Description
------------ | -------------
01_Wrangling_HAI_tidy_report.html | Step 1 output - Pandas profiling EDA report
Name Abbreviations HAI_Names_ID_xref.csv | Explanation of feature names related to HAI (Hospital associated infections)
Name abbreviations HCAHPS survey_ID_Questoin_Xref.csv | Explanation of survey features
Name abbreviations Sepsis.csv | Explanation of sepsis features
requirements.txt | python requirements file for reproducibility

Data files | Description
------------ | -------------
data/HAI_tidy_Encoded.csv | Master table with data encoded as digits instead of text categories
data/HAI_tidy_Wrangled.csv | Output of step 1, data wrangling
data/HCAHPS-Hospital.csv | Raw 2019 survey data
data/Healthcare_Associated_Infections_-_Hospital.csv | Raw 2019 Healthcare associated infections data
data/Timely_and_Effective_Care-Hospital.csv | Raw 2019 sepsis (and other treatment) data


### Notebooks
Notebook | Description
------------ | -------------
01_DataWrangling.ipynb | From raw data to 'tidy' format, main outcome is the cleaned HAI_tidy_Wrangled.csv file
02_ExploratoryDataAnalysis_HAI.ipynb | EDA notebook, includes many visualizations, main output is HAI_tidy_Encoded.csv
03_Preprocessing_and_Modeling.ipynb | Final notebook for model application, tuning and scoring.



**Related data** (https://data.cms.gov/provider-data/dataset/yv7e-xc69)
<br> - In case that wasn't enough links, here's one more. Other datasets included in comparing hospitals that have not been used in this study. 
