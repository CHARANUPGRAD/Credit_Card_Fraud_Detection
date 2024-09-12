
### **Problem Statement:-**

In the banking industry, detecting credit card fraud using machine learning is not just a trend; it is a necessity for the banks, as they need to put proactive monitoring and fraud prevention mechanisms in place. Machine learning helps these institutions reduce time-consuming manual reviews, costly chargebacks and fees, and denial of legitimate transactions.

### **Business Objective:**

Suppose you are part of the analytics team working on a fraud detection model and its cost-benefit analysis. You need to develop a machine learning model to detect fraudulent transactions based on the historical transactional data of customers with a pool of merchants.
Based on your understanding of the model, you have to analyse the business impact of these fraudulent transactions and recommend the optimal ways that the bank can adopt to mitigate the fraud risks.
### **Our Objective**

we will analyse the business impact of these fraudulent transactions and recommend the optimal ways that the bank can adopt to mitigate the fraud risks.

# **Approach of the process:**
**1. Reading and Understanding the Data**

Loaded the dataset: fraudTrain.csv and fraudTest.csv (1.85 million rows and 23 columns in total).

Checked the shape, column names, and data types.
Performed exploratory checks on null values and duplicated rows.

Concatenated both datasets into a single fraud_data dataset for easier analysis.

**2. Cleaning the Data**

Checked for null values (none found).
Dropped unnecessary columns such as 'Unnamed: 0', 'first', 'last', 'street'.
Converted date columns ('trans_date_trans_time', 'dob') into appropriate datetime formats.

Created new columns such as 'trans_Date' and 'trans_Time' for easier manipulation.

Binned job titles into categories for a cleaner analysis (e.g., combining different types of engineers into one group).

**3. Visualization of Data**

**Univariate Analysis:** Analyzed individual features like amt, job, and merchant.

**Multivariate Analysis:**

**Numerical Variables:** Plotted correlation heatmaps to understand relationships.

**Categorical Variables:** Visualized fraud transaction rates across various categories (jobs, states, merchant types).

**Created visualizations such as:**

Class Imbalance (Fraud vs. Non-Fraud).
Transaction amount distribution.
Fraud rate across different merchant categories.

**4. Data Preparation**

Feature Engineering: Derived new features such as:
Transaction year, month, hour, and weekday.
Distance between merchants.

Amount spent by customers over different time intervals (30 days, 24 hours).

**Exploratory Analysis:**

Explored insights such as fraud distribution by age group, city, state, and merchant type.
Plotted KDE and time distribution plots to visualize fraud transactions.

**5. Data Preparation for Modeling**
Checked for multicollinearity and dropped features with high correlation.
Created dummy variables for categorical data and label-encoded other columns.
Split the dataset into training and testing sets (X and y).
Handled class imbalance using techniques like SMOTE and ADASYN.

**6. Modeling**

**`Model 1:`** Decision Tree:
Default parameters using SMOTE and ADASYN.
Tuned model with optimized hyperparameters.

**`Model 2:`** Random Forest:

Trained with both default and tuned models using SMOTE and ADASYN.

**`Model 3: XGBoost:`**

Applied XGBoost with default and hyper-tuned parameters.
Achieved best performance with tuned XGBoost model (highest recall).

**7. Cost-Benefit Analysis**

**`Part 1:`** Before model deployment:
Estimated the average loss per fraudulent transaction and monthly fraud cost.

**`Part 2:`** After model deployment:
Calculated the reduction in fraudulent transactions and projected savings.

**8. Recommendations**

Sent SMS alerts for transactions that exceed average spending in the last 24 hours.

Increased vigilance during high-fraud periods (weekdays and weekends).
Focused fraud prevention efforts on categories with higher fraud rates, such as shopping, grocery, and transport.

**Cost Benefit Analysis(Part 2)**
                      Questions                                                                          Answer
1. Cost incurred per month before the model was deployed (2*3 of part1)----------------------------------213292.49
2. Average number of transactions per month detected as fraudulent by the model (TF)---------------------393.67
3. Cost of providing customer executive support per fraudulent transaction detected by the model---------1.5
4. Total cost of providing customer support per month for fraudulent transactions
    detected by the model(TF*$1.5) ----------------------------------------------------------------------590.51  
5. Average number of transactions per month that are fraudulent but not detected by the model (FN)-------8.46
6. Cost incurred due to fraudulent transactions left undetected by the model (FN*c)---------------------4487.35
7. Cost incurred per month after the model is built and deployed (4+6)-----------------------------------5077.86
8. Final savings = Cost incurred before - Cost incurred after(1-7)---------------------------------------208214.64

**Conclusion**
Before Cost incurred/month by the bank= $ 213292.49

Now Cost incurred/month by bank after my modelling = $ 5077.86 only

Cost saving done by Bank after model modelling = 208214.64

From above data, we can see that, cost incurred to bank for paying to customer for their loss is reduced by 97.62%.
##**Business Insights and Recommendation of strategies:**
# **1.Average Transaction Amount in Last 24 Hours (hist_trans_avg_amt_24h):**

**`Insight:`**
 The likelihood of a transaction being fraudulent increases as the average transaction amount over the last 24 hours `(hist_trans_avg_amt_24h)` rises. This value reflects the average spent in the last 24 hours.

**`Recommendation:`**
 The bank should trigger an SMS alert when a customer's spending in the last 24 hours exceeds their historical pattern, prompting them to verify unusual transactions immediately.

**2.Fraudulent Activity on Specific Days (Weekday Analysis):**

**`Insight:`**
 Fraudulent transactions tend to peak on Thursdays, Saturdays, and Mondays, according to patterns observed in the data.
Recommendation: Banks should apply stricter monitoring or heightened fraud detection alerts during these days, focusing on suspicious patterns to prevent fraud.

**3.Transaction Amount (amt):**

**`Insight:`**
Higher transaction amounts tend to correlate with an increased likelihood of fraud.

**`Recommendation:`**
If the transaction amount significantly exceeds the customer’s usual spending patterns, the bank should proactively send an alert to the customer for confirmation to reduce the risk of fraud.

**Category-Specific Fraud Risks (catg_home, catg_shopping_pos, etc.):**

**`Insight:`**
Categories such as home, shopping POS, grocery POS, health & fitness, and gas transport show higher fraud probabilities.

**`Recommendation:`**
For transactions in these categories, banks should implement real-time monitoring and send flash SMS alerts detailing transaction history, encouraging customers to confirm the legitimacy of these purchases.

**Odd Hour Transactions (Time-Based Fraud Analysis):**

**`Insight:'**
Fraudulent transactions are more likely to occur during odd hours (22:00 - 03:00).

**`Recommendation:`**
 The bank should enforce heightened fraud detection protocols during these hours and send SMS alerts for transactions that occur during this time frame to verify their legitimacy.
