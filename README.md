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
  Party Alliance = 
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

- **Vote Share %**: Calculates the percentage of votes received by a party.
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

