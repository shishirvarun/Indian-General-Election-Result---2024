# Indian-General-Election-Result---2024
# Election Results Analysis

![Gen_Election](https://github.com/user-attachments/assets/adf7db51-b844-433a-bb56-9511b7fb9943)
![Gen_Elec2](https://github.com/user-attachments/assets/12b75b0b-ca33-4c64-9971-b634e49afd23)


This repository contains a Power BI project that analyzes election results to uncover key insights on voter behavior, party performance, and constituency-level trends. The project demonstrates advanced data visualization and analytical capabilities using Power BI and DAX (Data Analysis Expressions).

## Overview
The objective of this project is to provide a comprehensive analysis of election results using interactive dashboards and advanced analytics. It offers insights into vote shares, seat distributions, and top-performing candidates.

## Features
### 1. **Dynamic Dashboards**
- Interactive visuals displaying vote shares, seat distributions, and candidate performance.
- Integrated slicers and filters for detailed regional and party-based analysis.

### 2. **Key Metrics & DAX Functions**
The project includes several custom measures created using DAX functions:

- **Party Alliance**: 
  ```DAX
  IF(
    PartyWiseResults[Party] = "Bharatiya Janata Party - BJP" ||
    PartyWiseResults[Party] = "Telugu Desam - TDP" ||
    PartyWiseResults[Party] = "Janata Dal  (United) - JD(U)" ||
    PartyWiseResults[Party] = "Shiv Sena - SHS" ||
    PartyWiseResults[Party] = "AJSU Party - AJSUP" ||
   PartyWiseResults[Party] = "Apna Dal (Soneylal) - ADAL" ||
    PartyWiseResults[Party] = "Asom Gana Parishad - AGP" ||
    PartyWiseResults[Party] = "Hindustani Awam Morcha (Secular) - HAMS" ||
    PartyWiseResults[Party] = "Janasena Party - JnP" ||
    PartyWiseResults[Party] = "Janata Dal  (Secular) - JD(S)" ||
    PartyWiseResults[Party] = "Lok Janshakti Party(Ram Vilas) - LJPRV" ||
    PartyWiseResults[Party] = "Nationalist Congress Party - NCP" ||
    PartyWiseResults[Party]= "Rashtriya Lok Dal - RLD" ||
    PartyWiseResults[Party] = "Sikkim Krantikari Morcha - SKM",
    "NDA",
    IF(
        PartyWiseResults[Party] = "Indian National Congress - INC" ||
        PartyWiseResults[Party] = "Aam Aadmi Party - AAAP" ||
        PartyWiseResults[Party] = "All India Trinamool Congress - AITC" ||
        PartyWiseResults[Party] = "Bharat Adivasi Party - BHRTADVSIP" ||
        PartyWiseResults[Party]= "Communist Party of India  (Marxist) - CPI(M)" ||
        PartyWiseResults[Party] = "Communist Party of India  (Marxist-Leninist)  (Liberation) - CPI(ML)(L)" ||
        PartyWiseResults[Party] = "Communist Party of India - CPI" ||
        PartyWiseResults[Party] = "Dravida Munnetra Kazhagam - DMK" ||
        PartyWiseResults[Party] = "Indian Union Muslim League - IUML" ||
        PartyWiseResults[Party] = "Jammu & Kashmir National Conference - JKN" ||
        PartyWiseResults[Party] = "Jharkhand Mukti Morcha - JMM" ||
        PartyWiseResults[Party] = "Kerala Congress - KEC" ||
        PartyWiseResults[Party] = "Marumalarchi Dravida Munnetra Kazhagam - MDMK" ||
        PartyWiseResults[Party] = "Nationalist Congress Party Sharadchandra Pawar - NCPSP" ||
        PartyWiseResults[Party] = "Rashtriya Janata Dal - RJD" ||
        PartyWiseResults[Party] = "Rashtriya Loktantrik Party - RLTP" ||
        PartyWiseResults[Party] = "Revolutionary Socialist Party - RSP" ||
        PartyWiseResults[Party] = "Samajwadi Party - SP" ||
        PartyWiseResults[Party] = "Shiv Sena (Uddhav Balasaheb Thackrey) - SHSUBT" ||
        PartyWiseResults[Party] = "Viduthalai Chiruthaigal Katchi - VCK",
        "I.N.D.I.A.",
        "OTHER"
    )
)

  ```

- **Vote Share %**:
  ```DAX
  DIVIDE([Total Votes], CALCULATE([Total Votes], ALL(ConstituencyWiseResults[Party ID])), 0)
  ```

- **Seat Percentages**:
  - **India Seat %**:
    ```DAX
    DIVIDE([Total INDIA Seats], [Total Seats], 0)
    ```
  - **NDA Seat %**:
    ```DAX
    DIVIDE([Total NDA Seats], [Total Seats], 0)
    ```
  - **Other Seat %**:
    ```DAX
    DIVIDE([Total Other Seats], [Total Seats], 0)
    ```

- **Top 10 Candidates by Vote Share**:
  ```DAX
  TOPN(10, ALL(ConstituencyWiseDetails[Candidate]), [Vote Share %])
  ```

- **Average Votes per Constituency**:
  ```DAX
  AVERAGEX(SUMMARIZE(ConstituencyWiseResults, ConstituencyWiseResults[Constituency ID]), [Total Votes])
  ```

### 3. **Insights**
- Analyzed vote share percentages across political parties.
- Identified top-performing candidates by vote share.
- Calculated seat distributions and voter averages across constituencies.
- Highlighted trends in voter turnout and party dominance.

## Installation and Usage
1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/election-results-analysis.git
   ```

2. Open the provided `.pbix` file in Power BI Desktop.

3. Explore the interactive dashboards and analyze the data insights.

<div align="center">

# General Election 2024 Analysis

## Indian General Elections 2024 Data Insights

This project contains a collection of SQL queries to analyze the results of the 2024 Indian General Elections. The analysis covers various aspects such as seat distribution, party performance, alliance classification, and constituency-level details.

---

## Table of Contents

1. [Overview](#overview)
2. [Queries](#queries)
   - [Total Seats](#total-seats)
   - [State-wise Seat Distribution](#state-wise-seat-distribution)
   - [NDA Alliance Performance](#nda-alliance-performance)
   - [I.N.D.I.A. Alliance Performance](#india-alliance-performance)
   - [Party Alliance Classification](#party-alliance-classification)
   - [Constituency-level Analysis](#constituency-level-analysis)
   - [Vote Distribution Analysis](#vote-distribution-analysis)
   - [State-level Party Performance](#state-level-party-performance)
   - [Alliance-wise State Performance](#alliance-wise-state-performance)
   - [Top Candidates by Votes](#top-candidates-by-votes)
3. [License](#license)

---

## Overview

The dataset includes detailed results from the 2024 Indian General Elections, spanning:

- Constituency-wise and state-wise results.
- Performance of major alliances like NDA and I.N.D.I.A.
- Insights into winning candidates, vote margins, and party-level statistics.

---

## Queries

### Total Seats

```sql
SELECT DISTINCT COUNT(`Parliament Constituency`) AS Total_Seats
FROM constituencywise_results;
```
This query calculates the total number of seats in the election.

---

### State-wise Seat Distribution

```sql
SELECT
    s.state AS state_name,
    COUNT(sr.`Parliament Constituency`) AS total_seats
FROM constituencywise_results cr
INNER JOIN statewise_results sr
    ON cr.`Parliament Constituency` = sr.`Parliament Constituency`
INNER JOIN states s
    ON s.`State ID` = sr.`State ID`
GROUP BY s.State;
```
This query shows the total number of seats available for elections in each state.

---

### NDA Alliance Performance

**Total Seats Won by NDA:**

```sql
SELECT
    SUM(CASE WHEN PARTY IN (
        'Bharatiya Janata Party - BJP',
        'Telugu Desam - TDP',
        'Janata Dal (United) - JD(U)',
        'Shiv Sena - SHS',
        'AJSU Party - AJSUP',
        'Apna Dal (Soneylal) - ADAL',
        'Asom Gana Parishad - AGP',
        'Hindustani Awam Morcha (Secular) - HAMS',
        'Janasena Party - JnP',
        'Janata Dal (Secular) - JD(S)',
        'Lok Janshakti Party(Ram Vilas) - LJPRV',
        'Nationalist Congress Party - NCP',
        'Rashtriya Lok Dal - RLD',
        'Sikkim Krantikari Morcha - SKM'
    )
    THEN WON ELSE 0 END) AS NDA_Total_Seats_Won
FROM partywise_results;
```

**Seats Won by Individual NDA Parties:**

```sql
SELECT party AS Party_Name,
    WON AS Seats_Won
FROM partywise_results
WHERE PARTY IN (
    'Bharatiya Janata Party - BJP',
    'Telugu Desam - TDP',
    'Janata Dal (United) - JD(U)',
    'Shiv Sena - SHS',
    'AJSU Party - AJSUP',
    'Apna Dal (Soneylal) - ADAL',
    'Asom Gana Parishad - AGP',
    'Hindustani Awam Morcha (Secular) - HAMS',
    'Janasena Party - JnP',
    'Janata Dal (Secular) - JD(S)',
    'Lok Janshakti Party(Ram Vilas) - LJPRV',
    'Nationalist Congress Party - NCP',
    'Rashtriya Lok Dal - RLD',
    'Sikkim Krantikari Morcha - SKM'
)
ORDER BY Seats_Won DESC;
```

---

### I.N.D.I.A. Alliance Performance

**Total Seats Won by I.N.D.I.A.:**

```sql
SELECT
    SUM(CASE WHEN party IN (
        'Indian National Congress - INC',
        'Aam Aadmi Party - AAAP',
        'All India Trinamool Congress - AITC',
        'Bharat Adivasi Party - BHRTADVSIP',
        'Communist Party of India (Marxist) - CPI(M)',
        'Communist Party of India (Marxist-Leninist) (Liberation) - CPI(ML)(L)',
        'Communist Party of India - CPI',
        'Dravida Munnetra Kazhagam - DMK',
        'Indian Union Muslim League - IUML',
        'Jammu & Kashmir National Conference - JKN',
        'Jharkhand Mukti Morcha - JMM',
        'Kerala Congress - KEC',
        'Marumalarchi Dravida Munnetra Kazhagam - MDMK',
        'Nationalist Congress Party Sharadchandra Pawar - NCPSP',
        'Rashtriya Janata Dal - RJD',
        'Rashtriya Loktantrik Party - RLTP'
    )
    THEN WON ELSE 0 END) AS INDIA_Total_Seats_Won
FROM partywise_results;
```

**Seats Won by Individual I.N.D.I.A. Parties:**

```sql
SELECT party AS Party_Name, WON AS Seats_Won
FROM partywise_results
WHERE PARTY IN (
    'Indian National Congress - INC',
    'Aam Aadmi Party - AAAP',
    'All India Trinamool Congress - AITC',
    'Communist Party of India - CPI',
    'Rashtriya Janata Dal - RJD'
)
ORDER BY Seats_Won DESC;
```

---

### Party Alliance Classification

```sql
ALTER TABLE partywise_results
ADD party_alliance VARCHAR(50);

UPDATE partywise_results
SET party_alliance = 'I.N.D.I.A.'
WHERE PARTY IN ('Indian National Congress - INC', 'Aam Aadmi Party - AAAP', ...);

UPDATE partywise_results
SET party_alliance = 'NDA'
WHERE PARTY IN ('Bharatiya Janata Party - BJP', 'Shiv Sena - SHS', ...);

UPDATE partywise_results
SET party_alliance = 'OTHER'
WHERE party_alliance IS NULL;
```

---

### Constituency-level Analysis

```sql
SELECT
    cr.`Winning Candidate`,
    pr.`Party`,
    pr.party_alliance,
    cr.`Total Votes`,
    cr.margin,
    cr.`Constituency Name`
FROM constituencywise_results cr
INNER JOIN partywise_results pr ON cr.`Party ID` = pr.`Party ID`
WHERE cr.`Constituency Name` = 'AGRA';
```

---

### Vote Distribution Analysis

```sql
SELECT cd.`EVM Votes`,
    cd.`Postal Votes`,
    cd.`Total Votes`,
    cd.`Candidate`,
    cr.`Constituency Name`
FROM constituencywise_results cr
INNER JOIN constituencywise_details cd
    ON cr.`Constituency ID` = cd.`Constituency ID`
WHERE cr.`Constituency Name` = 'AMROHA';
```

---

### State-level Party Performance

```sql
SELECT
    p.Party, COUNT(cr.`Constituency ID`) AS Seats_Won
FROM constituencywise_results cr
JOIN partywise_results p ON cr.`Party ID` = p.`Party ID`
WHERE s.`State` = 'Uttar Pradesh'
GROUP BY p.Party
ORDER BY Seats_Won DESC;
```

---

### Alliance-wise State Performance

```sql
SELECT
    s.State,
    SUM(CASE WHEN p.party_alliance = 'NDA' THEN 1 ELSE 0 END ) AS NDA_Seat_Won,
    SUM(CASE WHEN p.party_alliance = 'I.N.D.I.A.' THEN 1 ELSE 0 END ) AS INDIA_Seat_Won,
    SUM(CASE WHEN p.party_alliance = 'OTHER' THEN 1 ELSE 0 END ) AS OTHER_Seat_Won
FROM constituencywise_results cr
GROUP BY s.State;
```

---

### Top Candidates by Votes

```sql
SELECT
    cr.`Constituency Name`,
    cd.`Constituency ID`,
    cd.`Candidate`,
    cd.`EVM Votes`
FROM constituencywise_details cd
WHERE cd.`EVM Votes` =(
    SELECT MAX(cd1.`EVM Votes`) FROM constituencywise_details cd1
)
ORDER BY cd.`EVM Votes` DESC
LIMIT 10;
```

---

</div>




## Technologies Used
- **Power BI**: For creating interactive dashboards and visualizations.
- **DAX**: For advanced data manipulation and calculations.

## Contributing
Contributions are welcome! If you have suggestions for improvements or new features, please create a pull request or open an issue.


## Contact
For questions or collaborations, feel free to reach out:
- **Email**: varunshishir@gmail.com
- **LinkedIn**: www.linkedin.com/in/shishir-varun-744727152

---
### Note
This project is a demonstration of analytical skills and does not reflect real-world election data. The dataset used is for educational purposes only.

