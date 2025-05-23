# 📈 Predictive Modeling of UAE Banking Stocks Using Machine Learning

---

## 📘 Overview

The UAE banking industry plays a pivotal role in the nation's financial ecosystem. This project presents a comprehensive data-driven approach to analyzing and forecasting stock prices for four of the UAE's leading banks:

- Emirates NBD (ENBD)  
- Dubai Islamic Bank (DIB)  
- First Abu Dhabi Bank (FAB)  
- Abu Dhabi Commercial Bank (ADCB)

By integrating historical stock prices with macroeconomic indicators and applying machine learning techniques, particularly Random Forest algorithms, this project aims to generate accurate, actionable forecasts and uncover key market patterns.

---

## 📊 Data Collection and Integration

To build a reliable model, we sourced both micro and macro-level data:

1. **Bank-Specific Stock Data:**
   - Historical daily stock prices for each bank.
   - Datasets were standardized and labeled by bank name.

2. **Macroeconomic Indicators:**
   - DFM Index, Brent Oil Prices (converted to AED), USD-AED exchange rate, and GDP figures.
   - These were merged with stock data to capture broader economic influences.

---

## 🧼 Data Preprocessing and Feature Engineering

### Key Processing Steps:

- **Stock Data Consolidation:**
  - Merged datasets from all four banks into one master dataframe.
  - Added a `Bank Name` column for segmentation.

- **Missing Value Handling:**
  - Trading volumes and macroeconomic indicators were cleaned and forward-filled.

- **Feature Engineering:**
  - **Lag Variables:** `Price Lag 1`, `Change % Lag 1`
  - **Moving Averages:** 5-day and 10-day average prices
  - **Interaction Features:** `Price per Volume`

- **Integration of External Data:**
  - Merged macroeconomic indicators daily.
  - GDP was resampled and forward/backward filled for daily granularity.

- **Normalization:**
  - Used MinMaxScaler for scaling numerical features before modeling.

**✅ Output:** Cleaned and enriched dataset saved as `enhanced_stock_data.csv`

---

## 🤖 Modeling Approach: Random Forest for Stock Price Forecasting

### Workflow:

1. **Label Encoding:**
   - Converted categorical bank names to integers.

2. **Feature Selection:**
   - Chose engineered features and macroeconomic variables for training.

3. **Training Strategy:**
   - Separate models trained for each bank using an 80/20 time-based split.
   - Produced:
     - **30-Day Daily Forecasts**
     - **24-Month Monthly Forecasts**

4. **Post-Processing:**
   - Scaled predictions reverted to original values using inverse transforms.
   - Recalibrated forecasts to match latest actual prices.

5. **Prediction Merging:**
   - Combined actuals and forecasts in `combined_forecasts.csv` for analysis.

---

## 📌 Key Insights

### 1. 📉 Stock Price Trends
- **ENBD** displayed stable long-term growth post-2020.
- **FAB** peaked in 2022 at AED 19.58 but declined sharply in 2023–24.
- **ADCB** and **DIB** maintained modest, stable growth.

📊 *Visuals:* Yearly and Monthly Trends

---

### 2. 📈 Trading Volume Analysis
- **DIB** showed exceptionally high volumes (~17M/day in 2021).
- **FAB** had the second-highest trading activity.
- **ENBD** and **ADCB** showed moderate trading patterns.

📊 *Visuals:* Scatter plots and bar charts highlight volume spikes post-pandemic.

---

### 3. 🧮 Moving Average Trends
- 5-day and 10-day moving averages indicate consistent pre-2021 growth.
- Post-2021 patterns show stabilization across the sector.

📊 *Visuals:* Overlay of MA5 and MA10 from 2016–2024.

---

### 4. 🌍 Macroeconomic Influences
- Strong positive correlation observed between the **DFM Index** and **Brent Oil Prices**.
- Economic recovery in 2022 mirrored in both indices.

📊 *Visuals:* Bar chart comparing DFM Index vs. Oil Prices

---

### 5. 🧾 Price Change Analysis
- **ENBD** had notable price surges during recovery periods.
- **FAB** was highly volatile with steep corrections post-2022.
- **ADCB** and **DIB** were more stable, preferred by low-risk investors.

📊 *Visuals:* Heatmap of annual price variations by bank

---

### 6. 🔍 Actual vs Predicted Prices
- Daily forecasts aligned closely with real data.
- Monthly predictions were less reliable post-2024 for some banks (e.g., ENBD).

📊 *Visuals:* Side-by-side comparisons and residual error bars

---

## ⚠️ Challenges and Future Directions

1. **Data Gaps:** Aligning external economic indicators with daily stock data was complex.
2. **Forecast Accuracy:** Monthly models require tuning to handle volatility.
3. **Enhancements:** Incorporating financial news or sentiment analysis may boost performance.

---

## ✅ Conclusion

This project demonstrates how machine learning can enhance financial forecasting within the UAE banking sector. By synthesizing market indicators and company performance data, we developed robust, data-driven insights that are valuable for investors, analysts, and policy makers.

---

## 📂 Repository Structure

```bash
├── data/                      # Raw and processed data files
├── notebooks/                # Jupyter Notebooks for EDA and modeling
├── models/                   # Trained model files and forecasts
├── Visualizations/           # Graphs and plots used in analysis
├── scripts/                  # Python scripts for preprocessing and training
├── enhanced_stock_data.csv   # Final modeling dataset
├── combined_forecasts.csv    # Final predictions dataset
└── README.md                 # Project overview and documentation
