# Home Credit Default Risk Project
### 1. Description
Many people struggle to get loans due to insufficient or non-existent credit histories. And, unfortunately, this population is often taken advantage of by untrustworthy lenders.

Home Credit Group

Home Credit strives to broaden financial inclusion for the unbanked population by providing a positive and safe borrowing experience. In order to make sure this underserved population has a positive loan experience, Home Credit makes use of a variety of alternative data--including telco and transactional information--to predict their clients' repayment abilities.

While Home Credit is currently using various statistical and machine learning methods to make these predictions, they're challenging Kagglers to help them unlock the full potential of their data. Doing so will ensure that clients capable of repayment are not rejected and that loans are given with a principal, maturity, and repayment calendar that will empower their clients to be successful.

### 2. Udacity Final Project
This directory contain all code that was used for the Udacity Data Scientist Nanodegree Program


### 3. Define the Problem
For this project, the problem statement is given to us , develop an algorithm to predict the default of home credit .

Project Summary: Many people struggle to get loans due to insufficient or non-existent credit histories. And, unfortunately, this population is often taken advantage of by untrustworthy lenders.

In this project, we ask you to complete the analysis of which customers of home credit were likely default. In particular, we ask you to apply the tools of machine learning to predict which customers defaulted.

Project Metrics: Default customer can be predicted using less variable at credit risk perspective. So selected model specification must be explainable and applicable.

### 4. Gather the Data
The dataset is given to us as test and train data at Kaggle's Home Credit Default Risk

#### 4.1 Import Libraries
The following code is written in Python 3.x. Libraries provide pre-written functionality to perform necessary tasks.

#### 4.2 Prepare the Data
To begin this step, The data is imported firstly . Next we use the info() and head() function, to get a quick and dirty overview of variable datatypes (i.e. qualitative vs quantitative). Click here for the Source Data Dictionary.

What is the distribution of categorical features?

* Contract type as two possible values with 90% Cash loans (top=Cash loans, freq=278232/count=307511).
* Gender variable as three possible values with 66% female (top=female, freq=202448/count=307511).
* Own Car variable as two possible values with 66% "No" (top=N, freq=202924/count=307511).
* Own Realty variable as two possible values with 69% "Yes" (top=Y, freq=213312/count=307511).
* Suite Type variable as seven possible values with 81% unaccompanied (top=Unaccompanied, freq=248526/count=306219).
* Income Type variable as eight possible values with 81% Working (top=Working, freq=248526/count=307511).
* Education Type variable as five possible values with 71% unaccompanied (top=Secondary / secondary special, freq=218391/count=307511).
* Family status variable as six possible values with 64% "Married" (top=Married, freq=196432/count=307511).
* Housing type variable as six possible values with 89% "House / apartment " (top=House / apartment, freq=272868/count=307511).
* Occupation type variable as eighteen possible values with 26% "Laborers" (top=Laborers, freq=55186/count=211120).
* Weekday aproval process start day variable as seven possible values with 18% "TUESDAY" (top=TUESDAY, freq=53901/count=307511).
* Organization type variable as fifty eight possible values with 22% "Business Entity Type 3" (top=Business Entity Type 3, freq=67992/count=307511).
* Fondkapremont mode variable as four possible values with 76% "reg oper account" (top=reg oper account, freq=73830/count=97216).
* House type variable as three possible values with 98% "block of flats" (top=block of flats, freq=150503/count=153214).
* Walls material variable as seven possible values with 44% "Panel" (top=No, freq=66040/count=151170).
* Emergency state variable as two possible values with 99% "No" (top=No, freq=159428/count=161756).

### 4. The 4 C's of Data Cleaning: Correcting, Completing, Creating, and Converting
* In this stage, data should have been cleaned

Correcting abnormal values and outliers
Completing missing information
Creating new features for analysis
Converting fields to the correct format for calculations and presentation.
Correcting: Reviewing the data, there should have been analyzed to be any abnormal or non-acceptable data inputs. In addition, age and income may have outlier values.Exploratory analysis will done to find reasonable values. Outliers should been elimated in dataset.It should be noted, that if unreasonable values were , for example age is 1000 then it also should be elimaneted.

Completing: There are null values or missing data in dataset. Missing values can be bad, because some algorithms don't know how-to handle null values and will fail. While others, like decision trees, can handle null values. Thus, it's important to fix before modeling will started because several models will have compared. There are two common methods, either delete the record or populate the missing value using a reasonable input. It is not recommended to delete the record, especially a large percentage of records, unless it truly represents an incomplete record. Instead, it's best to impute missing values. A basic methodology for qualitative data is impute using mode. A basic methodology for quantitative data is impute using mean, median, or mean + randomized standard deviation.

Creating: Feature engineering is when we use existing features to create new features to determine if they provide new signals to predict our outcome.

Converting: Last, but certainly not least, we'll deal with formatting. There are no date or currency formats, but datatype formats. Our categorical data imported as objects, which makes it difficult for mathematical calculations. For this dataset, we will convert object datatypes to categorical dummy variables

### 6. Correlation Elimination 

All variable analyze the correlation of target. We will choose higher than 0.05 or lower than -0.005. Correlations are very useful in many applications, especially when conducting regression analysis. However, it should not be mixed with causality and misinterpreted in any way. I should also always check the correlation between different variables in our dataset and gather some insights as part of my exploration and analysis.

#### 6.1 Elimination List
EXT_SOURCE_1 variable is elimanted because of high correlated age_cal. I can choose the age_cal
EXT_SOURCE_3 variable is elimanted because of high correlated age_cal. I can choose the age_cal
Age_bin variable is elimanted because of high correlated age_cal. I can choose the age_cal
Gender_M variable is elimanted because of high correlated Gender_F. I can choose the Gender_F
REGION_RATING_CLIENT_W_CITY is elimanted because of moderate correlated ext_source_2. I can choose the ext_source_2
NAME_INCOME_TYPE_Working is elimanted because of moderate correlated age_cal. I can choose the age_cal

#### 6.2 Final Model Variable

* AGE_CAL
* CODE_GENDER_F
* DAYS_LAST_PHONE_CHANGE

#### 6.3 Train Test Cross Validation Split
the data we use is usually split into training data and test data. The training set contains a known output and the model learns on this data in order to be generalized to other data later on. We have the test dataset (or subset) in order to test our model’s prediction on this subset. In order to avoid this, we can perform something called cross validation. It’s very similar to train/test split, but it’s applied to more subsets. I decided to split size in below side

* Train dataset %60
* Test dataset %20
* Cross Validation dataset %20
### 7. Modelling
#### 7.1 Modelling selection
In literature logistic regression have been used usually for credit risk modeling. So I selected logistic regression modelling approach. If accuracy and precision is lower than expectation, we will try more machine learning methodolgy.

### 7.2 Modelling Metric
In literature modelling result is done comparing auc roc score and precision. We have focused auc roc score and precision. It is one of the most important evaluation metrics for checking any classification model’s performance. AUC - ROC curve is a performance measurement for classification problem at various thresholds settings. ROC is a probability curve and AUC represents degree or measure of separability. It tells how much model is capable of distinguishing between classes. Higher the AUC, better the model is at predicting 0s as 0s and 1s as 1s.

In a classification task, the precision for a class is the number of true positives (i.e. the number of items correctly labeled as belonging to the positive class) divided by the total number of elements labeled as belonging to the positive class (i.e. the sum of true positives and false positives, which are items incorrectly labeled as belonging to the class). Recall in this context is defined as the number of true positives divided by the total number of elements that actually belong to the positive class (i.e. the sum of true positives and false negatives, which are items which were not labeled as belonging to the positive class but should have been).

In information retrieval, a perfect precision score of 1.0 means that every result retrieved by a search was relevant (but says nothing about whether all relevant documents were retrieved) whereas a perfect recall score of 1.0 means that all relevant documents were retrieved by the search (but says nothing about how many irrelevant documents were also retrieved).

It is also important for us that what percentage of estimated defaults are true defaults

#### 7.4 Data Sampling
Our model have not been predicted default customers. So we will need to apply new machine learning aproach and data set aproach
We are doing sampling 50:50. Our dataset 24825 default customer and 24825 non-default customer. So we will train the alternative model for this dataset

* Proportion of default in train: 0.4989929506545821
* Proportion of default in test: 0.5003021148036254
* Proportion of default in valditaion: 0.5027190332326285

#### 7.5 Modelling Result
QuadraticDiscriminantAnalysis is best score Precision and Area under the curve

Precision: 0.6044389130885708
Area under the curve: 0.6088810563323734
GradientBoostingClassifier is best score Precision and Area under the curve

Precision: 0.6101585940848693
Area under the curve: 0.6126581898558849

#### 7.6 Model Refinement
QuadraticDiscriminantAnalysis is best model for results_precision and results_auc in kfold validation data. So the best model QuadraticDiscriminantAnalysis for this sampling dataset

##### 7.6.1 K-Fold cross validation
Now, we evaluate the performance of our classifiers with a 10-Fold cross validation.


### 8. Conclusion

My expectation would be credit type,credit amount or income type for final variable modelling. But these variable were eliminated correlation step. I am surprised for this happen. This proeject aimed to end to end data processing and data modelling in credit risk data. I enjoyed to analyze and create this project

### 9. References
* [Udacity Data Scientist Nanodegree Program](https://www.udacity.com/course/data-scientist-nanodegree--nd025)
* [Kaggle's Home Credit Default Risk](https://www.kaggle.com/c/home-credit-default-risk)
* [Source Data Dictionary](https://www.kaggle.com/c/home-credit-default-risk/data)
* [Creating New Column](https://stackoverflow.com/questions/21702342/creating-a-new-column-based-on-if-elif-else-condition)
* [Correlation Elimination](https://towardsdatascience.com/why-feature-correlation-matters-a-lot-847e8ba439c4)
* [Train Test Cross Validation](https://tarangshah.com/blog/2017-12-03/train-validation-and-test-sets/)
* [Credit Risk Modelling](https://smartdrill.com/pdf/Credit%20Risk%20Analysis.pdf)
* [Lgistic Regression](https://towardsdatascience.com/logistic-regression-detailed-overview-46c4da4303bc)
* [Gradient Boosting](https://machinelearningmastery.com/gentle-introduction-gradient-boosting-algorithm-machine-learning/)
* [LightGBM’s documentation](https://lightgbm.readthedocs.io/en/latest/)
* [Pandas Data Frame Describe](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.describe.html)
* [Pandas Missing Data](https://pandas.pydata.org/pandas-docs/stable/reference/frame.html#missing-data-handling)
* [tactics-to-combat-imbalanced-classes-in-your-machine-learning-dataset](https://machinelearningmastery.com/tactics-to-combat-imbalanced-classes-in-your-machine-learning-dataset/)
* [Precision_and_recall#F-measure](https://en.wikipedia.org/wiki/Precision_and_recall#F-measure) 
* [understanding-auc-roc-curveReferences](https://towardsdatascience.com/understanding-auc-roc-curve-68b2303cc9c5)
