# Crypto-Trade-Data-Analysis

### Table of Contents
- [Project Overview](#project-overview)
- [Data Architecture](#data-architecture)
- [Key Insights and Visualizations](#key-insights-and-visualizations)
- [Technical Workflow](#technical-workflow)
- [Model Performance](#model-performance)
- [Trading Strategy Recommendations](#trading-startegy-recommendations)
- [Setup and How to Run](#setup-and-how-to-run)

### Project Overview
This project analyzes the intersection of Market Psychology and On-Chain Trading Behavior. By correlating the "Crypto Fear and Greed Index" with historical trade data, we identify how different trader archetypes (Whales vs. Scalpers) adjust their risk, position sizing and bias during market extremes.

### Data Architecture
The analysis merges two primary data streams:
1. Fear and Greed Index: Daily sentiment scores ranging from 0 (Extreme Fear) to 100 (Extreme Greed).
2. Historical Trade Data: 200,000+ records including PnL, Size (USD), Side (Buy/Sell), and Account IDs.

### Key Insights and Visualizations
1. Market Timing: The "Smart Money" Bias: Our analysis reveals that Long Bias actually peaks during Extreme Fear ($51.1\%$) and hits its lowest point during Extreme Greed ($44.8\%$).
2. Position Fragmentation (Size vs. Sentiment): Average trade sizes drop by over 60% during Extreme Greed ($3,112$ USD) compared to Fear ($7,816$ USD), indicating "Position Splitting" where traders enter many small FOMO positions rather than calculated large bets.
3. Segment Durability: Frequent traders maintain an 89.5% win rate during Extreme Greed, significantly outperforming infrequent traders who struggle with high-volatility reversals.

### Technical Workflow
1. Data Alignment: Standardized IST Timestamps to Date objects and merged datasets on a 1:1 daily basis.
2. Behavioral Clustering: Applied K-Means Clustering to segment traders into three archetypes:
   - The Scalper: High frequency, low size, high consistency.
   - The Opportunist: Moderate size, sentiment-dependent frequency.
   - The Whale: High-conviction, large-size positions.
3. Predictive Modeling: Developed a Random Forest Classifier to predict next-day trader profitability using current sentiment and behavioral "Long Bias" features.

### Model Performance
| Model Name          | Accuracy | Precision | Recall |
| :------------------ | :------: | :-------: | :----: |
| Logistic Regression | 58.2%    | 0.56      | 0.52   |
| Random Forest       | 61.5%    | 0.60      | 0.58   |
| **XGBoost (Best)** | **63.2%**| **0.62** | **0.61**|
