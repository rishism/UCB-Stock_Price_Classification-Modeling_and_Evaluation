Problem Statement
---

Research Question
How do quarterly financial indicators — such as gross margin, revenue growth, ROA, ROE, debt-to-equity ratio, current ratio, quick ratio, and PE ratio — relate to the stock price performance
of 20 leading technology companies, and can we classify stock price levels using these factors?

Data Source
Quarterly income statements, balance sheets, and historical stock prices for 20 technology companies (AAPL, MSFT, AMZN, GOOGL, NVDA, META, AMD, TSLA, NFLX, ADBE, CRM, SHOP, ZS, NOW, HOOD,
DDOG, CRWD, PLTR, PANW, FSLR), sourced via the Yahoo Finance API (yfinance). The dataset comprises 116 quarterly observations across 12 base financial features, expanded to 28 features
through engineering.

Techniques
- Exploratory Data Analysis (EDA) to understand distributions, correlations, and relationships between financial metrics and stock price.
- Feature engineering including lagged values, rolling statistics, quarter-over-quarter and year-over-year changes, derived ratios, interaction features, and seasonality encodings.
- Six supervised classification models — Random Forest, Gradient Boosting, XGBoost, SVM, KNN, and Logistic Regression — each with hyperparameter tuning via GridSearchCV and 5-fold
cross-validation.
- Model comparison and evaluation using accuracy, precision, recall, F1-score, and ROC AUC.
- Feature importance analysis to identify which financial indicators most influence stock price classification.

Expected Results
Identification of the financial indicators most strongly correlated with stock price, along with a best-performing classification model (evaluated across multiple metrics) that categorizes
quarterly stock prices into "low," "medium," and "high" tiers to inform capital allocation decisions.

Why This Question Is Important
As a long-term technology sector investor, understanding which financial fundamentals drive stock price performance enables more disciplined, data-driven decisions about when to reallocate
capital within the sector — moving beyond intuition toward evidence-based portfolio management.
