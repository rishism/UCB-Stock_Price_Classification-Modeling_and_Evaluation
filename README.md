### Technology Stock Price Classification Using Quarterly Financial Indicators

# Capstone Project  
**Optimizing Quarterly Capital Allocation for Top Technology Companies**

---

## **Research Question**  
How do quarterly financial indicators — such as gross margin, revenue growth, ROA, ROE, debt-to-equity ratio, current ratio, quick ratio, and PE ratio — relate to the stock price performance of 20 leading technology companies, and can we classify stock price levels using these factors?

---

## **Data Source**  
Quarterly income statements, balance sheets, and historical stock prices for 20 technology companies (AAPL, MSFT, AMZN, GOOGL, NVDA, META, AMD, TSLA, NFLX, ADBE, CRM, SHOP, ZS, NOW, HOOD, DDOG, CRWD, PLTR, PANW, FSLR), sourced via the Yahoo Finance API (`yfinance`). The dataset comprises 116 quarterly observations across 12 base financial features, expanded to 28 features through engineering.

---

## **Techniques**  
- Exploratory Data Analysis (EDA) to understand distributions, correlations, and relationships between financial metrics and stock price.  
- Feature engineering including lagged values, rolling statistics, quarter-over-quarter and year-over-year changes, derived ratios, interaction features, and seasonality encodings.  
- Six supervised classification models — Random Forest, Gradient Boosting, XGBoost, SVM, KNN, and Logistic Regression — each with hyperparameter tuning via GridSearchCV and 5-fold cross-validation.  
- Model comparison and evaluation using accuracy, precision, recall, F1-score, and ROC AUC.  
- Feature importance analysis to identify which financial indicators most influence stock price classification.

---

## **Expected Results**  
Identification of the financial indicators most strongly correlated with stock price, along with a best-performing classification model (evaluated across multiple metrics) that categorizes quarterly stock prices into "low," "medium," and "high" tiers to inform capital allocation decisions.

---

## **Why This Question Is Important**  
As a long-term technology sector investor, understanding which financial fundamentals drive stock price performance enables more disciplined, data-driven decisions about when to reallocate capital within the sector — moving beyond intuition toward evidence-based portfolio management.

---

## **Model Outcomes or Predictions**  
- **Type of Learning**: Supervised learning (classification).  
- **Expected Output**:  
  - **Classification**: Predict the target category of stock performance ("low," "medium," "high") based on quarterly financial metrics.  
- **Algorithms Evaluated**: Random Forest, Gradient Boosting, XGBoost, SVM, KNN, and Logistic Regression (6 models total). XGBoost was selected as the best-performing model.  

---

## **Data Acquisition**  
**Data Source**:  
- **Yahoo Finance (via yfinance)**: Used to acquire historical stock prices, quarterly income statements, and balance sheets for 20 technology companies. Financial metrics extracted include revenue growth, gross margin, ROA, ROE, debt-to-equity, current ratio, quick ratio, and PE ratio (computed from earnings per share and stock price).  

**Data Visualization**:  
- Histograms, correlation matrices, and bar plots were used to explore data distributions and identify relationships between features and stock price categories.  
- Feature importance and model comparison charts helped evaluate predictive variables and algorithm performance.  

---

## **Data Preprocessing/Preparation**  
### **Steps Taken**  
1. **Handling Missing Values**:  
   - Imputed missing financial metrics using forward fill, backward fill, and median imputation.  
   - Replaced missing lagged values with rolling averages to maintain trend consistency.  

2. **Feature Engineering**:  
   - Created lagged features for stock prices and revenue growth (e.g., `revenue_growth_lag_1`), grouped by ticker to prevent cross-company data leakage.  
   - Generated rolling averages and standard deviations for volatility tracking, computed per ticker.  
   - Computed quarter-over-quarter and year-over-year changes in financial performance, grouped by ticker.  
   - Derived interaction features (e.g., `roa_roe_interaction`) and additional ratios (e.g., `liquidity_ratio`, `PE Ratio`).  

3. **Encoding**:  
   - Encoded categorical variables such as `Ticker` using label encoding.  
   - Introduced a numerical `quarter` feature to capture seasonal trends.  

4. **Target Variable**:  
   - Binned continuous stock prices into three categories ("low," "medium," "high") using defined thresholds for classification.  

5. **Train-Test Split**:  
   - Split the data into training (80%) and test (20%) sets with a fixed random state for reproducibility.  

---

## **Modeling**  
### **Machine Learning Algorithms**  
1. **XGBoost**: Selected as the best-performing model based on accuracy and cross-validation scores.  
2. **Random Forest**: Used for comparison and feature importance analysis.  
3. **Gradient Boosting**: Explored as an alternative ensemble method.  
4. **SVM**: Evaluated with linear, RBF, and polynomial kernels (with probability calibration enabled).  
5. **KNN**: Tested with varying neighbor counts and distance metrics.  
6. **Logistic Regression**: Evaluated as a linear baseline with regularization tuning.  

All models used a pipeline with custom preprocessing, standard scaling, and hyperparameter tuning via GridSearchCV with 5-fold cross-validation.  

### **Feature Selection**  
- Key features included stock prices, financial ratios (e.g., gross margin, ROA, PE ratio), and engineered features like `stock_price_yoy` and rolling statistics.  

---

## **Model Evaluation**  
### **Metrics**  
1. **Accuracy**: Overall correctness of predictions across all categories.  
2. **Precision**: How often a predicted category was correct.  
3. **Recall**: How well the model captured each true category.  
4. **F1-Score**: Harmonic mean of precision and recall for balanced evaluation.  
5. **ROC AUC**: Weighted one-vs-rest area under the ROC curve, measuring each model's ability to distinguish between classes with probability estimates.  

All six models were compared using bar plots, grouped metric charts, a performance heatmap, and ROC AUC comparison.  

### **Findings**  
- XGBoost consistently outperformed other models in classification accuracy and F1-score.  
- Feature engineering significantly improved model performance, with lagged and rolling features playing a critical role.  
- Feature importance analysis (XGBoost and Random Forest) revealed the top predictive features driving stock price classification.  
- The best XGBoost model was saved using `joblib` for future use.  

---

## **Future Work**  
1. **Regression Modeling**:  
   - With a larger dataset, explore regression to predict actual stock price movements or returns.  
2. **Backtesting**:  
   - Simulate portfolio allocation strategies using model predictions and evaluate with metrics like Sharpe Ratio and Maximum Drawdown.  
3. **Data Augmentation**:  
   - Incorporate sentiment analysis from social media/news and macroeconomic indicators (interest rates, GDP) to enhance predictions.  
4. **Model Deployment**:  
   - Develop a user-friendly interface for real-time portfolio suggestions based on user-provided holdings.  
5. **Model Enhancement**:  
   - Explore neural network architectures to further improve performance and scalability.  

---

## **Outline of Project**  
1. **Data Preparation**:  
   - Collected, cleaned, and engineered data features for modeling.  
2. **Model Selection**:  
   - Evaluated six machine learning algorithms with hyperparameter tuning.  
3. **Model Export**:  
   - Saved the best-performing XGBoost model for future integration.  

---

## **Contact and Further Information**  
**Email**: 21.rishi@gmail.com  