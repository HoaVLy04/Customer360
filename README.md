# CUSTOMER 360

**Date: July 3**

---

## Table of Contents

1. [Project Overview](#project-overview)
2. [Analysis Model](#analysis-model)
   - [Customer 360](#customer-360)
   - [RFM Metrics](#rfm-metrics)
3. [Customer Segmentation Analysis](#customer-segmentation-analysis)
   - [Data](#data)
   - [RFM Calculation](#rfm-calculation)
   - [Customer Segmentation](#customer-segmentation)
4. [Findings](#findings)

---

## Project Overview

Using the **Customer 360 concept** and **RFM analysis method**, this project categorizes customers into different groups to help the marketing team create effective strategies tailored to each customer segment.

---

## Analysis Model

### 1. Customer 360

The **Customer 360 view** is a comprehensive approach to understanding customers by aggregating data from multiple touchpoints and channels to create a unified and holistic view of each customer. Generally, the Customer 360 includes:

- **Demographic Data**: Basic information about customers such as age, gender, location, etc.
- **Transaction Data**: Details of past transactions, including purchase history, order value, frequency of purchase, etc.
- **Interaction Data**: Customer interactions with the company’s various departments, such as sales, marketing, customer service, etc.
- **Behavioral Data**: Data about customers’ preferences, opinions, needs, etc.

### 2. RFM Metrics

**RFM** stands for **Recency**, **Frequency**, and **Monetary**. RFM Analysis is a customer segmentation technique used in marketing to categorize customers based on their purchasing behavior.

- **Recency**: How recently or the last time the customer has made a purchase.
- **Frequency**: How often the customer makes a purchase.
- **Monetary**: Total amount of money the customer has spent.

This report measures these three components (Recency, Frequency, Monetary) on a scale of **1 to 4**, where **4 is the highest score**.

---

## Customer Segmentation Analysis

### 1. Data

- Analyzed **114,081 active customers** within a **3-month period** from **June 1, 2022, to September 1, 2022**.
- **Tables Used**:
  - `Customer_registered`
  - `Customer_transaction`

### 2. RFM Calculation

- **Recency** = `datediff(max(purchased_date), '2022-09-01')`  
  The number of days since the customer's last purchase compared to **September 1, 2022**.
  
- **Frequency** = `count(distinct(purchase_date)) / contract_age`  
  The frequency of purchases normalized by the customer's contract age.
  
- **Monetary** = `sum(gmv)`  
  The total Gross Merchandise Value (GMV) spent by the customer.

- **Interquartile Range (IQR)**: Measures the spread of the middle half of the data (middle 50% of the sample).

Using the **IQR method**, the RFM scores are calculated as follows:

| Metric | Score 1       | Score 2           | Score 3            | Score 4              |
|--------|---------------|-------------------|--------------------|----------------------|
| R      | 0–31 days     | 31–62 days        | 62–92 days         | 92+ days             |
| F      | 0–0.0005 times| 0.0006–0.0007 times | 0.0005–0.0006 times | 0.0007–0.004 times   |
| M      | 0–75,000 VND  | 75,000–85,000 VND | 85,000–105,000 VND | 105,000–568,182 VND  |

### 3. Customer Segmentation

Based on the **BCG Matrix**, customers are divided into four groups:

- **Star (VIP)**: Customers who have high engagement and spend the most.
- **Question Mark (Potential)**: Customers who have high engagement but don’t spend too much.
- **Cash Cow (Loyal)**: Customers who have low engagement but spend significantly.
- **Dogs (About to Sleep)**: Customers who have low engagement and low spending.

**Applied to the data:**

| Customer Segmentation | Description                                                                 | RFM Score                  |
|------------------------|-----------------------------------------------------------------------------|----------------------------|
| **Star**               | Customers frequently visit the website, make purchases, and spend the most money | 443                        |
| **Question Marks**     | Customers frequently visit the website but spend less or don’t make any purchase | 421, 422, 432, 332, 342, 442, 343, 333 |
| **Cash Cow**           | Customers visit less but spend as much as VIPs                              | 233, 344, 214, 114, 124, 144 |
| **Dogs**               | Customers rarely visit and make the least purchase                          | 211, 121, 232              |

---

## Findings

- There are **114,080 customers**, who spent a total GMV of approximately **11 billion VND**.
  
- Among the four segments (excluding the ‘others’ segment), the **Star segment** is the largest (**18.21%**). This shows that the company’s marketing strategy is well-executed since it attracted a large amount of ‘Star’ customers. In addition, the company should also do more research about customers in the ‘Others’ segment since it is the biggest segment. The third place goes to the **Dogs segment**, followed by **Question Marks**, and **Cash Cows** segments.

- Similar to the pie chart above, in which customers in the ‘Others’ segment are the largest, this pie chart shows that those customers also contribute to the revenue of the company a considerable amount of **4 billion**. Following up is the customers from the **Star segment** with **27.75%** of the total revenue.

- Surprisingly, customers in the **Star segment** spent the largest average amount of money. Despite being the largest segment in the other chart, the **Others segment** placed third in the average amount of money spent.

---
