# Part B: Business Case Analysis

## B1. Problem Formulation

### (a) ML Problem
- **Target:** items_sold  
- **Features:** store_size, location_type, promotion_type, month, year, is_weekend, is_festival, competition_density, footfall  
- **Type:** Supervised Regression  
- **Why:** Predicts a continuous value (sales volume)


### (b) Why Items Sold > Revenue
- Revenue affected by price/discounts → misleading  
- Items sold reflects true demand  
- **Principle:** Target should align directly with business goal and avoid bias


### (c) Better Modelling Strategy
- Segment models (urban/rural) OR clustering OR hierarchical model  
- **Reason:** Stores behave differently → improves accuracy  



## B2. Data & EDA

### (a) Data Joining
- Join tables using:
  - store_id, date, promotion_id  
- **Final dataset:** 1 row = 1 store per month  

**Aggregations:**
- items_sold → sum  
- footfall → sum/avg  
- promotion_type → mode  
- festivals/weekends → count  


### (b) EDA
1. Sales by promotion (bar chart) → best promotion  
2. Time series → seasonality  
3. Boxplot (location vs sales) → store differences  
4. Scatter (competition vs sales) → impact of competition  
5. Correlation heatmap → feature relationships  

**Use:** Feature engineering + model selection  


### (c) Imbalance Issue
- 80% no promotion → model bias  

**Fix:**
- Oversampling  
- Stratified sampling  
- Class weights  



## B3. Evaluation & Deployment

### (a) Train-Test Split
- Use **time-based split** (not random)  
- Train: first 2–2.5 yrs  
- Test: last months  

**Why not random?**
- Causes data leakage  

**Metrics:**
- MAE → avg error  
- RMSE → penalizes large errors  
- R² → model fit  



### (b) Explaining Recommendations
- Use feature importance / SHAP  

**Example:**
- December → festivals → Loyalty Bonus  
- March → low demand → Discount  

**Explain:** Different conditions → different promotions  


### (c) Deployment
1. Save model (joblib/pickle)  
2. Prepare monthly data (same preprocessing)  
3. Predict for all promotions → choose best  

**Monitoring:**
- MAE over time  
- Data drift  
- Concept drift  

**Retraining:**
- Every 3–6 months or when performance drops  


# Summary
- Regression problem  
- Use items sold (not revenue)  
- Segment models  
- Time-based validation  
- Continuous monitoring  

Raw Data - Preprocessing - Model - Predictions - Recommendations - Monitoring - Retraining