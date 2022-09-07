# Capstone: SG Food Recommender
Author: Choo Wende<br>
Date: 07 Sep 2022

---

## Background

In the recent years, e-commerce sales have increased exponentially, along side technological development. With e-commerce, there is a significant increase in the number of good products, offers & discounts etc. Recommendation Systems are an important element of the electronic business,
according to research, with personalized RSs improving sales by up to 35% through recommended items.([source](https://www.mdpi.com/2071-1050/13/19/10786/pdf?version=1632898502#:~:text=The%20recommendation%20systems%20aim%20to,are%20implemented%20for%20this%20purpose.))

Specifically in the Food & Beverages industry and the introduction of food deliveries services, many customers have adopted the use of delivery apps to order food. They have access to restaurants beyond its vicinity and have a lot more options.  

The use of food reviews website and social media platforms have facilitated customers in deciding their meal options. However, customers have to actively seach for restaurants that they may be interested in. 

In addition, with the easing of Covid restrictions, more tourists are coming to Singapore. 

Hence, it is critical to develop a food recommenders to facilitate shortlisting restaurants or food for each customers based on their profile.

## Problem Statement
As part of a team of analyst in Yelp Singapore, the project aims to build a SG Food Recommender based on user's reviews and ratings from Yelp website ([link](https://www.yelp.com/)) as explicit input. 

The Recommender should shortlist a list of restaurants not visited by the user and predict the their ratings for the restaurants. Thereafter, the Recommender will recommend the top rated restaurants for the user. 

The Recommender may be deployed online to allow customers to access the recommended restaurants list generated.

## Executive Summary

1. The project conducted **Webscrapping** for restaurant and reviews data from Yelp website, specifically for Singapore restaurants and their corresponding reviews. The data is then cleaned and imputed while presesrving the integrity of the data to develop accurate recommender. 

2. **Exploratory Data Analysis (EDA)** is performed to gather new insights on the data scraped. 
    - EDA identified food that are unique to Singapore, such as chicken rice, chilli crab and bak kut teh. 
    - Topic Modelling (Latent Dirichlet Allocation (LDA)) is used to understand the content of the reviews. It is recommended that the SG Food recommender be marketed to overseas travellers who wants to explore unqiuely Singapore food and restaurants, which are largely largely reviewed by locals.


3. **SG Food Recommender** is built based on filtering restaurants (by user location, similar users and similar restaurants) and predicting the user ratings using Singular Value Decomposition (SVD) model, which was has the lowest Root Mean Squared Error and one of the highest Precision@k and Recall@k score among the other models explored. 

## Content
The project consists of three notebooks.

- Part 1: Webscrapping and Data Cleaning
- Part 2: EDA and Topic Modelling
- Part 3: Recommendation Systems

## Data Dictionary

|Features|Description|
|---|---|
|rest_name <br/> href<br/> address<br/> postal_code <br/> latitude<br/> longitude<br/> opening<br/> img<br/> star_rating<br/> review_count</br> location<br/> price_range|These are restaurant information.|
|username<br/> userid<br/> user_location<br/>|These are user information.|
|user_rating<br/> review_date<br/> comment<br/> |These are user's review information|
|category_{name}|These are restaurants' categories. Restaurans can have more than one category.|

## Model Summary

|    | model_name       |   train_cross_val_rmse |   train_rmse |   test_rmse |   average_model_precision |   average_model_recall |
|---:|:-----------------|-----------------------:|-------------:|------------:|--------------------------:|-----------------------:|
|  6 | svd              |                  0.896 |        0.748 |       0.894 |                     0.581 |                  0.529 |
|  1 | baselineonly     |                  0.898 |        0.81  |       0.896 |                     0.59  |                  0.529 |
|  5 | knn_baseline     |                  0.908 |        0.49  |       0.916 |                     0.594 |                  0.528 |
|  2 | knn_basic        |                  0.95  |        0.552 |       0.953 |                     0.168 |                  0.071 |
|  3 | knn_means        |                  0.971 |        0.551 |       0.964 |                     0.467 |                  0.458 |
|  4 | knn_zscore       |                  0.971 |        0.557 |       0.966 |                     0.466 |                  0.457 |
|  0 | normal_predictor |                  1.278 |        1.292 |       1.275 |                     0.55  |                  0.438 |



## Conclusion and Recommendations
1. The project successfully developed a SG Food Recommender using restaurants information and users' reviews scrapped from Yelp website. 

2. From the Exploratory Data Analysis, 
    - There are almost five times more overseas users who reviewed the restaurants than locals. However, the number of reviews by overseas users and locals are comparable. 
    - From the most common bigrams and trigrams used in the `comment` column, many findings are related to food unique to Singapore, such as chicken rice, chilli crab and bak kut teh. 
    - Hence, it is recommended that the SG Food recommender be marketed to overseas travellers who wants to explore unqiuely Singapore food and restaurants, which are largely largely reviewed by locals.
<br><br>
3. From the recommender system, the recommender filter restaurants based on user location, restaurants highly rated by similar users and restaurants similar to those highly rated by the user. The 'svd' model is used to predict the rating of restaurants not visited by the user. The top rated restaurants predicted by the model is then recommended to the user. 
    - Three case studies were conducted and concluded that the SG Food Recommender was able to predict ratings of restaurants not visited by the users. 
    - The recommender provided relevant recommended restaurants based on distance and user location. 


## Future Works
1. **Building database**. Other than Yelp website, other reviews from other website and social media could be referenced to gather a more comprehensive data set for training, testing and deploying. 
2. **Implicit Data**. The project could explore collecting users' activity, such as clicking on restaurant link etc, on Yelp to be used to enhance the consine similarity between users. 
3. **Content of Users' Comment**. While EDA identified top bi-grams and tri-grams, they are not used in the development of the recommender system. In addition, users' sentiments were also not considered. These could be included in future enhancement of the recommender to better personalised the recommendations. 
4. **Neural NEtwork and Deep Learning**. These could be explored for future enhancement of the recommender system. 