![Logo](https://d1aueex22ha5si.cloudfront.net/Conference/423/BackGround/Cardio%20care-1549632167059.gif)

**Cardiovascular disease(CVD’s) are a group of life threatening diseases which takes millions of lives world wide.Early diagnosis can help in saving lives as it is said that prevention is better can cure. If our model is able to identify persons, who are at most risk of getting of CVD’s  then it would greatly help doctors to save lives by starting early diagnosis and reduce the chances of death.
Our project aims at building ML models to detect high risk persons who are most vulnerable towards suffering from CVD’s** 
![--](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)
# **Index**

|  SI.No.            |   Content                                                              |
| ----------------- | ------------------------------------------------------------------ |
| 1 | <a href = "https://github.com/omkardesai98/Cardiovascular-Risk-Prediction#1-Introduction"> Introduction </a> |
| 2| <a href = "https://github.com/omkardesai98/Cardiovascular-Risk-Prediction#1-Data Collection and Understanding"> Data Collection and Understanding </a> |
| 3 | <a href = "https://github.com/omkardesai98/Cardiovascular-Risk-Prediction#1-Data Cleaning and Manipulation"> Data Cleaning and Manipulation </a> |
| 4 | <a href = "https://github.com/omkardesai98/Cardiovascular-Risk-Prediction#1-Exploratory Data Analysis (EDA)"> Exploratory Data Analysis (EDA) </a>  |
| 5 | <a href = "https://github.com/omkardesai98/Cardiovascular-Risk-Prediction#1-Model Selection And Evaluation"> Model Selection And Evaluation </a>  |
| 6 | <a href = "https://github.com/omkardesai98/Cardiovascular-Risk-Prediction#1-Conclusion">Conclusion </a>  |

![--](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)

# **1. Introduction**:
*   Cardiovascular diseases (CVDs) are the leading cause of death globally.
*   An estimated 17.9 million people died from CVDs in 2019, representing 32% of 
all global deaths. Of these deaths, 85% were due to heart attack and stroke.

*   Most cardiovascular diseases can be prevented by addressing behavioural risk factors such as tobacco use, unhealthy diet and obesity, physical inactivity and harmful use of alcohol.
*   It is important to detect cardiovascular disease as early as possible so that management with counselling and medicines can begin.

**Cardiovascular diseases (CVDs) are a group of disorders of the heart and blood vessels. They include:**

**1. coronary heart disease –** a disease of the blood vessels supplying the heart muscle;

**2. cerebrovascular disease –** a disease of the blood vessels supplying the brain;

**3. peripheral arterial disease –** a disease of blood vessels supplying the arms and legs;

**4. rheumatic heart disease –** damage to the heart muscle and heart valves from rheumatic fever, caused by streptococcal bacteria;

**5. congenital heart disease –** birth defects that affect the normal development and functioning of the heart caused by malformations of the heart structure from birth;
 and
**6. deep vein thrombosis and pulmonary embolism –** blood clots in the leg veins, which can dislodge and move to the heart and lungs.


**This project is based upon a medical domain dataset, and it has been collected from various patients. It includes entries of over 3000 patients and has 16 different attributes for the prediction of Coronary Heart Diseases in patients for the next 10 years.**

![--](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)

# **2. Data Collection and Understanding**
**This project is based on medical domain dataset and it has been collected from various patients.It includes entries of over 3000 patients and has 17 different attributes for the prediction of Coronary Heart Disease in patients for the next ten years
It includes 3390 records and 17 attributes.Variables each attribute is a potential risk factor.There are both demographic,behavioral and medical risk factors**
![--](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)

# **3. Data wrangling and Feature Engineering**

* **Categorical features :** is_smoking, sex, bp_meds, prevalent_hyp, prevalent_stroke. diabetes
* **Numerical features :**  age, cigs_per_day, total_cholesterol, systolic_bp, diastolic_bp, bmi, heart rate, glucose

**1. Rename columns: We have renamed columns to give appropriate name to features and removed spaces in-between**

**2. Checking for duplicate rows : We had zero duplicate rows in our dataset**

**3. Checking for missing values : Missing values were present in  education, cigs_per_day, bp_meds, total_cholesterol, bmi, heart_rate, glucose**

**1) Data Splitting: Before performing any feature engineering step, we need to split the data into a training and testing dataset to prevent data leakage.Since the data is imbalanced, a stratified split was employed to get an almost equal proportion of dependent variables in the training and test sets.**

**2) Handling Missing values : As in our dataset, some features contain missing values, so before model building we need to take care of them.**

**3) Categorical Encoding: As all our categorical features have binary labels so we have use binary label encoding technique.**

**4) Handling Skew and Outliers: The skew in numeric variables is reduced by performing log transformation.
The outliers beyond 3 standard deviations from the mean were imputed with the median value**

**5) Feature Manipulation and Selection:**
* removing multicollinearity: As in our dataset Systolic blood pressure and diastolic blood pressure are highly correlated. Hence to solve multicollinearity we create new feature.
* **Pulse pressure = Systolic BP – Diastolic BP**

* **Different feature selection methods we used such as :**
* Gini Impurity
* Chi2 Test 
* Information Gain

**6) Data Scaling: Since predictions from the distance-based models will be affected if the attributes are in different ranges, we use StandardScaler to scale down the variables.**

**7) Handling Imbalanced Dataset:
Since we are dealing with unbalanced data, i.e., only 15% of the patients were diagnosed with coronary heart disease, we oversample the training dataset using SMOTE (Synthetic Minority Oversampling Technique).
This will ensure that our model has been trained equally on all kinds of results and is not biased towards one particular result.**
![](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)

# **4. Exploratory Data Analysis (EDA)** 
## Screenshots
![image](https://user-images.githubusercontent.com/106911079/219087143-da1bded9-c2b5-4bbc-81b2-9028e1863331.png)
![image](https://user-images.githubusercontent.com/106911079/219089372-b200f698-a8af-4c8a-bd4d-393261afbae8.png)
![image](https://user-images.githubusercontent.com/106911079/219089816-16db003d-4e7c-4705-a7b2-a479378fcefd.png)
![image](https://user-images.githubusercontent.com/106911079/219089974-8cae7c40-3af4-4d8d-a540-6a1f650c9b74.png)


![](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)
# **5. Model Selection And Evaluation**
**Before starting model building, it’s important to choose the evaluation metric.
We have chosen recall as the evaluation metric. Because this is a health-care dataset, it is critical to predict who is most likely to develop heart disease. We are fine with a false positive (the model predicted heart disease and the person did not get heart disease), but a false negative (the  model did not predict heart disease and the person got heart disease) is very dangerous as the person may lose his life.**
![image](https://user-images.githubusercontent.com/106911079/219090249-aee49a19-2296-4a63-be24-015101e0eae4.png)
![image](https://user-images.githubusercontent.com/106911079/219090387-5c3a3660-ad55-4f45-b873-86d4dbd7adab.png)

![](https://raw.githubusercontent.com/andreasbm/readme/master/assets/lines/rainbow.png)
# **6. Conclusion**
**We trained 7 machine learning models using the training dataset, and hyperparameter tuning was used in some models to improve the model's performance.
 Missing values were handled, feature engineering and feature selection were carried out, and the training dataset was oversampled using SMOTE to reduce bias on one outcome.
 We chose recall as the model evaluation metric because it was critical that we reduce false negatives.
 Predicting the risk of coronary heart disease is critical for reducing fatalities caused by this illness. We can avert deaths by taking the required medications and precautions if we can foresee the danger of this sickness ahead of time.
It is critical that the model we develop has a high recall score. It is OK if the model incorrectly identifies a healthy patient as a high risk patient because it will not result in death, but if a high risk patient is incorrectly labelled as healthy, it may result in fatality.6)We were able to create a model with a recall of just 0.81 because of limitated data available and limited computational power available.
 A recall score of 0.81 indicates that out of 100 individuals with the illness, our model will be able to classify only 81 as high risk patients, while the remaining  19 will be misclassified.
Future developments must include a strategy to improve the model recall score, enabling us to save even more lives from this disease. This includes involving more people in the study, and include people with different medical history, etc. build an application with better recall score.
From our analysis, it is also found that the age of a person was the most important feature in determining the risk of a patient getting infected with CHD, followed by pulse pressure, prevalent hypertension and total cholesterol.10) Diabetes, prevalent stroke and BP medication were the least important features in determining the risk of CHD.**
