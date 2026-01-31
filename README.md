# 📱 Mobile Sales Analysis – Power BI Case Study

## 📌 Project Overview

This project presents an **end-to-end Mobile Sales Analysis dashboard built in Power BI**, covering **sales performance, profitability, seasonality, inventory costs, brand performance, distributor efficiency**, and a **dynamic EMI Calculator** feature.

The dashboard answers **real business questions** using interactive visuals, DAX measures, and advanced Power BI features such as **tooltips, bookmarks, parameters, and forecasting**.

---

## 🛠 Tools & Technologies

**ATS Keywords:** Power BI, DAX, Data Analytics, Business Intelligence, Sales Analysis, Profit Analysis, Forecasting, KPI Dashboard, EMI Calculator, Financial Modeling

* **Tool:** Microsoft Power BI
* **Language:** DAX
* **Features Used:**

  * Measures & Calculated Columns
  * Time Intelligence
  * Tooltips
  * Bookmarks & Buttons
  * Numeric Parameters
  * Forecasting
  * Interactive Slicers

---

## 🎯 Business Questions Answered & Insights

Below are the **core business questions** addressed through this Power BI dashboard and analysis:

1. **From 2018–2021, which country and distributor achieved the best sales performance?**
2. **What are the seasonal sales trends across countries and distributors?**
3. **How do inventory costs vary seasonally by country and distributor?**
4. **What are the seasonal net profit trends for each country and distributor?**
5. **Each year, which brand was the top seller in each country and distributor?**
6. **Who were the most successful sales representatives and distributors in each country?**
7. **Which countries recorded the lowest and highest inventory costs from 2018–2021?**
8. **Which countries recorded the lowest and highest net profits from 2018–2021?**
9. **Can sales trends for 2023 be predicted based on historical data?**
10. **What recommendations can be made to optimize net sales based on top-performing countries?**

---

### 📌 Insights & DAX-Based Analysis

### 1️⃣ From 2018–2021, which country and distributor achieved the best sales performance?

**Chart Used:** Bar Chart + KPI Cards

**Insight:**

* **USA** consistently delivered the highest total sales from 2018–2021
* **Tuenti** emerged as the top-performing distributor across multiple countries

**DAX:**

```DAX
Total Sales = SUM(Sales[SalesAmount])
```

---

### 2️⃣ What are the seasonal sales trends across countries and distributors?

**Chart Used:** Line Chart (Year/Month)

**Insight:**

* Strong sales spikes observed in **Q4 (Nov–Dec)** due to festive demand
* Sales dip consistently in **Q1**, indicating post-holiday slowdown

**DAX:**

```DAX
Monthly Sales = CALCULATE([Total Sales], DATESMTD('Date'[Date]))
```

---

### 3️⃣ How do inventory costs vary seasonally by country and distributor?

**Chart Used:** Column + Line Combo Chart

**Insight:**

* Inventory costs peak **before high-sales seasons**
* Countries with better demand forecasting maintain **stable inventory costs**

**DAX:**

```DAX
Inventory Cost = SUM(Inventory[InventoryCost])
```

---

### 4️⃣ What are the seasonal net profit trends for each country and distributor?

**Chart Used:** Line Chart

**Insight:**

* Net profit closely follows sales trends but drops during **high inventory buildup periods**
* Distributors with optimized stock cycles show **higher profit margins**

**DAX:**

```DAX
Net Profit = [Total Sales] - [Inventory Cost]
```

---

### 5️⃣ Each year, which brand was the top seller in each country and distributor?

**Chart Used:** Table + Rank

**Insight:**

* **Apple** dominated as top brand across most countries
* **Samsung** consistently ranked second

**DAX:**

```DAX
Brand Rank = RANKX(ALL(Brands[Brand]), [Total Sales], , DESC)
```

---

### 6️⃣ Who were the most successful sales representatives and distributors?

**Chart Used:** Bar Chart

**Insight:**

* Top distributors drive **70%+ of total revenue**
* High-performing reps show consistent monthly sales, not spikes

---

### 7️⃣ Which countries recorded the lowest and highest inventory costs?

**Chart Used:** Bar Chart

**Insight:**

* **El Salvador & Ireland** recorded highest inventory costs
* **Paraguay & Bolivia** maintained lean inventory operations

---

### 8️⃣ Which countries recorded the lowest and highest net profits?

**Chart Used:** Bar Chart

**Insight:**

* **USA & Brazil** generated highest net profits
* Countries with high inventory but low sales showed reduced margins

---

### 9️⃣ Can sales trends for 2023 be predicted based on historical data?

**Chart Used:** Line Chart with Forecast

**Insight:**

* Forecast shows **steady growth trend for 2023**
* Expected sales ~**60M+** based on historical momentum

---

### 🔟 Recommendations to optimize net sales

* Focus marketing & inventory on **USA, Brazil, Europe**
* Strengthen partnerships with **top distributors (Tuenti, Entel)**
* Reduce excess inventory before Q1
* Push EMI & financing offers to boost unit sales

---

## 📊 Dashboard Insights (Bullet Summary)
![Mobile Sales Dashboard](https://github.com/iamsumansaha/MobilePhone_Sales_2018-2021/blob/main/Dashboard/Screenshot%202026-01-31%20203024.png)


* Total Sales reached **127M** with **44M profit**
* Profit margin stabilized around **35%**
* 2021 was the **best-performing year**
* Apple leads both **sales & profit contribution**
* Inventory efficiency is a key profit driver

---

## 📊 Seasonal Dashboard
![Seasonal Analysis Dashboard](https://github.com/iamsumansaha/MobilePhone_Sales_2018-2021/blob/main/Dashboard/Screenshot%202026-01-31%20203038.png)


## ⚠️ Tooltip Value Issue (Why Values Look Wrong)

**Common Reasons:**

* Tooltip page not filtered by the same dimension
* Missing `ALLSELECTED()` in DAX
* Using calculated columns instead of measures

**Fix Example:**

```DAX
Tooltip Sales = CALCULATE([Total Sales], ALLSELECTED())
```

---

## 💳 EMI Calculator – Power BI Design

### EMI Calculator Requirements

* **Year Duration:** 0–5 years (Numeric Parameter)
* **Loan Amount:** Phone price (Brand-wise)
* **Interest Rate:** Fixed
* **User Input:** EMI / Duration

![EMI Calculator](https://github.com/iamsumansaha/MobilePhone_Sales_2018-2021/blob/main/Dashboard/Screenshot%202026-01-31%20203053.png)


---

### Step 1: Numeric Parameter

* Create parameter: `Loan_Years`
* Range: `0 to 5`

---

### Step 2: Loan Amount Measure

```DAX
Loan Amount = SELECTEDVALUE(Phones[Price])
```

---

### Step 3: EMI Formula (Fixed Interest)

```DAX
EMI =
VAR P = [Loan Amount]
VAR R = 0.12/12
VAR N = [Loan_Years] * 12
RETURN
IF(N=0, P, P * R * POWER(1+R, N) / (POWER(1+R, N) - 1))
```

---

### Step 4: Total Payable & Interest

```DAX
Total Payable = [EMI] * [Loan_Years] * 12
Total Interest = [Total Payable] - [Loan Amount]
```

---

## 📈 Charts Used in Dashboard

* KPI Cards (Sales, Profit, Units)
* Line Chart (Trends & Forecast)
* Bar Charts (Country, Brand, Distributor)
* Pie Chart (Distributor Share)
* Map (Sales by Country)
* Calendar Heatmap (Seasonality)
* Table (Top Brand per Country)

---

## 👤 Author

**Suman Saha**
Data Analyst | Power BI | DAX | Business Analytics

---

⭐ This project demonstrates **real-world BI problem solving**, financial modeling, and decision-driven dashboard design.
