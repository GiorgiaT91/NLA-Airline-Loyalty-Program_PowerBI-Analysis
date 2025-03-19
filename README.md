# NLA Airline Loyalty Program - PowerBI Analysis
![Airline Loyalty Program PowerBI Dashboard](/Images/AIRLINE_1.png)

## Introduction to the Project
This project focuses on data analysis of **Northern** **Lights** **Air** (NLA), a Canadian fictitious airline that implemented a promotional campaign between **February** **and** **April** **2018** to increase enrollments in its loyalty program.
The dashboard developed in Power BI focuses on the impact of the campaign on loyalty program enrollments, member socio-demo attributes and flight behavior during the following summer.

---

## Business Objectives
The main objective of the analysis is to **quantify** **the** **impact** **of** **the** **promotional** **campaign** on the loyalty program. 

In particular, it aims to answer three specific questions:
+ What impact did the campaign have on loyalty program memberships (gross / net)?
+ Was the campaign adoption more successful for certain demographics of loyalty members?
+ What impact did the campaign have on booked flights during summer?

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
![Airline Loyalty Program PowerBI Dashboard](/Images/AIRLINE_2.png)

---

## Data Cleaning 
To ensure an accurate and consistent analysis, a data cleaning and data preparation process was carried out within Power Query, which included the following activities:
+ Outlier handling: Identification and correction of **inconsistent** **values**, such as negative salaries, replaced with the average salary calculated by education level (Education).
+ Creation of derived fields: Generation of **new** **calculated** **columns** to enrich the analysis, such as "Salary Tier".
+ Missing Data Cleanup: Handling of **nulls** and incomplete attributes on master and behavioral variables, standardizing datasets.
+ Data normalization: Review and correction of decimal values on monetary columns (e.g., CLV), due to loss of decimal separators during import. Conversion of date fields to Date format.

---

## Data Modeling
The data model is structured according to a classic **star** **schema**, with Customer Flight Activity as the **fact** **table**, containing transactional data related to flights (number of flights, distance traveled, points accumulated/redeemed, etc.) and Customer Loyalty History as the **dimension** **table**, describing the profile of customers (master name, loyalty level, CLV, membership type). The relationship between the two tables is 1:N on the ***Loyalty*** ***Number*** key, where each customer can generate multiple flight activities over time. This schema allows analyzing the performance of the loyalty program by segmenting the results by demographic and behavioral characteristics of the members.

---

Costruzione di un modello relazionale:
Relazione 1 a molti tra Customer Loyalty History (Loyalty Number) e Customer Flight Activity (Loyalty Number).
Collegamento tra Calendar e le date di volo (Customer Flight Activity[Date]).
Direzione dei filtri personalizzata per consentire un corretto propagarsi del contesto tra tabelle.

# 3️⃣ Creazione di misure DAX
KPI sul volume di iscrizioni e cancellazioni.
Calcolo del churn rate.
Misure comparative 2018 vs 2017 su iscrizioni, voli e distanza percorsa.
Creazione di delta % e delta assoluti per analisi temporali e campagne.

# 4️⃣ Dashboard & Visualizzazioni
Creazione di più schede report con layout professionale:
Impatto della campagna sulle iscrizioni (gross/net) ➡ grafici KPI, churn rate, trend mensile.
Analisi demografica dell’adozione della campagna ➡ grafici per Education, Income, Province, Gender.
Comportamento sui voli estivi ➡ focus su estate 2018 vs estate 2017 (voli, distanze e punti fedeltà).
Heatmap stagionale e mappa geografica su province canadesi.

# 5️⃣ UX migliorata
Utilizzo di slicer su Enrollment Type (Promo vs Standard) e su Season.
Creazione di grafici combinati (linea + barre) per evidenziare variazioni anno su anno.
Applicazione di formattazione condizionale su valori delta.

# 🎯 Obiettivi del progetto
Analizzare l’efficacia della campagna fedeltà in termini di customer acquisition e comportamento d’acquisto.
Mostrare capacità di creare un report Power BI end-to-end: dalla pulizia dati al data storytelling.

# 📈 Screenshot (opzionale)

# 📷 Inserire eventuali immagini o GIF della dashboard Power BI.

# 📥 Come esplorare il report
Apri il file .pbix incluso nella repo.
Esplora le diverse pagine del report.
Utilizza slicer e filtri per personalizzare la visualizzazione.
