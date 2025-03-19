# NLA Airline Loyalty Program - PowerBI Analysis

## Project Overview
This project focuses on data analysis of Northern Lights Air (NLA), a Canadian fictitious airline that implemented a promotional campaign between February and April 2018 to increase enrollments in its loyalty program.
The dashboard developed in Power BI focuses on the impact of the campaign on loyalty program enrollments, member socio-demo attributes, and flight behavior during the following summer.

---

## Business Problem
+ Quale impatto ha avuto la campagna sulle iscrizioni al programma fedeltà (lordo/netto)?
+ L'adozione della campagna ha avuto più successo per alcuni gruppi demografici di membri del programma fedeltà?
+ Che impatto ha avuto la campagna sui voli prenotati durante l'estate?

---

## Tecnologie e strumenti
Power BI Desktop
DAX (Data Analysis Expressions)
Power Query
Data Modeling (relazioni 1:N, direzioni filtro e normalizzazione)
🚀 Azioni svolte per la creazione del report

---

## Dati
Il set di dati è stato preso dal sito [Maven Analytics](https://mavenanalytics.io/data-playground) e comprende tabelle contenenti informazioni su Customer Flight Activity e Customer Loyalty History.

| Table                          | Description                               |
|--------------------------------|-------------------------------------------|
| Customer Flight Activity       | Contains data on flights from 2017 to 2018|
| Customer Loyalty History       | Details of each loyalty number            |
| Calendar                       | Date for time data analysis               |
| Airplane Loyalty Data Dictionary | Description of all fields                |



---

# 1️⃣ Data Cleaning & Data Preparation
Importazione di 3 dataset:
Customer Loyalty History
Customer Flight Activity
Calendar
Pulizia dei dati in Power Query:
Rimozione di valori nulli.
Correzione di dati anomali (es. valori negativi su "Salary").
Creazione di colonne calcolate (es. Season, Customer Value Tier, ecc.).
Sostituzione di dati mancanti con valori medi su base Education.

# 2️⃣ Data Modeling
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
