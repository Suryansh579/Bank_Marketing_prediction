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
The exploratory data analysis (EDA) conducted on the dataset provided meaningful insights into data quality, feature distributions, and relationships relevant for predictive modeling. Key findings are summarized below:


### ✅ Data Quality and Structure

- **No Missing Values**: The dataset contains no null or missing entries.
- **No Constant Features**: All features have more than one unique value, contributing meaningful variance.
- **Feature Types**:
  - 9 **categorical features**
  - 7 **numerical features** (all continuous)



### 🔠 Categorical Feature Insights

- **High Cardinality**:
  - `job` and `month` have the highest number of unique categories.

- **Distribution Observations**:
  - **Job**: Most clients work in `'management'`, while `'housemaid'` is least common.
  - **Marital Status**: The majority of clients are `'married'`.
  - **Education**: Most clients have a `'secondary'` education background.
  - **Default**: Dominated by `'no'`; limited variance, may be dropped.

- **Time-Based Trends**:
  - **Month of Contact**: May has the most records but the **lowest deposit interest rate**, while December has the fewest records.
  - **Interest by Month**: Higher interest rates are observed in March, September, October, and December.

- **Previous Campaign Outcome (`poutcome`)**:
  - Clients with a `'success'` outcome in the previous campaign are more likely to subscribe again.

- **Loan Insight**:
  - Clients with **housing loans** show lower interest in deposits.

- **Job Type**:
  - **Retired clients** show the highest interest in subscribing to deposits.



### 📈 Numerical Feature Insights

- **Distributions**:
  - `age` and `day` are approximately **normally distributed**.
  - `balance`, `duration`, `campaign`, `pdays`, and `previous` are **left-skewed** and contain **outliers**.

- **Client Engagement**:
  - Clients with longer **call durations** are more likely to subscribe to a term deposit.

- **Outliers**:
  - Detected in `age`, `balance`, `duration`, `campaign`, `pdays`, and `previous` using boxplots.

- **Correlation**:
  - No strong multicollinearity detected; numerical features provide unique insights.



### ⚖️ Class Balance Check

- The **target variable (`deposit`)** is balanced across both classes (`yes`, `no`), allowing for fair model training and evaluation.



### 🧠 Summary

EDA revealed critical behavioral patterns, key predictors like `duration`, and time-based trends that directly influence client decision-making. These insights were essential for guiding feature selection, model development, and strategic recommendations for future marketing campaigns.


## Feature Engineering

Feature engineering is the process of transforming raw data into meaningful features that improve the performance of machine learning models. It involves creating, modifying, selecting, or combining features (columns in a dataset) to help the algorithm better understand patterns in the data.

- **Key Steps in Feature Engineering**
  - Handling missing values (e.g., imputation)

  - Encoding categorical variables (e.g., label encoding, one-hot encoding)

  - Creating new features (e.g., extracting year from a date)

  - Scaling or normalizing numerical values

  - Removing irrelevant or redundant features

  - Binning or discretization of continuous variables

  - Log transformation / Box-Cox for skewed features

## Modelling Approach
This project follows a structured and performance-focused machine learning pipeline to predict whether a customer will subscribe to a term deposit, using two powerful ensemble models: Random Forest Classifier and XGBoost Classifier.

#### 1. Baseline Model Evaluation :
To compare the effectiveness of the models, both classifiers were initially trained and evaluated using 5-fold cross-validation on the training dataset. This approach ensures that the model’s performance is consistent across different data splits and reduces the risk of overfitting.

**Cross-Validation Results:**

| Model                    | CV Accuracy Scores                         | Mean Accuracy |
| ------------------------ | ------------------------------------------ | ------------- |
| Random Forest Classifier | `[0.8588, 0.8492, 0.8397, 0.8509, 0.8582]` | **0.8514**    |
| XGBoost Classifier       | `[0.8566, 0.8576, 0.8531, 0.8565, 0.8615]` | **0.8571**    |


#### 2. Hyperparameter Tuning with Grid Search :
To further improve the model performance, a Grid Search Cross-Validation technique was applied to both models. This method exhaustively tests combinations of hyperparameters to identify the best-performing configuration for each classifier.

   **Parameter Grids Used :**
   
   Random Forest
{
    'n_estimators': [10, 50, 100, 130],
    'criterion': ['gini', 'entropy'],
    'max_depth': range(2, 4, 1),
    'max_features': ['auto', 'log2']
}

 XGBoost
{
    'learning_rate': [0.5, 0.1, 0.01, 0.001],
    'max_depth': [3, 5, 10, 20],
    'n_estimators': [10, 50, 100, 200]
}

#### 3. Model Selection Strategy

After evaluating both models on:

 - Cross-validation accuracy

 - Model stability

 - Tuning results

The XGBoost Classifier was selected as the final model due to its:

 - Superior cross-validation accuracy

 - Efficiency with large and imbalanced datasets

 - Ability to control overfitting through regularization



#### Final Remark
This project demonstrates a methodical machine learning approach using ensemble learning models. After baseline evaluation and rigorous hyperparameter tuning via GridSearchCV, the following results were obtained:
| Model                    | Best CV Accuracy | Best Parameters                                                       |
| ------------------------ | ---------------- | --------------------------------------------------------------------- |
| Random Forest Classifier | **0.7433**       | `criterion='gini', max_depth=3, max_features='log2', n_estimators=10` |
| XGBoost Classifier       | **0.8151**       | `learning_rate=0.1, max_depth=10, n_estimators=100`                   |

Final Model Selected: XGBClassifier
  Reason for Selection:

   - Higher accuracy and better generalization

   - More flexibility in tuning (e.g., learning rate, depth)

   - Regularization and boosting make it robust to overfitting

This makes XGBoost the optimal model for predicting client interest in term deposit subscriptions and driving strategic marketing decisions.

## Feature Importance and Buisness Value

## Results


## Recommendation For Market strategy
