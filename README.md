# Problem Statement 
The project focuses on analyzing and predicting the success of term deposit subscriptions from a bank's past marketing campaign data. The objective is two-fold:
- To build predictive models that forecast customer responses
- And more importantly, to extract insights that can help the bank improve the effectiveness of future marketing campaigns.
## Dataset Discription
The dataset, sourced from the UCI Machine Learning Repository, contains information of client contacted. It includes personal data (like age, job, marital status), past interactions (campaign outcome, number of contacts), and external factors.
### Dataset overview
- Total records: ~45,000
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
