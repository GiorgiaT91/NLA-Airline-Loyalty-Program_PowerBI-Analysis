# NLA-Airline-Loyalty-Program_PowerBI-Analysis

# 📚 Descrizione
Progetto di analisi dei dati di Northern Lights Air (NLA), una compagnia aerea fittizia canadese che ha implementato una campagna promozionale tra Febbraio e Aprile 2018 per incrementare le iscrizioni al proprio programma di fidelizzazione.
Il progetto si concentra sull’impatto della campagna su:

Iscrizioni (lordo / netto)
Adozione da parte di diversi segmenti demografici
Comportamento di volo durante l’estate successiva

# 🛠 Tecnologie e strumenti
Power BI Desktop
DAX (Data Analysis Expressions)
Power Query
Data Modeling (relazioni 1:N, direzioni filtro e normalizzazione)
🚀 Azioni svolte per la creazione del report

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
