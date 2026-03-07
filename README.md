# Crypto-Trade-Data-Analysis

### Table of Contents
- [Project Overview](#project-overview)
- [Data Architecture](#data-architecture)
- [Key Insights and Visualizations](#key-insights-and-visualizations)
- [Technical Stack](#technical-stack)
- [Technical Workflow](#technical-workflow)
- [Model Performance](#model-performance)
- [Trading Strategy Recommendations](#trading-startegy-recommendations)
- [Setup and How to Run](#setup-and-how-to-run)
- [References](#references)

### Project Overview
This project analyzes the intersection of Market Psychology and On-Chain Trading Behavior. By correlating the "Crypto Fear and Greed Index" with historical trade data, we identify how different trader archetypes (Whales vs. Scalpers) adjust their risk, position sizing and bias during market extremes.

### Data Architecture
The analysis merges two primary data streams:
1. Fear and Greed Index: Daily sentiment scores ranging from 0 (Extreme Fear) to 100 (Extreme Greed).
2. Historical Trade Data: 200,000+ records including PnL, Size (USD), Side (Buy/Sell), and Account IDs.

### Key Insights and Visualizations
1. Market Timing: The "Smart Money" Bias- Our analysis reveals that Long Bias actually peaks during Extreme Fear ($51.1\%$) and hits its lowest point during Extreme Greed ($44.8\%$).
2. Position Fragmentation (Size vs. Sentiment): Average trade sizes drop by over 60% during Extreme Greed ($3,112$ USD) compared to Fear ($7,816$ USD), indicating "Position Splitting" where traders enter many small FOMO positions rather than calculated large bets.
3. Segment Durability: Frequent traders maintain an 89.5% win rate during Extreme Greed, significantly outperforming infrequent traders who struggle with high-volatility reversals.

### Technical Stack
1. Data: Pandas, Numpy
2. Analysis: Matplotlib, Seaborn
3. Machine Learning: Scikit Learn (K-Means Clustering, Random Forest)

### Technical Workflow
1. Data Alignment: Standardized IST Timestamps to Date objects and merged datasets on a 1:1 daily basis.
2. Behavioral Clustering: Applied K-Means Clustering to segment traders into three archetypes:
   - The Scalper: High frequency, low size, high consistency.
   - The Opportunist: Moderate size, sentiment-dependent frequency.
   - The Whale: High-conviction, large-size positions.
3. Predictive Modeling: Developed a Random Forest Classifier to predict next-day trader profitability using current sentiment and behavioral "Long Bias" features.

### Model Performance
I used a Random Forest Classifier to predict next-day profitability based on today's market sentiment and trading bias. The model achieved a strong recall, indicating it is particularly good at identifying potential winning days.

| Model Name          | Accuracy | Precision | Recall |
| :------------------ | :------: | :-------: | :----: |
| **Random Forest** | **61.8%**| **0.65** | **0.79** |

### Trading Startegy Recommendations
1. The Contra-Fear Rule: During "Extreme Fear," increase position size by 1.5x for high-conviction accounts, as this period shows the highest long-term accumulation bias.
2. The Greed Scalp Rule: In "Extreme Greed" phases, pivot to high-frequency, small-size "scalping" to capture micro-trends while minimizing exposure to sharp market corrections.

### Setup and How to Run
1. Installation
Clone the repository and install dependencies:
```bash
git clone [https://github.com/your-username/trader-analysis.git](https://github.com/your-username/trader-analysis.git)
pip install pandas numpy matplotlib seaborn scikit-learn
```
2. Run the analysis
Place historical_data.csv and fear_greed_index.csv in the root folder and run:
```bash
python main_analysis.py
```

### References
- Sentiment Data: Alternative.me Crypto Fear & Greed API.
- Tools: Scikit-Learn (Modeling)
