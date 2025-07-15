# ⏱️ Porter Order Delivery Time Estimation: Turning Data into Delivery Precision

This solo project was developed as part of the Post Graduate Diploma program offered by IIIT Bangalore in collaboration with UpGrad.

---

## 🚀 Project Summary

Have you ever wondered how delivery apps like Porter estimate how long your order will take to arrive? This project tackles that challenge by building a reliable **regression model to predict delivery times for Porter orders**.

By improving prediction accuracy, Porter can streamline its operations, manage its logistics more efficiently, and provide customers with realistic delivery expectations. This analysis identifies the **key variables that significantly impact delivery durations**, offering actionable insights for data-driven decisions.

---

## 📊 Understanding the Dataset

The dataset `porter_data_1.csv` includes **175,777 order entries** and 14 descriptive columns. Each row provides detailed insights about a single delivery journey.

**Key fields include:**

- `market_id`: The region or zone where the order originated.  
- `created_at`: The timestamp when the order was placed.  
- `actual_delivery_time`: The timestamp when the delivery was completed.  
- `store_primary_category`: The type of restaurant (e.g., fast food, Indian).  
- `order_protocol`: Method of order placement (e.g., app, phone).  
- `total_items`: Number of items in the order.  
- `subtotal`: Total cost of the order.  
- `num_distinct_items`: Number of different items ordered.  
- `min_item_price` & `max_item_price`: Range of item prices.  
- `total_onshift_dashers`: Number of available delivery partners.  
- `total_busy_dashers`: Number of delivery partners already occupied.  
- `total_outstanding_orders`: Number of pending orders.  
- `distance`: Distance between the restaurant and the customer.

---

## ⚙️ Data Pipeline Overview

The end-to-end process consisted of the following major steps:

1. **Data Loading**: The dataset was read from a CSV file and inspected for completeness and structure.  
2. **Data Preprocessing & Feature Engineering**: Timestamps were converted, new features such as `order_hour` and `isWeekend` were created, and the target variable `time_taken` was derived. Average delivery time: **~46.20 minutes**.  
3. **Exploratory Data Analysis (EDA)**: Distributions, correlations, and outliers were explored. The feature `distance` had the **strongest positive correlation (0.461)** with delivery time. Skewed variables were adjusted using **Winsorization**.  
4. **Model Development**: After splitting the data (80% training / 20% test), a **Linear Regression model** was trained. **Recursive Feature Elimination (RFE)** selected the top 11 most relevant predictors.  
5. **Model Evaluation**: The model’s accuracy and effectiveness were validated on test data.

---

## 🎯 Model Performance

The Linear Regression model delivered strong predictive performance:

- **R²: 0.8693** — It explains approximately **87%** of the variation in delivery time.  
- **RMSE: 3.38 minutes** — Predictions deviate by ~3.38 minutes on average.  
- **MAE: 2.41 minutes** — Average absolute error is just 2.41 minutes.

### 🔍 Feature Importance (Coefficient Insights):

- **`distance`**: Most influential — every unit increase adds ~12.83 minutes.  
- **`total_outstanding_orders`**: High backlog increases time by ~18.59 minutes.  
- **`subtotal`**: Higher-value orders take slightly longer (~2.34 minutes increase).  
- **`total_items`**: Each additional item increases delivery time by ~0.05 minutes.

---

## 🌟 Key Insights

- **Distance is the dominant factor** affecting delivery speed.  
- **Workload and congestion** (like busy dashers or outstanding orders) are major contributors to delays.  
- The **model is generalizable** and performs well on new data.  
- **Data cleaning and feature engineering** played a crucial role in model success.

---

## 🛠️ Tools & Libraries Used

- **Python 3.x**  
- **pandas**, **numpy** — For data handling and numerical operations  
- **matplotlib**, **seaborn** — For visual exploration  
- **scikit-learn** — For model building, feature selection, and evaluation  
- **statsmodels**, **scipy** — For statistical analysis and residual diagnostics

---
