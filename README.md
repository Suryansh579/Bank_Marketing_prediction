# Problem Statement 
The project focuses on analyzing and predicting the success of term deposit subscriptions from a bank's past marketing campaign data. The objective is two-fold:
- To build predictive models that forecast customer responses
- And more importantly, to extract insights that can help the bank improve the effectiveness of future marketing campaigns.
## Dataset Discription
The dataset, sourced from the UCI Machine Learning Repository, contains information of client contacted. It includes personal data (like age, job, marital status), past interactions (campaign outcome, number of contacts), and external factors.
### Dataset overview
- Total records: 45,000
- Target variable: response (yes or no – indicating if the client subscribed to a term deposit)
- Attributes: 17 input features + 1 output label
### Feature Summary
| Feature     | Description                                                         |
| ----------- | ------------------------------------------------------------------- |
| `age`       | Client’s age (numeric)                                              |
| `job`       | Type of job (e.g., admin., technician, entrepreneur, etc.)          |
| `marital`   | Marital status (e.g., married, single, divorced)                    |
| `education` | Education level (e.g., primary, secondary, tertiary, unknown)       |
| `default`   | Has credit in default? (yes/no)                                     |
| `balance`   | Average yearly balance in euros                                     |
| `housing`   | Has housing loan? (yes/no)                                          |
| `loan`      | Has personal loan? (yes/no)                                         |
| `contact`   | Contact communication type (cellular or telephone)                  |
| `day`       | Last contact day of the month                                       |
| `month`     | Last contact month of the year                                      |
| `duration`  | Duration of the last contact in seconds                             |
| `campaign`  | Number of contacts performed during this campaign                   |
| `pdays`     | Days since the client was last contacted in a previous campaign     |
| `previous`  | Number of contacts performed before this campaign                   |
| `poutcome`  | Outcome of the previous marketing campaign (e.g., success, failure) |
| `response`  | **Target variable** – client subscribed to a term deposit (yes/no)  |
## Exploratory Data Analysis (EDA)
#### What is EDA ?
Exploratory Data Analysis (EDA) is a critical step in the data science workflow where we deeply examine the dataset using statistics and visualizations to:
Understand the structure and distribution of data.
Detect outliers, anomalies, and missing values.
Identify patterns and relationships between features.
Inform feature selection, data cleaning, and modeling strategies.
EDA allows data scientists to make informed, data-driven decisions rather than guessing or assuming.

#### Why is it one of the most important step
EDA is not just a preliminary step — it’s the foundation of every successful data science project. Without understanding the data, modeling becomes a blind process.
In this project, EDA was essential to understanding the marketing behavior of clients and identifying key features that influence whether they subscribe to a term deposit.

**1. Addressing Class Imbalance :**
Using value counts and pie charts, we observed a significant imbalance
Only 11% of the customers responded with “yes”
This insight led us to Use evaluation metrics beyond just accuracy (like F1-score, ROC-AUC).
Consider sampling techniques during model training.

**2. Discovering Key Influential Features :**
Through violin plots, boxplots, and correlation heatmaps, we found that
Duration of contact strongly correlates with positive response.
Clients contacted via cellular had a much higher subscription rate than those via telephone.
Month, education, and previous campaign outcomes significantly impact the likelihood of success.

**3. Improving Data Quality :**
The pdays feature showed a high frequency of the value 999, indicating that many clients were never contacted before. This insight helped
Engineer better features (e.g., binary flag for "contacted before").
Prevent misleading model behavior due to outlier values.

**4. Visualizing Relationships :**
Used heatmaps to analyze correlations among numerical variables.
Applied violin plots and joint plots to explore relationships between categorical and numerical variables with the target variable (response).

Exploratory Data Analysis Tasks include :-

- Finding unwanted column
- Finding missing values
- Finding feature with one value
- Explore the categorical features
- Finding categorical feature distribution
- Relationship between categorical feature with label
- Explore the numerical feature
- Finding the discrete numerical features
- Relation between discrete numerical feature and label
- Finding the continous features
- Distribution of continous numerical feature and label
- Finding outliers in numerical features
- Explore the correlatin between numerical feature
- Finding the pair plot
- Checking the data set is balanced or not based on target values in classification


## Insights



## Feature Engineering


## Modelling Approach


## Feature Importance and Buisness Value

## Results


## Recommendation For Market strategy
