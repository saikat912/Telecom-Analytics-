
# Telecom Customer Churn Analysis

## Overview

This project analyzes customer churn in the telecom industry to identify factors influencing churn and predict potential churners. By understanding these dynamics, telecom companies can develop targeted retention strategies to reduce churn and improve customer loyalty.

## Table of Contents

- [Project Description](#project-description)
- [Data Description](#data-description)
- [Dependencies](#dependencies)
- [Installation](#installation)
- [Usage](#usage)
- [Data Cleaning and Preprocessing](#data-cleaning-and-preprocessing)
- [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
- [Feature Engineering](#feature-engineering)
- [Label Encoding](#label-encoding)
- [Churn Analysis](#churn-analysis)
- [Contributing](#contributing)
- [License](#license)

## Project Description

Customer churn is a critical issue in the telecom industry. This project aims to:

-   Explore and visualize factors contributing to customer churn.
-   Develop machine learning models to predict customer churn.
-   Provide actionable insights for customer retention strategies.

## Data Description

The dataset `Telecom_Customer_Details.csv` contains 7043 entries with 21 columns, including customer demographics, service usage, and churn status. Key columns include:

-   `customerID`: Unique identifier for each customer.
-   `gender`: Customer's gender (Male, Female).
-   `SeniorCitizen`: Whether the customer is a senior citizen (1, 0).
-   `Partner`: Whether the customer has a partner (Yes, No).
-   `Dependents`: Whether the customer has dependents (Yes, No).
-   `tenure`: Number of months the customer has stayed with the company.
-   `PhoneService`: Whether the customer has phone service (Yes, No).
-   `MultipleLines`: Whether the customer has multiple lines (Yes, No, No phone service).
-   `InternetService`: Customer's internet service provider (DSL, Fiber optic, No).
-   `OnlineSecurity`: Whether the customer has online security (Yes, No, No internet service).
-   `OnlineBackup`: Whether the customer has online backup (Yes, No, No internet service).
-   `DeviceProtection`: Whether the customer has device protection (Yes, No, No internet service).
-   `TechSupport`: Whether the customer has tech support (Yes, No, No internet service).
-   `StreamingTV`: Whether the customer has streaming TV (Yes, No, No internet service).
-   `StreamingMovies`: Whether the customer has streaming movies (Yes, No, No internet service).
-   `Contract`: The contract term of the customer (Month-to-month, One year, Two year).
-   `PaperlessBilling`: Whether the customer has paperless billing (Yes, No).
-   `PaymentMethod`: The customer’s payment method (Electronic check, Mailed check, Bank transfer (automatic), Credit card (automatic)).
-   `MonthlyCharges`: The amount charged to the customer monthly.
-   `TotalCharges`: The total amount charged to the customer.
-   `Churn`: Whether the customer churned (Yes or No).

## Dependencies

-   pandas
-   numpy
-   matplotlib
-   seaborn
-   scikit-learn

Install the required dependencies using pip:

```
pip install pandas numpy matplotlib seaborn scikit-learn
```

## Installation

1.  Clone the repository:

```
git clone <repository_url>
cd telecom-churn-analysis
```

2.  Download the dataset `Telecom_Customer_Details.csv` and place it in the same directory as the scripts.

## Usage

1.  Run the main script to perform data cleaning, EDA, and churn analysis:

```
python churn_analysis.py
```

2.  Follow the notebook `telecom_churn_analysis.ipynb` for detailed steps and visualizations.

## Data Cleaning and Preprocessing

-   **Missing Values**: Handled missing values in `TotalCharges` by replacing spaces with NaN and then removing rows with NaN.
-   **Data Types**: Converted `TotalCharges` to numeric type.
-   **Removed irrelevant column**: Dropped the `customerID` column as it is not needed for analysis.

## Exploratory Data Analysis (EDA)

-   **Visualizations**:

    -   Heatmap to check for missing values.
    -   Plots to visualize the distribution of churned vs. non-churned customers.
    -   Plots to understand relationships between categorical and numerical features with churn.

## Feature Engineering

-   Identified categorical and numerical features.

## Label Encoding

-   Transformed categorical features into numerical format using Label Encoding.

    ```
    from sklearn.preprocessing import LabelEncoder
    le = LabelEncoder()
    df1 = data.copy(deep=True)
    text_data_features = [i for i in list(data.columns) if i not in list(data.describe().columns)]

    for i in text_data_features:
        df1[i] = le.fit_transform(df1[i])
    ```

## Churn Analysis

-   Compared the means of features for churned and non-churned customers using heatmaps.

    ```
    colors = ['#E94B3C', '#2D2926']
    churn = df1[df1['Churn']==1].describe().T
    not_churn = df1[df1['Churn']==0].describe().T

    fig, ax = plt.subplots(nrows=1, ncols=2, figsize=(12,12))
    plt.subplot(1,2,1)
    sns.heatmap(churn[['mean']], annot=True, cmap=colors, linewidths=0.4, linecolor= 'black', cbar=False, fmt='.2f')
    plt.title('Churned Customer')

    plt.subplot(1,2,2)
    sns.heatmap(not_churn[['mean']], annot=True, cmap=colors, linewidths=0.4, linecolor = 'black', cbar=False, fmt='.2f')
    plt.title('Not Churned Customer')

    fig.tight_layout(pad=0)
    plt.show()
    ```

## Contributing

Contributions are welcome! Please fork the repository and submit a pull request with your changes.

## License

This project is licensed under the [MIT License](LICENSE).
```

