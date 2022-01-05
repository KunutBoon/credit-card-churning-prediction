# credit-card-churning-prediction
This project demonstrates my working approaches on developing predictive ML model to classify credit card user who may churn using their purchasing behavior on credit card, saving balance, along with other provided data.

#### -- Project Status: [Completed]

The complete code used in this project can be download via provided <a id="raw-url" href="https://raw.githubusercontent.com/KunutBoon/credit-card-churning-prediction/main/Jupyter%20Notebook/Credit%20Card%20Churning%20Prediction.ipynb">link</a> here, or you could download the Jupyter Notebook provided in the folder.

## Table of Contents
- [Project Description](#1)
- [Tooling](#2)
- [Business Problem](#3)
- [Data Description](#4)
- [Approaching to the solution](#5)
- [Model Performance](#6)
- [Insights](#7)
- [Conclusion](#8)
- [Project File Structure](#9)
- [Contact](#10)

<a name='1'></a>
## Project Description
The purpose of this project is to **illustrate my understanding in Data Science along with my traditional working approaches for developing the predictive ML model** following the Data Science process. The problem definition of this project is related to Credit Card Churning, where predictive ML models are built to predict the customer who might stop using credit card for the next consecutive periods. Data provided for this project is in transactional format, which required full process of developing ML model starting from Data Integration to Model Development. Therefore, this project is able to shows my strong understanding and my skills on developing ML model.

<a name='2'></a>
## Technologies
- Python
- Jupyter Notebook
- Scipy
- Matplotlib
- Pandas
- Scikit Learn 

<a name='3'></a>
## Business Problem
Credit Card Churning is customer behavior which defined by inactivity of all credit cards in each user for 3 consecutive months. This problem is typically solved by using the predictive ML models to classify credit card user who might stop using credit cards using his credit transaction, credit payment, card usage, user demographic, etc. The Credit Card Churning problen for this project, same as typical solution, is also required a Data Scientist to **build a predictive model and predict customer credit card churning signals for the next three months** given the list of customers, their demographics, financial history and miscellaneous data.

<a name='4'></a>
## Data Description
Data avaiable for this project are provided as csv files, which are describe below. For more detail on each data provided for this project together with sample of the data 

&emsp;&emsp;`df.head(10)`

please visits the "Sample Data" folder in the Git Repo

* File 1 : **y_train.csv**
  * Description : Output for selected user ids
  * Size: 494 rows

    | Field Name |  Data Type |      Description     |
    |:----------:|:----------:|:--------------------:|
    |  user_id   |     INT    |      Dummy user id   |
    |   Label    |     INT    | 0-Active, 1-Inactive |

* File 2 : **demo.csv**
  * Description : Personal information of customers
  * Size: 52762 rows

    |             Field Name           |  Data Type |                             Description                                  |
    |:---------------------------------|:-----------|:-------------------------------------------------------------------------|
    |               user_id            |     INT    |                               Dummy user id                              |
    |         account_start_date       | TIMESTAMP  |                          First account start date                        |
    |              birth_year          |     INT    |                                 Birth year                               |
    |                gender            |   STRING   |                             F-Female, M-Male                             |
    |            marital_status        |     INT    |                   1-Single, 2-Married, 3-Divorce/widow                   |
    |     family_income_segment_code   |     INT    |    Family income segment in ordinal scale (1 as lowest income segment)   |
    |  individual_income_segment_code  |     INT    |  Individual income segment in ordinal scale (1 as lowest income segment) |

* File 3 : **card_info.csv**
  * Description : Credit card information
  * Size: 60296 rows

    | Field Name |  Data Type |         Description      |
    |:-----------|:-----------|:-------------------------|
    |  user_id   |     INT    |      Dummy user id       |
    |  bill_cyc  |     INT    | Bill cycle day of month  |
    | cr_lmt_amt |     INT    | Credit limit amount      |
    |   card_no  |     INT    | Dummy cerdit card number |

* File 4 : **cc_txn.csv**
  * Description : Credit card transaction log
  * Size: 3223075 rows

    | Field Name |  Data Type |         Description      |
    |:-----------|:-----------|:-------------------------|
    |  mcc       |   STRING   |    Merchant Category     |
    | txn_dt     |  TIMESTAMP | Transaction Timestamp    |
    | user_id    |     INT    | Dummy user id            |
    |  txn_amt   |     INT    | Transaction amount       |
    |  card_no   |     INT    | Dummy cerdit card number |

* File 5 : **sa_bal.csv**
  * Description : Saving account balance aggregated by months
  * Size: 633144 rows

    | Field Name |  Data Type |          Description                         |
    |:-----------|:-----------|:---------------------------------------------|
    |  user_id   |   INT      |    Dummy user id                             |
    |  mm        |  INT       |   Month of year                              |
    | max_sa_bal |   FLOAT    | Maximum saving account balance in the month  |

* File 6 : **dtxn.csv**
  * Description : Incoming and outgoing transaction aggregated by months (explude credit card transactions)
  * Size: 490599 rows

    | Field Name |  Data Type |          Description                         |
    |:-----------|:-----------|:---------------------------------------------|
    |  user_id   |   INT      |    Dummy user id                             |
    |  mm        |  INT       |   Month of year                              |
    |  amt_in    |   FLOAT    |   Amount of money inbound                    |
    |  amt_out   |   FLOAT    |   Amount of money outbound                   |

<a name='5'></a>
## Approaching to the solution
For the ML model development, Data Scientist usally follows the Data Science process as a systematic framework to analyze, visualize, and model the huge amount of data. All of my current working approaches on this project are also follows this Data Science process to systematically develop the Ml model. Each working approach could be illustrated as follows
* **Data Understanding** : Understanding basic details of each provided data for further usage, such as its format, its size, associated data type, its meaning, etc.
* **Basic Data Assessment** : Doing the basic assessment on each data to better understanding the current snapshot of the data, such as looking at sample rows of each data, identifying data format, identifying missing values, etc.
* **Data Aggregation & Feature Engineering** : Aggregating data from various data source with the prior dataset along with develop some new features which could represent useful insights for classifying churners.
* **Exploratory Data Analysis** : Analyzing data to investigate and summarize their main characteristics before concluding any assumptions and insights found using statistical and visualization toold
  * Univariate Analysis : Analyzing each variable in order to describe all data values contained within it by determining the data distribution, calculating statistics, detecting outliers, etc.
  * Bivariate Analysis : Analyzing two variables together in order to finds some pattern and relationship between these variables by calculating pairwise correlation, visualizing data distribution seperated by category, etc.
* **Data Preprocessing** : Processing the data into the usable format for the Machine Learning model to train on. The process also refers to manipulating the raw data in the way which turns it into signals by using insights found from previous steps
* **Model Training** : Training the Machine Learning model using the data from previous step by trying to fit data with various models, tuning the hyperparameters on each model using cross-validation and random search, and selecting the model which provides highest average recall score on hold-out cross validation set.
* **Model Prediction** : Predicting the unseen data by repeating all steps involving with Data Preprocessing and then predicting the data using selected model

<a name='6'></a>
## Model Performance
Evaluation metrics validating model prediction performance on each hold-out cross validation set for each type of Machine Learning model are illustrated below
* **Logistic Regression**
  |       Accuracy     |      Precision    |       Recall      |         F1        |
  |:------------------:|:-----------------:|:-----------------:|:-----------------:|
  | 0.9942 +/- 0.0140  | 0.9887 +/- 0.0271 | 1.0000 +/- 0.0000 | 0.9943 +/- 0.0137 |
* **Linear SVC**
  |       Accuracy     |      Precision    |       Recall      |         F1        |
  |:------------------:|:-----------------:|:-----------------:|:-----------------:|
  | 1.0000 +/- 0.0000  | 1.0000 +/- 0.0000 | 1.0000 +/- 0.0000 | 1.0000 +/- 0.0000 |
* **Decision Tree Classifier**
  |       Accuracy     |      Precision    |       Recall      |         F1        |
  |:------------------:|:-----------------:|:-----------------:|:-----------------:|
  | 0.9298 +/- 0.0495  | 0.8824 +/- 0.0736 | 0.9943 +/- 0.0224 | 0.9346 +/- 0.0437 |
* **Random Forest Classifier**
  |       Accuracy     |      Precision    |       Recall      |         F1        |
  |:------------------:|:-----------------:|:-----------------:|:-----------------:|
  | 0.9942 +/- 0.0139  | 0.9944 +/- 0.0218 | 0.9941 +/- 0.0231 | 0.9942 +/- 0.0139 |
* **XGBoost Classifier**
  |       Accuracy     |      Precision    |       Recall      |         F1        |
  |:------------------:|:-----------------:|:-----------------:|:-----------------:|
  | 0.9971 +/- 0.0114  | 0.9944 +/- 0.0218 | 1.0000 +/- 0.0000 | 0.9972 +/- 0.0110 |
  
Model which provide highest recall score on hold-out cross validation sets are including Logistic Regression, Linear SVC, and XGBoost Classifier. For these models, the candidate models which provide highest scores across all metrics are inclusing Linear SVC and XGBoost Classifier, which we choose **XGBoost Classifier** as the best candidate model.

<a name='7'></a>
## Insights
* Inteperting the ML model

  ![Feature Importance](Pictures/feature_importances.png)

  From the graph, the features which have highest impact on classifying churn customer are credit transaction (`max_txn` & `total_txn`). The features which have the second highest impact are customer saving balance (`max_sa_bal` & `avg_sa_bal`). Other features which also have high impact are including individual income, family income, merchant category, transaction amount (non-credit transaction), etc.
* Insights from the data

  * Max transaction spend by each customer

  ![max_txn](Pictures/max_txn.png)

    Credit card user with maximum credit card payment amount greater than 175000 has a great chance to churn

  * Average saving balance account for each customer

  ![avg_sa_bal](Pictures/avg_sa_bal.png)

    Credit card user with average saving balance value greater than 500000 has a great chance to churn

  * Individual income segment code

  ![individual_income_segment_code](Pictures/individual_income_segment_code.png)

    Credit card user with income segment 02 and 12-15 has a higher chance to churn compared with user from other income segment

  * Least spending category

  ![individual_income_segment_code](Pictures/least_purchasing_category.png)

    Credit card user with least spending in merchant `mcc_cat11`, `mcc_cat2`, and `mcc_cat6` has a higher chance to churn

<a name='8'></a>
## Conclusion
The problem definition for this project is to predict credit card churning signals for each customer for the next 3 consecutive months, which required Data Scientist to develop the predictive Machine Learning model. To solve this problem, we use Data Science process framework starting from Data Aggregation to Model Development, and try to fit the data with various types of ML model in order to find the best candidate of those models. The **best model is XGBoost Classifier** which provides the overall highest score acorss all evaluation metrics. We also **discovered some insights from the data** by interpreting the classification behavior from the model and further analyze upon those findings.


<a name='9'></a>
## Project File Structures
The structure of project files are illustrated below
```
├── .gitattributes                                  <- File which specified file type to keep tracking version for git lfs
├── README.md                                       <- README file wich contains description of the project
├── Jupyter Notebook
│   └── Credit Card Churning Prediction.ipynb       <- Jupyter notebook file which contains all of my code for implementing ML model
├── Pictures                                        <- Folder which contains some visualization from EDA and ML model intepretation
├── Prediction Results
│   └── prediction_results.csv                      <- Prediction 
│
├── notebooks                <- Notebooks for analysis and testing
│   ├── eda                  <- Notebooks for EDA
│   │   └── example.ipynb    <- Example python notebook
│   ├── features             <- Notebooks for generating and analysing features (1 per feature)
│   ├── modelling            <- Notebooks for modelling
│   └── preprocessing        <- Notebooks for Preprocessing 
│
├── scripts                  <- Standalone scripts
│   ├── deploy               <- MLOps scripts for deployment (WIP)
│   │   └── score.py         <- Scoring script
│   ├── train                <- MLOps scripts for training
│   │   ├── submit-train.py  <- Script for submitting a training run to Azure ML Service
│   │   ├── submit-train-local.py <- Script for local training using Azure ML
│   │   └── train.py         <- Example training script using the iris dataset
│   ├── example.py           <- Example sctipt
│   └── MLOps.ipynb          <- End to end MLOps example (To be refactored into the above)
│
├── src                      <- Code for use in this project.
│   └── examplepackage       <- Example python package - place shared code in such a package
│       ├── __init__.py      <- Python package initialisation
│       ├── examplemodule.py <- Example module with functions and naming / commenting best practices
│       ├── features.py      <- Feature engineering functionality
│       ├── io.py            <- IO functionality
│       └── pipeline.py      <- Pipeline functionality
│
└── tests                    <- Test cases (named after module)
    ├── test_notebook.py     <- Example testing that Jupyter notebooks run without errors
    ├── examplepackage       <- examplepackage tests
        ├── examplemodule    <- examplemodule tests (1 file per method tested)
        ├── features         <- features tests
        ├── io               <- io tests
        └── pipeline         <- pipeline tests
```
<a name='9'></a>
