# 📱 Mobile Sales Analytics Dashboard

An interactive Power BI dashboard built to analyze mobile phone sales data and uncover insights related to revenue, customer behavior, product performance, and sales trends.

---

## 🚀 Project Overview

Businesses make hundreds or even thousands of sales every day, generating large volumes of data. However, without proper analysis, it can be difficult to understand what is actually driving performance. This project uses Power BI to turn raw sales data into meaningful insights, helping users monitor key metrics, identify trends, and make more informed decisions.

The dashboard helps answer questions such as:

- Which mobile brands are generating the highest revenue?
- Which cities contribute the most to overall sales?
- How are sales trending over time?
- Which payment methods are most commonly used by customers?
- How does current performance compare to previous periods?
- Which products are driving business growth?
- What patterns can be observed in customer ratings?

To answer these questions, I developed a multi-page Power BI dashboard using DAX measures, calculated columns, and time intelligence functions.

---

# 📊 Dashboard Pages

## 1️⃣ Sales Dashboard

The main dashboard provides a high-level overview of business performance through key metrics and interactive visualizations.

![Sales Dashboard](Screenshots/Sales_Dashboard.png)

### Key KPIs

| KPI | Value |
|------|------|
| Total Sales | 769M |
| Total Quantity Sold | 19K |
| Total Transactions | 4K |
| Average Price | 40.11K |

### Visualizations Included

- Revenue by City (Map Visualization)
- Quantity Sold by Month
- Sales by Mobile Model
- Sales by Day of Week
- Customer Rating Analysis
- Payment Method Distribution
- Brand Performance Comparison

### Business Value

This dashboard enables stakeholders to quickly understand overall sales performance and identify key revenue drivers.

---

## 2️⃣ Month-To-Date (MTD) Dashboard

The MTD dashboard focuses on tracking cumulative sales performance throughout a selected month.

![MTD Dashboard](Screenshots/MTD_Report.png)

### Key Features

- Daily cumulative sales tracking
- Month-wise performance monitoring
- Dynamic filtering capabilities
- Revenue progression analysis

### Business Value

This dashboard helps monitor sales progress before month-end and allows decision-makers to identify performance trends early.

---

## 3️⃣ Same Period Last Year Dashboard

This dashboard compares current sales performance with the same period from the previous year.

![Same Period Last Year Dashboard](Screenshots/Same_Period_Last_Year.png)

### Analysis Included

- Year-over-Year Comparison
- Quarterly Comparison
- Monthly Comparison
- Historical Benchmarking

### Business Value

Year-over-Year analysis helps determine whether the business is growing and highlights periods that require additional attention.

---

# 🏗 Data Modeling

A dedicated Calendar Table was created to support advanced time intelligence calculations and improve reporting flexibility.

### Fact Table

**Sales_Data**

Contains transactional information such as:

- Transaction ID
- Date
- Mobile Model
- Brand
- City
- Units Sold
- Total Sales
- Payment Method
- Customer Ratings

### Dimension Table

**Calendar Table**

Contains:

- Year
- Quarter
- Month
- Day
- Day Name

Creating a separate date table is a Power BI best practice and was essential for implementing MTD and Same Period Last Year calculations.

---

# 🧮 DAX Measures Created

### Total Sales

```DAX
Total Sales =
SUM(Sales_Data[Total Sales])
```

### Total Quantity

```DAX
Total Quantity =
SUM(Sales_Data[Units Sold])
```

### Transactions

```DAX
Transactions =
DISTINCTCOUNT(Sales_Data[Transaction ID])
```

### Average Price

```DAX
Average Price =
DIVIDE(
    [Total Sales],
    [Total Quantity]
)
```

### Month-To-Date Sales

```DAX
MTD Sales =
TOTALMTD(
    [Total Sales],
    Calendar[Date]
)
```

### Same Period Last Year

```DAX
Same Period Last Year =
CALCULATE(
    [Total Sales],
    SAMEPERIODLASTYEAR(Calendar[Date])
)
```

---

# 🏷 Calculated Column

### Rating Status

To simplify customer satisfaction analysis, customer ratings were grouped into categories.

```DAX
Rating Status =
SWITCH(
    TRUE(),
    Sales_Data[Customer Ratings] >= 4, "Good",
    Sales_Data[Customer Ratings] >= 3, "Average",
    "Poor"
)
```

This allowed ratings to be analyzed more effectively across the dashboard.

---

# 📈 Key Insights

After analyzing the dataset, several interesting trends emerged:

- The business generated approximately **769M** in total revenue.
- More than **19,000 units** were sold across over **4,000 transactions**.
- Certain mobile models contributed significantly more revenue than others.
- Customer ratings were predominantly positive.
- Digital payment methods accounted for a large share of transactions.
- Sales performance varied across cities, highlighting regional demand differences.
- Time-based analysis revealed fluctuations in monthly sales performance and provided visibility into year-over-year growth trends.

---

# 💡 What I Learned

This project helped me strengthen my understanding of:

- Power BI Dashboard Development
- Data Modeling Concepts
- Relationship Management
- DAX Measures
- Calculated Columns
- Time Intelligence Functions
- KPI Reporting
- Business Performance Analysis
- Data Storytelling

One of the biggest takeaways from this project was learning how important a proper data model is when building analytical solutions. Creating a Calendar Table and implementing Time Intelligence functions such as `TOTALMTD()` and `SAMEPERIODLASTYEAR()` gave me a much deeper understanding of how business reporting works in real-world scenarios.

---

# 🛠 Tools & Technologies

- Power BI Desktop
- DAX (Data Analysis Expressions)
- Power Query
- Microsoft Excel
- Data Modeling
- Business Intelligence Reporting

---

# 🎯 Skills Demonstrated

### Business Intelligence

- KPI Reporting
- Executive Dashboard Development
- Data Storytelling

### Data Analysis

- Sales Analysis
- Product Performance Analysis
- Customer Analysis
- Trend Analysis
- Geographic Analysis

### Power BI

- Interactive Dashboards
- DAX Measures
- Calculated Columns
- Time Intelligence
- Data Modeling

