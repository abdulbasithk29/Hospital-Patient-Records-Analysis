# Hospital-Patient-Records-Analysis

## Challenge Objectives
For the Maven Hospital Challenge, I would have to play the role of an analytics Consultant for ‘Massachusetts General Hospital (MGH)’.

Need to build a high-level KPI report for the executive team, based on a subset of patient records. The purpose of the report is to give stakeholders visibility into the hospital’s recent performance, and answer the following questions:

· How many patients have been admitted or readmitted over time?

· How long are patients staying in the hospital, on average?

· How much is the average cost per visit?

· How many procedures are covered by insurance?

---

## About The Data Set
Synthetic data on ~1k patients of ‘Massachusetts General Hospital’ from 2011-2022, including information on patient demographics, insurance coverage, and medical encounters & procedures.

---

## Analysis Insights
1. How many patients have been admitted or readmitted over time?

• 154 Patients have been admitted over time with 1136 encounters

• The re-admission rate over time is 55.72%. Which means almost half of the admitted patients have been re-admitted within 30 days.

• I have defined admissions as hospital stays of 15 hours or more and re-admissions as any subsequent admission within 30 days of the previous admission, regardless of encounter class.

2. How long are patients staying in the hospital, on average?

• On average patients have been staying in hospital around 1.81 hours for normal encounters

• Considering admissions, 29.58 hours is the average hospital stay.

• Please note that I have eliminated records with unusually long duration in outpatient, ambulatory, inpatient, and emergency encounters to maintain data integrity.

3. How much is the average cost per visit?

• $3.62K is the average cost per visit.

• $2.50K is the average payment made by patients after deducting the coverage amount

4. How many procedures are covered by insurance?

• 32,580 procedures are covered by insurance.

• Total procedures are 47,701.

• So, 68.3% of procedures are covered by insurance.

---

## Tools & Techniques  
- **Power BI**: Comprehensive analysis and interactive visualizations.  
- **Power Query in Power BI**: For efficient data transformation and cleaning.  
- **Data Modeling**: Creating relationships between tables and optimizing the data structure for analysis.
- **DAX (Data Analysis Expressions)**: Designing advanced measures and calculated columns to uncover insights.
- **Power BI Dashboards**: Crafting interactive, user-friendly dashboards for presenting key findings.

---

## Data Transformation Process – Power Query
- Gathered the data from 5 csv files into Power Query
- Added Custom columns in ‘encounters’ and ‘procedures’ tables for ‘duration’ of the encounter and procedure performed as per given start and stop date & time.
- Replaced the blank values of ‘ReasonCode’ and ‘ReasonDescription’ columns from ‘encounters’ and ‘procedures’ tables as ‘N/A’.
- Split the column ‘Birthplace’ in the ‘patients’ table in to ‘Town’ and ‘CountryCode’.
- Added custom column for ‘Patient Status’ in ‘patients’ table to categorise as ‘Alive’ and ‘Deceased’.
- Created column for Age by calculating using birth date and death date.
- Created custom column for Age Group as ‘25 to 40’, ‘40 to 60’, ‘60 to 80’ & ‘80 above’
- Replaced the blank values of ‘Maiden’ columns from table ‘patients’ as ‘No info’.
- Done other transformations like changing data types and trimming the text columns.
- Removed the records from ‘encounters’ table where extremely long durations of the encounters (several months) for outpatient visits considering these as outliers; the durations of outpatient visits are highly unusual and likely indicate data errors
- Some of the records in ambulatory encounters are also suspiciously long duration (several months and even years). Ambulatory encounters typically last a few hours, similar to outpatient visits. Removed those records as well.
- In inpatient encounters one record has 344 days duration is on the high end, it is not unheard of for severe or chronic conditions requiring long-term hospital care. Removed this record for the integrity of analysis.
- Emergency encounters typically range from a few hours to a day. Durations over 24 hours are unusual and are removed.

---

## Data Transformation Process – DAX
- Created Relationships between tables through Data modelling.
- Created a calendar table to make relationships between encounter dates and procedure dates.
- Created a week type column (Weekend & Weekday) to understand trends in patient admissions, optimize staffing, and improve resource allocation.
- Created calculated columns in ‘encounters’ table as ‘NextStartDate’ (to find the date of next admission of the same patient) and ‘IsReadmission’ (to get whether it is a re admission or not (True or False)). Considering re admission as any hospital stay that occurs within 30 days after the discharge of a previous stay.
- Considering ‘Admission’ as a hospital stay for more than or equal to 15 hours and Re admission as any admission of the same patient (>= 15hours stay) within 30 days of the previous admission, irrespective of the encounter class.

-- **Some of the measures created are**--
1.	Total Revenue
2.	Revenue growth % (10 years) - (Filtered 2022 for accurate and meaningful analysis as there are only January and February data for patient admissions)
3.	Previous Year Revenue
4.	YoY Revenue growth %
5.	No. of encounters covered by insurance
6.	Total cost covered by insurance
7.	Insurance coverage rate
8.	Total base cost of procedures
9.	Average cost per visit
10.	No. of Encounters
11.	Previous Year Encounters
12.	YoY Encounters rate
13.	Total Admission
14.	No. of Re admissions
15.	Re admission rate
16.	No. of Procedures
17.	No. of Patients
18.	Average Stay
19.	No. of Patients alive and Deceased
20.	No. of Follow-up encounters
21.	No. of Patients with Procedures
22.	No. of encounters with Procedures

---

## Calculated Columns and Measures Created
- *Attached screenshots*
