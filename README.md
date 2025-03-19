# NLA Airline Loyalty Program - PowerBI Analysis



## Introduction to the Project
This project focuses on data analysis of **Northern** **Lights** **Air** (NLA), a Canadian fictitious airline that implemented a promotional campaign between **February** **and** **April** **2018** to increase enrollments in its loyalty program.
The dashboard developed in Power BI focuses on the impact of the campaign on loyalty program enrollments, member socio-demo attributes and flight behavior during the following summer.

---

## Business Objectives
The main objective of the analysis is to **quantify** **the** **impact** **of** **the** **promotional** **campaign** on the loyalty program. 

In particular, it aims to answer three specific questions:
+ _What impact did the campaign have on loyalty program memberships (gross / net)?_
+ _Was the campaign adoption more successful for certain demographics of loyalty members?_
+ _What impact did the campaign have on booked flights during summer?_

---

## Data Source
The dataset was taken from [Maven Analytics](https://mavenanalytics.io/data-playground) and includes tables containing information on Customer Flight Activity and Customer Loyalty History.

In particular, the ***Customer Loyalty History*** table contains the detail of all registered customers, including location, gender, education, salary, marital status, customer lifetime value, enrollment type, date of enrollment and/or cancellation. The ***Customer Flight Activity*** table includes details of flights, including date, distance traveled by customers per trip, points accumulated and redeemed, and cost associated with redeemed points.

| Table                          | Description                               |
|--------------------------------|-------------------------------------------|
| Customer Flight Activity       | Contains data on flights from 2017 to 2018|
| Customer Loyalty History       | Details of each loyalty number            |
| Calendar                       | Date for time data analysis               |
| Airplane Loyalty Data Dictionary | Description of all fields                |

---

## Tech Tools Utilized:
+ Excel: Data Exploration
+ PowerBI: Data Cleaning with Power Query, Data Modeling, DAX functions, Data Visualization

---
## Data Preparation
Comprehension and exploration through loading and importing data, examining the structure of the dataset through column headers and data types, and transferring .csv data into the Power BI Power Query Editor.

| |
|:---:|
| ![Airline Loyalty Program PowerBI Dashboard](/Images/AIRLINE_2.png) |

---

## Data Cleaning 
To ensure an accurate and consistent analysis, a data cleaning and data preparation process was carried out within Power Query, which included the following activities:
+ Outlier handling: Identification and correction of **inconsistent** **values**, such as negative salaries, replaced with the average salary calculated by education level (Education).
+ Creation of derived fields: Generation of **new** **calculated** **columns** to enrich the analysis, such as "Salary Tier".
+ Missing Data Cleanup: Handling of **nulls** and incomplete attributes on master and behavioral variables, standardizing datasets.
+ Data normalization: Review and correction of decimal values on monetary columns (e.g., CLV), due to loss of decimal separators during import. Conversion of date fields to Date format (e.g., Enrollment Date).

---

## Data Modeling
The data model is structured according to a classic **star** **schema**, with Customer Flight Activity as the **fact** **table**, containing transactional data related to flights (number of flights, distance traveled, points accumulated/redeemed, etc.) and Customer Loyalty History as the **dimension** **table**, describing the profile of customers (master name, loyalty level, CLV, membership type). The relationship between the two tables is 1:N on the ***Loyalty*** ***Number*** key, where each customer can generate multiple flight activities over time. This schema allows analyzing the performance of the loyalty program by segmenting the results by demographic and behavioral characteristics of the members.

To properly separate customer lifecycle events from transactional flight activity, the model includes two calendar tables:
+ _Calendar_ is used for customer-level dates, such as enrollment and cancellation dates related to the loyalty program lifecycle.
+ _Calendar_Flight Activity_ is a duplicate of the Calendar table, created specifically to manage the temporal dimension of the flight transactions.

This approach ensures clean separation between the customer timeline (e.g., when a customer joined or left the program) and the flight activity timeline (e.g., flight bookings by month or season), avoiding overlaps in filters and enabling targeted time-based analysis for each context.

| |
|:---:|
| ![Airline Loyalty Program PowerBI Dashboard](/Images/AIRLINE_3.png) |

---

## DAX Measures
The project involved the creation of some **DAX** **measures** to ensure in-depth analysis and effectively answer business questions. Among the main techniques and calculations implemented:
+ Delta % Year-over-Year (YoY): Calculating the percentage change between 2018 and 2017 values on key KPIs such as Total CLV, Total enrollments, Flights booked and average distance per flight.
+ Churn rate: Custom measure to determine the churn rate between enrollments and cancellations on a monthly basis.
+ Period-specific filtering: Creating filtered measures on specific time intervals, such as promotional period (February-April 2018) or summer (June-August 2018), via DAX functions such as FILTER() and DATE().
+ SAMEPERIODLASTYEAR(): Using SAMEPERIODLASTYEAR to easily compute comparisons between equivalent periods over different years within combined graphs.
+ Dynamic (context-sensitive) measures: Development of measures that respect the dynamic context of slicers and filters, such as Average CLV per active customer in the month and Average distance per flight by season or year selected.

---

## Dashboard & Visualizations
The Power BI report is divided into **4** **pages**, each addressing specific analytical goals related to the NLA loyalty program and its promotional campaign:

**1)** **Campaign** **Overview**:
+ KPI Cards: Overview of total enrollments, cancellations, net enrollments, and churn rate.
+ Enrollment Trend Line Chart: Monthly trend of enrollments over several years with a focus on the Feb-Apr 2018 promotional period.
+ Comparative Analysis: Insights on enrollments compared to the previous period and the same months of the prior year, highlighting the campaign’s contribution.



**2)** **Revenue** **Focus**:
+ KPI Cards: Total and average CLV, flights per customer, average points accumulated and redeemed per customer.
+ Bar and Line Combo Chart: Monthly trend of total flights with enrollment type segmentation.
+ Bar Charts: CLV breakdown by province and city.
+ Funnel Chart: Average CLV segmented by education level.

| |
|:---:|
| ![Airline Loyalty Program PowerBI Dashboard](/Images/AIRLINE_4.png) |

**3)** **Demographics** **Focus**:
+ Bar Charts: Breakdown of enrollments (standard vs promo) by key demographics: gender, marital status, education, salary tier, and loyalty card type.
+ Heatmap: Enrollments by province and season to detect geographical and seasonal patterns in campaign adoption.

| |
|:---:|
| ![Airline Loyalty Program PowerBI Dashboard](/Images/AIRLINE_5.png) |

**4)** **Impact** **on** **Summer** **2018**:
+ KPI Cards: Summer 2018 flights, points accumulated, points redeemed, and dollar value of redeemed points, each compared to summer 2017.
+ Combo Chart: Total summer flights in 2018 with a YoY delta % line.
+ Grouped Bar Chart: Seasonal comparison of distance traveled (2017 vs 2018).
+ Deep-dive charts: Average flight distance per month and behavioral analysis of Promo vs Standard customers during summer.

| |
|:---:|
| ![Airline Loyalty Program PowerBI Dashboard](/Images/AIRLINE_6.png) |

The first three pages include a slicer, _Enrollment Type_, to allow for dynamic filtering across all visualizations.

---

## Data Analysis & Insights

Once the dashboard has been constructed, it becomes feasible to address the business objectives.
+ What impact did the campaign have on loyalty program memberships (gross / net)?

The promotional campaign launched between February and April 2018 generated a significant increase in loyalty program enrollments. Compared to both the previous period (Nov-Dec 2017) and the same months of the prior year (Feb-Apr 2017), total enrollments showed a strong upward trend, with a reduction in churn rate during the campaign period. The net enrollments (enrollments minus cancellations) confirmed the positive outcome, indicating that the campaign effectively improved customer acquisition and retention KPIs.
  
+ Was the campaign adoption more successful for certain demographics of loyalty members?

The campaign adoption was more effective among certain customer segments. Specifically, customers with higher levels of education (Bachelor's and above), higher income tiers, and those holding premium loyalty cards (Aurora and Nova tiers) showed higher enrollment rates in the promotion. The regional breakdown also highlighted greater campaign success in provinces like Ontario and Quebec, while certain demographics such as married customers and customers aged 30-50 were particularly responsive to the campaign.
  
+ What impact did the campaign have on booked flights during summer?

The promotional campaign positively influenced summer flight behavior. The analysis of summer 2018 bookings (June-August) showed an increase in the total number of flights compared to summer 2017, particularly among Promo members. In addition, there was an increase in loyalty points accumulated and redeemed during the same period. Although the average distance per flight slightly decreased, the volume of flights booked by customers acquired through the promotion rose significantly, demonstrating a tangible behavioral shift driven by the campaign.

---

## Executive Summary

The promotional campaign implemented by Northern Lights Air (Feb-Apr 2018) led to a substantial increase in loyalty program memberships, both in gross and net terms, reducing churn and outperforming previous periods and the prior year. The campaign adoption was especially successful among high-value customer segments, including those with higher education and income levels, as well as premium loyalty cardholders. Moreover, the campaign had a positive impact on summer flight activity, driving higher booking volumes and increased loyalty points usage among Promo members, highlighting a clear improvement in customer engagement and transactional behavior.

---

## Power BI Dashboard Link
Click the link to view the [Dashboard](https://app.powerbi.com/view?r=eyJrIjoiNGQ2MjIyYjAtYzE0YS00OWQzLWE1NzgtN2I4NTY0N2MxYWU2IiwidCI6ImM5NDI0M2ViLTZmMGUtNDU2Ni1hMjk2LWI1ZGZjOWQyNTczYiIsImMiOjh9).

---

## About me
Hi folks!
I am Giorgia and I am a real passionate about DATA! 

Let's stay in contact!

+ 📩: giorgiatagliaferri91@gmail.com
+ 🔗: [Linkedin](https://www.linkedin.com/in/giorgiatagliaferri91/)

