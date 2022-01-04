# credit-card-churning-prediction
This project demonstrates my working approaches on developing predictive ML model to classify credit card user who may churn using their purchasing behavior on credit card, saving balance, along with other provided data.

#### -- Project Status: [Completed]

The complete code used in this project can be download via provided <a id="raw-url" href="https://raw.githubusercontent.com/KunutBoon/credit-card-churning-prediction/main/Jupyter%20Notebook/Credit%20Card%20Churning%20Prediction.ipynb">link</a> here, or you could download the Jupyter Notebook provided in the folder.

## Table of Contents
- [Project Description](#1)
- [Tooling](#2)
- [Business Problem](#3)
- [Data Description](#4)
- [Approaches to the solution](#5)
- [Model Performance](#6)
- [Insights from Data](#7)
- [Conclusion](#8)
- [Project File Structure](#9)
- [Contributing to This Template](#10)
- [Contact](#11)
- [License](#12)

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
