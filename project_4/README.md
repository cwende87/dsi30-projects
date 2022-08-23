<img src="http://imgur.com/1ZcRyrc.png" style="float: left; margin: 20px; height: 55px">

# Project 4 - West Nile Virus Prediction

### Authors: Cheong Hao Han, Phua Jia Qing, Choo Wende
---

## Background & Outside Research

#### **West Nile Virus**
West Nile virus (WNV) is the leading cause of mosquito-borne disease in the continental United States. It is most commonly spread to people by the bite of an infected mosquito. Roughly 20% of people who are infected develop a fever and other symptoms which could lead to a more serious and fatal illness. Only certain species of mosquitoes can transmit WNV as shared by ([*source*](https://www.sgvmosquito.org/west-nile-virus)). 

#### **West Nile Virus Peak Season and Optimal Conditions**
Most cases of WNV happens during mosquito season, which starts in summer and continues through fall. This is due to the fact that mosquitoes breed in water. The 'Preventive Pest Control' blog shares some weather patterns that aid mosquitoes breeding. One can understand more from ([*source*](https://www.orkin.com/pests/mosquitoes/when-are-mosquitoes-most-active)). Some factors are:

- Rain Water
- Precipitation
- Higher Temperature

#### **Mosquitoes Activity**
Mosquitoes are most active at night and are likely to start to bite early in the evening. Hence, the best time to kill adult mosquitoes is to spray at dusk, when they are most active and looking for people to bite. Mosquitoes activity are affected by:

- Humidity 
- Wind

## Problem Statement

West Nile Virus (WNV) is a deadly virus that should not be taken lightly. Hence, Chicago Department of Public Health (CDPH) had established a comprehensive surveillance and control system by setting up traps for mosquitoes in order to test for the presence of WNV. CDPF have partnered with us for this research.

The purpose of this research is to develop a model which predicts the presence of West Nile Virus (WNV) at various areas and time. The model aims to:

- Predict areas with probable surge in number of WNV in advance.
- Propose practicable solutions to mitigate spread of WNV in the identified areas. 

Using these information, we would be able to make inform decisions on where and when to deploy pesticides in Chicago. This way, we can maximise the effectiveness of pesticide while minimising monetary expenses.

--------

## Data Dictionary

| **Dataset** | **Features**                                                                                                                                                  | **Year Available for** |
|-------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------|
| **Weather** | - Date<br/> - Temperature<br/> - Sunset/Sunrise Timing<br/> - Precipitation<br/>                                                                              | 2007-2014              |
| **Spray**   | - Date<br/> - Time<br/> - Location<br/>                                                                                                                       | 2011 & 2013            |
| **Train**   | - Date<br/> - Location of Mosquitos<br/> - Mosquitos Species</br> - Location of Trap<br/> - Number of Mosquito Caught<br/> - Presence of West Nile Virus<br/> | 2007, 2009, 2011, 2013 |
| **Test**    | Same as Train, excluding Number of Mosquito Caught and Presence of West Nile Virus                                                                            | 2008, 2010, 2012, 2014 |



--------


## Content

**Part 1: Data Cleaning and Processing**
<br>
_(Project_4_Part1_WJH.ipynb)_
1. Weather Data
2. Spray Data
3. Train and Test Data
4. Merge and Save DataFrame

**Part 2: Exploratory Data Analysis**
<br>
_(Project_4_Part2_WJH.ipynb)_
1. Map Overview of Data
2. Train Data Analysis
3. Weather Data Analysis
4. Spray Data Analysis

**Part 3: Modelling**
<br>
_(Project_4_Part3_WJH.ipynb)_
1. Preprocessing
2. Modelling
3. Model Comparison
4. Kaggle Submission
5. Cost-Benefit Analysis
6. Conclusion & Recommendations

--------


## Model Summary

| # |               **Models**               | **Best Score** | **Train Score** | **Test Score** | **ROC_AUC_Score** |
|:-:|:--------------------------------------:|:--------------:|:---------------:|:--------------:|:-----------------:|
| 1 | **_LogisticRegression(max_iter=400)_** |    0.821835    |     0.831480    |    0.795655    |    **0.729464**   |
| 2 |      **_KNeighborsClassifier()_**      |    0.736780    |     0.863922    |    0.697192    |      0.627095     |
| 3 |     **_RandomForestClassifier()_**     |    0.833840    |     0.866323    |    0.815099    |      0.728088     |
| 4 |       **_AdaBoostClassifier()_**       |    0.833517    |     0.849368    |    0.811328    |      0.725872     |
| 5 |   **_GradientBoostingClassifier()_**   |    0.834458    |     0.888404    |    0.818053    |      0.670760     |
| 6 |      **_ExtraTreesClassifier()_**      |    0.829349    |     0.849932    |    0.808676    |      0.720470     |

--------


## Conclusion & Recommendation

Spraying is costly and has temporal effect (last about 2 weeks) in mitigating WNV. 

Based on historical data, mosquito number starts to increase when:

1. Heat level decrease
2. Cool level increase
3. PrecipTotal increase

Based on the model features coefficients, the top 10 dominant features identified by the random forest model are: 

1. DayDuration (mosquito are more active at night)
2. week, month, year (these seasonal trends that is related weather conditions, which affect mosquito activities)
3. trap_cluster_mod_wnv (this the cluster identified by KMeans model)
4. Tavg and cool (High temperature promots mosquito activities)
5. R-Humid and Dewpoint (high moisture increases mosquito activities)
6. Avg Wind Speed (low wind speed promotes mosquito activities as they are poor flyers)

Hence, spraying is recommneded around mid July where weather conditions favours mosquitos activities. As spraying is costly, spraying can be done at  areas with high number of mosquitos and WNV present expected based on model prediction. The top three areas based on past history are:
1. T900: ORD Terminal 5, O'Hare International Airport,
2. T115: South Doty Avenue, Chicago, IL, USA
3. T002: 4100 North Oak Park Avenue, Chicago, IL 60634,

