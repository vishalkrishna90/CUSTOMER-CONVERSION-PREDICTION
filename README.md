
# Customer Conversion Preciction 

This is a **Customer Conversion Prediction** project that I found during the Guvi Hackathon, with the help of this project any **Startup Insurance Company** can predict  whether a customer will subscribe there **Insurance** or not 

[Go To The Web App](https://customer-conversion-prediction.herokuapp.com/)

![Customer Conversion Prediction](https://github.com/vishalkrishna90/CUSTOMER-CONVERSION-PREDICTION/blob/main/Images/Web_app_1.png)

**Author = Vishal Kumar Mridha**

**Domain = Insurance**

**Level = Intermediate**

**Accuracy Score = 89%>**

**Project Type = End To End Project**

![User Libraries](https://github.com/vishalkrishna90/CUSTOMER-CONVERSION-PREDICTION/blob/main/Images/li_im.jpg)


## Process Followed To Complite This Project
- Problem Statement
- Data Collection 
- Data Description
- Data Preprocessing
- Handle Outliers 
- Exploratory Data Analysis (EDA)
- Data Encoding
- Feature Selection
- Data Balancing
- Data Scaling
- Model Building
- Model Performances & Feature Importance
- Make Pickle File
- Create New Enviornment
- Create Web App With Streamlit
- Upload All Files In Github Repository
- Deploy Model On Heroku

**Web App Overview**

![Customer Cunversion Web App](https://github.com/vishalkrishna90/CUSTOMER-CONVERSION-PREDICTION/blob/main/Images/Web_app_2.png)
## Problem Statement

The problem statement is to build an ML model that predicts if a client will subscribe to insurance or not. We need to use the historical data to reduce the cost of telephonic marketing, still it effective but Incur a lot of costs. It is also important to identify the customers that are most likely to convert beforehand so that they can be specifically targeted via call.

In a simple word, we have to build a model which helps any **Startup Insurance Company** can understand what strategy they should follow to get more and more **Customers** via call, they can also use this model to check the customer will subscribe there **Insurance** or not
## Data Collection
I found this dataset during the Guvi Hackathon, first I downloaded this dataset from google docs to
my local storage then uploaded in Github Repo and then imported in jupyter notebook

```
df = pd.read_excel('https://raw.githubusercontent.com/vishalkrishna90/CUSTOMER-CONVERSION-PREDICTION/main/Customer%20Conversion%20Prediction.xlsx')

```
**Data Overview**

![Data Overview](https://github.com/vishalkrishna90/CUSTOMER-CONVERSION-PREDICTION/blob/main/Images/Data_Overview.png)
## Data Description

The Customer Cunversion Prediction dataset has 45211 rows and 11 columns. This data frame contains the following columns:

age - Age of a person

job - type of job

marital - marital status

educational_qual - education status

call_type - contact communication type

day - last contact day of the month (numeric)

mon - last contact month of year

dur - last contact duration, in seconds (numeric)

num_calls: - number of contacts performed during this campaign and for this client

prev_outcome - outcome of the previous marketing campaign (categorical: "unknown","other","failure","success")

y - output
## Data Preprocessing
In this step first I checked there are any null and duplicate values present or not, and I found there are no null values present but some duplicate values was there, I dropped them and check there are any incorrect data present or not, and I found some amount of wrong data was there and I corrected them.

![Data Preprocessing 1](https://github.com/vishalkrishna90/CUSTOMER-CONVERSION-PREDICTION/blob/main/Images/Null_Values_1.png)
![Data Preprocessing 2](https://github.com/vishalkrishna90/CUSTOMER-CONVERSION-PREDICTION/blob/main/Images/Null_Values_2.png)
![Data Preprocessing 3](https://github.com/vishalkrishna90/CUSTOMER-CONVERSION-PREDICTION/blob/main/Images/Null_Values_3.png)

## Handle outliers
After correcting incorrect data, I checked whether there are any outliers present or not, and I found that there are some amount of outliers present, for more clarification, I used the IQR method to check outliers and I found that there are no outliers.

![Outliers 1](https://github.com/vishalkrishna90/CUSTOMER-CONVERSION-PREDICTION/blob/main/Images/Outliers_1.png)
![Outliers 2](https://github.com/vishalkrishna90/CUSTOMER-CONVERSION-PREDICTION/blob/main/Images/Outliers_2.png)

## Exploratory Data Analysis (EDA)
In this step I tried to Analyze the data very efficiently and deeply, first I checked correlation between features, 
then check feature distribution and then relation between features and target by graph

![EDA 1](https://github.com/vishalkrishna90/CUSTOMER-CONVERSION-PREDICTION/blob/main/Images/EDA_1.png)
![EDA 2](https://github.com/vishalkrishna90/CUSTOMER-CONVERSION-PREDICTION/blob/main/Images/EDA_2.png)
![EDA 3](https://github.com/vishalkrishna90/CUSTOMER-CONVERSION-PREDICTION/blob/main/Images/EDA_3.png)

## Data Encoding

After EDA I did data encoding by label and on hot encoder and create a new data frame for the next process

![Data Encoding](https://github.com/vishalkrishna90/CUSTOMER-CONVERSION-PREDICTION/blob/main/Images/Data_Encoding.png)

## Feature Selection
In this step first I splits features and target, then splits data into train
and test data

```
# split data into features and target
X = n_df.drop('result',axis = 1)
y = n_df['result']
```

```
# import train test split to split train and test data
from sklearn.model_selection import train_test_split
X_train,X_test,y_train,y_test = train_test_split(X,y, test_size=0.2)
```

## Data Balancing
There was a big problem with this project, I got an imbalance dataset, so before building a model first I had to balance the data, for balance the data I used the SMOTETomek library

```
from imblearn.combine import SMOTETomek
smt = SMOTETomek(sampling_strategy='all')
X_train, y_train = smt.fit_resample(X_train, y_train)
```


## Data Scaling

After data Balancing I scaled features train and test data 

```
# import standard scaler to scale data
from sklearn.preprocessing import StandardScaler
sc = StandardScaler()
X_train = sc.fit_transform(X_train)
X_test = sc.transform(X_test)
```

## Model Building
In this step, I build different - different models and checked their performance, and then chose the best model for the dataset

![Model 1](https://github.com/vishalkrishna90/CUSTOMER-CONVERSION-PREDICTION/blob/main/Images/Model_1.png)
![Model 2](https://github.com/vishalkrishna90/CUSTOMER-CONVERSION-PREDICTION/blob/main/Images/Model_2.png)

## Model Performances & Feature Importance
After model Building, I checked their performance by accuracy score and the model whose accuracy score was higher I consider that model to be a final model and then I checked important features based on that model 

![Model Performance](https://github.com/vishalkrishna90/CUSTOMER-CONVERSION-PREDICTION/blob/main/Images/Model_Performance.png)
![Feature Importance](https://github.com/vishalkrishna90/CUSTOMER-CONVERSION-PREDICTION/blob/main/Images/Feature_Importance.png)

## Make Pickle File
After getting score from the best model I created a Pickle file for the web app

```
import pickle as pkl
pkl.dump(greed_rfc, (open('ccp_model.pkl','wb')))
```

## Create New Enviornment
After making pickle file I created new virtual environment for the 
project and install required libraries and created web app in VS Code IDE

```
conda create -p customerconversion python==3.9 -y
```

```
pip install streamlit numpy pandas sklearn xgboost
``` 

## Create Web App With Streamlit
After installing all required libraries and dependencies I created web app 

![Web App 2](https://github.com/vishalkrishna90/CUSTOMER-CONVERSION-PREDICTION/blob/main/Images/Web_app_2.png)

## Upload All Files In Github repository

After creating web app I uploaded all files in github repository by git CLI
```
git config --global user.name "FIRST_NAME LAST_NAME"
```

```
git config --global user.email "myemail@gmail.com"
```

```
git add files_name
```

```
git commit -m  "about the commit"
```

```
git push origin main
```

## Deploy Model On Heroku

In the end, I deployed the model on Heroku, so that anybody can use the web app

[Customer Conversion Prediction Web App](https://customer-conversion-prediction.herokuapp.com/)

![Customer Conversion Prediction](https://github.com/vishalkrishna90/CUSTOMER-CONVERSION-PREDICTION/blob/main/Images/Web_app_1.png)
## Deployment Requirement Tools 

![Deploy](https://github.com/vishalkrishna90/CUSTOMER-CONVERSION-PREDICTION/blob/main/Images/st_im.png)

 - [Streamlit](https://streamlit.io/)
 - [Github Account](https://github.com/)
 - [Heroku Account](https://dashboard.heroku.com/apps)
 - [Visual Studio Code](https://code.visualstudio.com/)
 - [Git CLI](https://git-scm.com/book/en/v2/Getting-Started-The-Command-Line)



## Challenges

- Imbalance data
- Based on data there was some amount of outliers present but when I applied some approaches I found that are not outliers
- There were many categorical values present and I had to encode them one by one
- Creating web app and deployment on Heroku
