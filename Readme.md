# 📊 Monthly Price Forecasting Model

## 🧩 Problem Statement

The objective of this project is to develop a forecasting model that predicts **average monthly prices for the next 12 months** using historical data. The dataset contains time-series information of prices, and the goal is to build a robust model that can capture trends, seasonality, and fluctuations in price behavior.

Multiple models were explored, including:
- SARIMAX (Statistical Time Series Model)
- Prophet (Additive Time Series Model)
- Support Vector Machine (Machine Learning Model)

The best-performing model was selected based on evaluation metrics.

---

## 🧹 Data Cleaning & Preprocessing

The following steps were performed to ensure data quality:

### 1. Handling Missing Values
- Missing values were handled using:
  - Forward fill (`ffill`)
  - Interpolation where necessary

### 2. Handling Outliers
- Outliers were detected using the **IQR (Interquartile Range)** method
- Extreme values were removed to prevent distortion in model training

### 3. Data Type Conversion
- Date column was converted to datetime format
- Data was sorted chronologically

### 4. Feature Engineering
- Extracted time-based features:
  - Year
  - Month
- Created lag features for ML models

---

## 🤖 Model Selection & Justification

Three models were trained and evaluated:

| Model     | MAE |
|----------|-----|
| SARIMAX  | 4975.48 |
| Prophet  | 1486.43 |
| SVM      | 1709.98 |

### ✅ Selected Model: **Prophet**

### Why Prophet?
- Handles **trend and seasonality automatically**
- Works well with **real-world business data**
- Robust to missing values and outliers
- Requires minimal parameter tuning
- Captures **non-linear patterns better than SARIMAX**

---

## 📈 Model Performance

The model was evaluated using **Mean Absolute Error (MAE)**:

- **Prophet MAE: 1486.43 (Best Performance)**

### Why MAE?
- Easy to interpret
- Measures average prediction error
- Preferred in business forecasting scenarios

---

## 💡 Business Recommendations

Based on predicted price trends:

### 📈 If Prices Are Expected to Rise:
- Procure inventory early (bulk purchasing)
- Lock supplier contracts at current prices
- Adjust product pricing strategies

### 📉 If Prices Are Expected to Fall:
- Delay procurement
- Reduce inventory levels
- Offer discounts to clear stock

### 📊 Strategic Actions:
- Dynamic pricing
- Supplier negotiation
- Demand forecasting alignment

---

## 📊 Measuring Effectiveness of Actions

To evaluate the effectiveness of implemented strategies:

### Key Performance Indicators (KPIs):
- Profit margins
- Inventory turnover ratio
- Revenue growth
- Forecast accuracy (MAPE)

### Approach:
- Compare **predicted vs actual outcomes**
- Perform **A/B testing**
- Measure ROI after strategy implementation

---

## 🚀 Model Deployment using Django

### Steps:
1. Serialize the trained model (using pickle)
2. Create Django API endpoint
3. Load model inside Django view
4. Return predictions as JSON response

### Example Workflow:
- User sends request → Django API → Model → Prediction → Response

---

## ⚡ Django + FastAPI Integration

### Architecture:
- **Django**: Handles authentication, user management, business logic
- **FastAPI**: Handles model inference (high-performance API)

### Workflow:
1. Django sends request to FastAPI
2. FastAPI processes prediction
3. Returns forecast results
4. Django serves response to frontend

---

## 🌐 Frontend Integration (Next.js & React Native)

### API Integration:
- Use REST APIs to fetch predictions

### Example:
```javascript
fetch("http://api-url/predict")
  .then(res => res.json())
  .then(data => console.log(data));


### Use Cases:
- Dashboard for price trends
- Mobile app for real-time predictions
- Alerts for price fluctuations

### Model Monitoring in Production
## Monitoring Metrics:
- Prediction accuracy (MAE, MAPE)
- Data drift
- Model drift

## Handling Model Drift:
- Detect changes in data distribution
- Trigger retraining when performance drops

## Retraining Strategy:
- Periodic retraining (monthly/quarterly)
- Automated pipelines for model updates

## Tools:
- MLflow (experiment tracking)
- Prometheus & Grafana (monitoring dashboards)
- Logging systems

### Conclusion:
- Prophet outperformed SARIMAX and SVM with the lowest MAE
- The model effectively captures seasonality and trend patterns
- Deployment-ready architecture ensures scalability
- Continuous monitoring ensures long-term reliability

### Future Improvements:
- Incorporate external factors (weather, demand, inflation)
- Use deep learning models (LSTM)
- Improve feature engineering
- Hyperparameter tuning