# NLA Airline Loyalty Program - Power BI Analysis

| |
|:---:|
| ![Airline Loyalty Program PowerBI Dashboard](/Images/AIRLINE_1.png) |


## Introduction to the Project
This project focuses on analyzing data from **Northern** **Lights** **Air** (NLA), a fictitious Canadian airline that implemented a promotional campaign between **February** and **April** **2018** to increase enrollments in its loyalty program.
The dashboard developed in Power BI focuses on the impact of the campaign on loyalty program enrollments, member-demo attributes, and flight behavior during the following summer.

---

## Business Objectives
The primary purpose of the analysis is to **quantify** **the** **impact** **of** **the** **promotional** **campaign** on the loyalty program. 

In particular, it aims to answer three specific questions:
+ _What impact did the campaign have on loyalty program memberships (gross / net)?_
+ _Was the campaign adoption more successful for certain demographics of loyalty members?_
+ _What impact did the campaign have on booked flights during summer?_

---

## Data Source
The dataset was taken from [Maven Analytics](https://mavenanalytics.io/data-playground) and includes tables containing information on Customer Flight Activity and Customer Loyalty History.

Specifically, the ***Customer Loyalty History*** table contains the detail of all registered customers, including location, gender, education, salary, marital status, customer lifetime value, enrollment type, enrollment and/or cancellation date. 

The ***Customer Flight Activity*** table includes details of flights, including date, distance traveled by customers per trip, points accumulated and redeemed, and cost associated with redeemed points.

| Table                          | Description                               |
|--------------------------------|-------------------------------------------|
| Customer Flight Activity       | Contains data on flights from 2017 to 2018|
| Customer Loyalty History       | Details of each loyalty number            |
| Calendar                       | Date for time data analysis               |
| Airplane Loyalty Data Dictionary | Description of all fields                |

---

## Tools & Scope:
+ Excel: Data Exploration
+ PowerBI: Data Cleaning with Power Query, Data Modeling, DAX functions, Data Visualization

---
## Data Preparation
The project began with a **data** **ingestion** and **exploration** **phase**. The data sets, provided in CSV format, were loaded and imported into Power BI Power Query Editor for preprocessing. This initial phase included:

+ Evaluation of the data structure, in which column headers and data types were examined for consistency.
+ Identification of key variables, such as dates, categorical fields (e.g., Gender, Education, Enrollment Type) and numerical measures (e.g., CLV, Salary, Points).
+ Verification of data quality, with emphasis on null values (e.g., Salary for College) and outliers (negative values in Salary).
+ Preparation for modeling, in which raw data were transformed, cleaned, and enriched to enable efficient transformation and analysis in Power BI.

| |
|:---:|
| ![Airline Loyalty Program PowerBI Dashboard](/Images/AIRLINE_2.png) |

---

## Data Cleaning 
As next step, to ensure an accurate and consistent analysis, a **data** **cleaning** and **data** **preparation** **process** was carried out within **Power** **Query**, which included the following activities:
+ Outlier handling: identification and correction of **inconsistent** **values**, such as negative salaries, replaced with the average salary calculated by education level (Education).
+ Creation of new fields: generation of **new** **calculated** **columns** to enrich the analysis, such as "Salary Tier".
+ Missing Data Cleanup: handling of **nulls** and incomplete attributes on demographic and behavioral variables, for standardizing the datasets.
+ Data normalization: correction of decimal values on monetary columns (e.g., CLV), due to loss of decimal separators during import; conversion of date fields to Date format (e.g., Enrollment Date).

---

## Data Modeling
Once the data were transformed, cleaned, and enriched, the data model was structured according to a classic **star** **schema**, with Customer Flight Activity as the **fact** **table**, containing transactional data related to flights (Number of flights, Distance traveled, Points accumulated/redeemed) and Customer Loyalty History as the **dimension** **table**, describing the profile of customers (Education, Enrollment Type, CLV). The relationship between the two tables is 1:N on the ***Loyalty*** ***Number*** key, since each customer can take more than one flight over time. This schema allows analyzing the performance of the loyalty program by segmenting the results by demographic and behavioral characteristics of the members.

To properly separate customer lifecycle events from transactional flight activity, the model includes two calendar tables:
+ _Calendar_ is used for customer-level dates, such as enrollment and cancellation dates related to the loyalty program lifecycle.
+ _Calendar_Flight Activity_ is a duplicate of the Calendar table, created specifically to manage the temporal dimension of the flight transactions.

This approach ensures a clear separation between the customer timeline (when a customer joined or left the program) and the flight activity timeline (flight bookings by month or season), avoiding overlaps in filters and allowing targeted time-based analysis for each context.

| |
|:---:|
| ![Airline Loyalty Program PowerBI Dashboard](/Images/AIRLINE_3.png) |

---

## DAX Measures
The project involved the creation of some **DAX** **functions** to ensure in-depth analysis and effectively answer the business questions. Among the main techniques and calculations implemented:
+ Delta % Year-over-Year (YoY): calculating the percentage change between 2018 and 2017 values on key KPIs such as Total CLV, Total enrollments, Flights booked and average distance per flight.
+ Churn rate: custom measure to determine the churn rate between enrollments and cancellations on a monthly basis.
+ Period-specific filtering: creating filtered measures on specific time intervals, such as promotional period (February-April 2018) or summer (June-August 2018), via DAX functions such as FILTER() and DATE().
+ SAMEPERIODLASTYEAR(): using SAMEPERIODLASTYEAR to easily compute comparisons between equivalent periods over different years within combined graphs.
+ Dynamic measures: development of measures that respect the dynamic context of slicers and filters, such as Median CLV per active customer in the month and Average distance per flight by season or year selected.

---

## Dashboard & Visualizations
The Power BI report is divided into **four** **pages**, each one addressing specific analytical goals related to the NLA loyalty program and its promotional campaign:

**1)** **Campaign** **Overview**:
+ KPI cards: overview of total enrollments, cancellations, net enrollments, and churn rate.
+ Enrollment & Churn Rate trend line chart: trend of enrollments and churn rate over the years and months.
+ Comparative analysis: insights on enrollments compared to the previous period (Nov 2017-Jan 2018) and the same months of the prior year (Feb-Apr 2017), highlighting the campaign’s contribution.

| |
|:---:|
| ![Airline Loyalty Program PowerBI Dashboard](/Images/AIRLINE_1.png) |

**2)** **Revenue** **Focus**:
+ KPI cards: total and median CLV, average flights per customer, total CLV 2018 compared to 2017.
+ Bar and line chart: monthly trend of total CLV 2018 with delta % CLV 2018 VS 2017.
+ Comparative analysis: a line chart compares the average accumulated points and the average redeemeded one by client
+ Bar charts: CLV breakdown by province and city.
+ Funnel chart: median CLV segmented by education level.

| |
|:---:|
| ![Airline Loyalty Program PowerBI Dashboard](/Images/AIRLINE_4.png) |

**3)** **Demographics** **Focus**:
+ Pie charts: breakdown of enrollments by gender, loyalty card and marital status.
+ Bar chart: breakdown of enrollments by salary tier.
+ Funnel chart: total enrollments by education level.
+ Heatmap: enrollments by province to detect geographical patterns in campaign adoption.

| |
|:---:|
| ![Airline Loyalty Program PowerBI Dashboard](/Images/AIRLINE_5.png) |

**4)** **Impact** **on** **Summer** **2018**:
+ KPI cards: total number of summer 2018 flights, points accumulated, points redeemed, and dollar value of redeemed points, each KPI card is compared to summer 2017.
+ Bar and line chart: total summer flights in 2018 by enrollment type with a YoY delta % line.
+ Grouped bar chart: seasonal comparison of distance traveled (2017 vs 2018).
+ Bar charts: total summer flights 2018 by education and salary tier compared to 2017.

| |
|:---:|
| ![Airline Loyalty Program PowerBI Dashboard](/Images/AIRLINE_6.png) |

The first three pages include a slicer, _Enrollment Type_, to allow for dynamic filtering across all visualizations.

---

## Data Analysis & Insights

Once the dashboard is completed, it is possible to address the business objectives.
+ What impact did the campaign have on loyalty program memberships (gross / net)?

The first two pages of the report, Campaign Overview and Revenues Focus, address this question from a business and a financial perspective. 
The promotional campaign launched between February and April 2018 generated a significant increase in loyalty program enrollments.
Ccompared to both the previous period (November 2018 - January 2017) and the same months of the prior year (February - April 2017), the total enrollments showed a strong upward trend, with a reduction in churn rate during the campaign period. 
The net enrollments (enrollments - cancellations) confirmed the positive outcome, indicating that the campaign effectively improved customer acquisition and retention KPIs. 
From a financial angle, the promotional campaign positively impacted the revenue generated in 2018, +48% increase in total CLV compared to 2017; the line chart highlights a substantial growth in CLV during the campaign months, with peaks of over +60% YoY delta. 
In addition, insights into customer profiles reveal that doctors and college students experienced the highest median increases in CLV during the campaign. Promotion customers also showed more frequent travel behavior, accumulating more loyalty points per trip than standard members.
  
+ Was the campaign adoption more successful for certain demographics of loyalty members?

The third page, Focus Demographics, addresses the above question. 
Although no significant differences were observed based on gender, marital status or type of loyalty card, a key finding is that the campaign successfully attracted low-value customers, who showed a greater response to the promotion compared to the standards.
In addition, bachelor-level customers showed high enrollment rates in both promotional and standard programs.
From a geographical point of view, regional trends reflected those of standard campaigns, without much variation among provinces.

| ![Airline Loyalty Program PowerBI Dashboard](/Images/AIRLINE_7.png) |
|:---:|
| *I applied a filter for 2018 promotion, selected “Bachelor” under “Enrollment by Education,” and as a result, I can see the breakdown of Bachelor's degrees by salary level.* |

+ What impact did the campaign have on booked flights during summer?

The final page of the report, Impact on Summer 2018, shows the positive influence of the promotional campaign on summer flight behavior. 
Total summer flights grew by +44% YoY, with Promo customers contributing significantly to this growth over multiple months, as shown in the bar-line chart.
As flight traffic increases, the result is also an increase in loyalty points accumulated and redeemed in the summer period. 
Seasonal comparison shows that all seasons, not just summer, experienced growth in distances traveled. 
High School students registered the highest growth in summer 2018 bookings (+53% YoY delta), while low-value salary tier customers confirm that the promotional campaign was particularly effective among this customer segment.

---

## Executive Summary

The promotional campaign run by Northern Lights Air between February and April 2018 led to a **significant** **increase** **in** **loyalty** **program** **memberships**, **reducing** **turn** **over** and improving acquisition and retention metrics. 
The campaign also resulted in a **+48%** **increase** **in** **CLV** compared to 2017, confirming its positive financial impact. Promo members showed higher travel frequency and accumulated more loyalty points per trip than standard members.
From a demographic perspective, the campaign was particularly successful among low-income customers and Bachelor level profiles, with strong adoption in key regions such as British Columbia and Ontario.
Lastly, the campaign led to higher engagement during the summer, with summer 2018 flight growth of **+44%** **year-over-year** and a significant increase in loyalty point usage. 
**Promo** **members** and **Bachelor/low-income** **customers** played a key role in increasing summer traffic.

---

## Power BI Dashboard Link
Click the link to view the [Dashboard](https://app.powerbi.com/view?r=eyJrIjoiNGQ2MjIyYjAtYzE0YS00OWQzLWE1NzgtN2I4NTY0N2MxYWU2IiwidCI6ImM5NDI0M2ViLTZmMGUtNDU2Ni1hMjk2LWI1ZGZjOWQyNTczYiIsImMiOjh9&pageName=1458df3c202a09cd95d1).

---

## About me
Hi folks!
I am Giorgia and I am a real passionate about DATA! 

This is my first dashboard in Power BI, I am more than open to criticisms and tips!

Let's stay in contact!

+ 📩: giorgiatagliaferri91@gmail.com
+ 🔗: [Linkedin](https://www.linkedin.com/in/giorgiatagliaferri91/)

