# 🎮 Power Game Analysis — Sales & Customer Insights Dashboard (Power BI) — PB21

## 📌 Project Overview  
This Power BI dashboard analyzes **game sales data** from a fictional gaming company, focusing on **customer demographics, order patterns, game category performance, regional revenue distribution, and time-based trends**.

Designed as a **comprehensive analytics portfolio project**, it demonstrates **advanced DAX modeling, time intelligence, geographic mapping, and business storytelling** — ideal for showcasing skills in gaming industry analytics, retail, and consumer goods.

---

## 👀 Dashboard Preview  
<img width="584" height="332" alt="PB211" src="https://github.com/user-attachments/assets/f06b6c9e-6e4a-4dbc-ab95-13835c32fce4" />
<img width="583" height="320" alt="PB212" src="https://github.com/user-attachments/assets/8d4ba7f4-4cd6-4a96-9cdd-de527a9e08d1" />
<img width="577" height="320" alt="PB213" src="https://github.com/user-attachments/assets/442c278d-21e8-47fa-b960-31924b5ce968" />
<img width="571" height="323" alt="PB214" src="https://github.com/user-attachments/assets/fbd05473-5858-42b9-8a5e-2b681294c153" />
<img width="578" height="326" alt="PB215" src="https://github.com/user-attachments/assets/04e49237-c519-4592-841d-9b5e14e93a6d" />


*(Screenshot captured May 1, 2026)*

---

## 🎯 Objectives  
- Analyze **customer demographics by age, gender, and typology**  
- Track **order volume and revenue by game category**  
- Visualize **regional performance across French cities**  
- Monitor **monthly and yearly sales trends**  
- Identify **top-performing games and customer segments**  
- Practice **multi-tab navigation and visual storytelling**

---

## 📊 Dashboard Breakdown

### 🔹 Key Metrics (KPIs)
- **Total Revenue**: €296,290  
- **Total Orders**: 1,185  
- **Average Customer Age**: 28.74 years  
- **Total Games Sold**: 1,612  
- **Revenue by Region**: Strasbourg (€90,720), Bordeaux (€69,650), Lille (€67,470)  
- **Top Games**: R-type (60 units), The Karate Tournament (51 units)

---

### 🔹 Clients Page
- **Age Distribution**: Most customers are between 20–30 years old  
- **Gender Split**: 50% female, 50% male  
- **Customer Typology**: Argent (25%), Or (44%), Platine (31%)  
- **Top 3 Customers**: Keith Stephens (26 orders), Philip Bailey (24), Arthur Webb (23)  
- **Visuals**: Sankey diagram, bar chart by age, top customers table

---

### 🔹 Orders Page
- **Total Orders**: 1,023  
- **Game Categories**: Combat (24), Plateforme (16), Tir (16), Reflexion (5)  
- **Order Evolution**: Clear seasonal peaks in summer months  
- **Visuals**: Line chart (orders over time), scatter plot (orders vs. revenue)

---

### 🔹 Games Page
- **Top Games by Orders**:  
  - R-type: 60  
  - The Karate Tournament: 51  
  - Rampage: 47  
- **Revenue by Category**: Combat (€318K), Plateforme (€16K), Tir (€16K)  
- **Visuals**: Bar chart by category, monthly games ordered trend

---

### 🔹 Revenue Page
- **Total Revenue**: €296,290  
- **Top Regions**: Strasbourg (€90,720), Bordeaux (€69,650), Lille (€67,470)  
- **YoY Growth**: -0.07% (slight decline from 2020 to 2021)  
- **Visuals**: Revenue by city, monthly revenue line chart, target comparison

---

### 🔹 Region/Store Page
- **Top Cities**: Bordeaux (239 orders), Marseille (156)  
- **Geographic Map**: Visualized across France  
- **Regional Revenue**: Nord (€593K), Sud (€318K), Centre (€296K)  
- **Visuals**: Map, bar chart by city, regional comparison

---

## 📐 Methodology
- **Data Model**: Star schema with `Orders` as fact table and `Clients`, `Games`, `Regions` as dimensions  
- **Date Table**: Created using `CALENDAR()` for time intelligence  
- **DAX Measures**: Used `CALCULATE`, `SUMX`, `TOTALYTD`, `SAMEPERIODLASTYEAR`, `RANKX`, etc.  
- **Visual Design**: Consistent color scheme, clear labels, interactive slicers

---

## 🛠️ Tools & Technologies
- **Power BI Desktop**  
- **Intermediate–Advanced DAX**  
- **Geospatial visualization (France map)**  
- **Multi-tab navigation (Home / Action / Detail style)**  
- **Dashboard layout & storytelling**

---

## 📌 Key Insights
✅ **Even gender split** — balanced customer base  
✅ **20–30 age group dominates** — core demographic  
✅ **Combat games drive most revenue** (€318K)  
✅ **Strasbourg is top region** (€90,720)  
✅ **Slight YoY decline (-0.07%)** — needs investigation  
✅ **Strong seasonal pattern** — summer = peak sales  
✅ **R-type is #1 game** — potential for expansion

---

## 📁 Repository Structure
├── Power_Game_Analysis_PB21.pbix
├── Dataset/
│ ├── Clients.csv
│ ├── Games.csv
│ ├── Orders.csv
│ └── Regions.csv
├── Screenshots/
│ └── power_game_analysis_pb21.png
└── README.md


---

## 🚀 Project Purpose
This project was built as a **portfolio Power BI project** to:  
- Practice **gaming industry analytics**  
- Improve **dashboard design and analytical storytelling**  
- Apply **customer segmentation, time intelligence, and regional analysis**  
- Simulate **analytics reporting for gaming companies**

---

## 📬 Contact
**Mustapha Tarfi**  
📍 Morocco  
🔗 LinkedIn: [https://www.linkedin.com/in/mustapha-tarfi-1106b5283/](https://www.linkedin.com/in/mustapha-tarfi-1106b5283/)  

---

## 📝 DAX Measures

### 🔹 Basic Measures
```dax
Total Revenue = SUM(Orders[Revenue])
Total Orders = COUNT(Orders[OrderID])
Avg Customer Age = AVERAGE(Clients[Age])
Total Games Ordered = SUM(Orders[Quantity])
Revenue by Region = CALCULATE([Total Revenue], ALL(Orders[City]), VALUES(Regions[Region]))

Revenue Growth % = 
VAR CurrentYear = [Total Revenue]
VAR PreviousYear = CALCULATE([Total Revenue], SAMEPERIODLASTYEAR('Date'[Date]))
RETURN DIVIDE(CurrentYear - PreviousYear, PreviousYear, 0)

Top Game = TOPN(1, VALUES(Games[GameName]), [Total Revenue])

Customer Typology Distribution = 
DIVIDE(
    CALCULATE(COUNT(Clients[ClientID]), Clients[Typology] = "Argent"),
    COUNT(Clients[ClientID])
)

Revenue by Category = 
CALCULATE([Total Revenue], ALL(Orders[GameCategory]), VALUES(Games[Category]))

Revenue per Customer = DIVIDE([Total Revenue], DISTINCTCOUNT(Clients[ClientID]))

Monthly Revenue Trend = 
CALCULATE([Total Revenue], DATESINPERIOD('Date'[Date], MAX('Date'[Date]), -3, MONTH))

Top 3 Games = TOPN(3, VALUES(Games[GameName]), [Total Revenue])

Regional Revenue Rank = RANKX(ALL(Regions[Region]), [Revenue by Region], , DESC)

Game Category Performance = DIVIDE([Revenue by Category], [Total Revenue])
