# Project 3: Web APIs & NLP

_Author: Choo Wende_

_Date: 28 Jul 2022_

---

## Background




Many countries have shift their approach to classify COVID-19 as endemic. As with many countries, Australia's tourism has been crippled in the last two years. With the easing of travel restrictions to and from Australia as of 6 Jul 2022 ([source](https://www.homeaffairs.gov.au/covid19/entering-and-leaving-australia)), there is a need to boost its tourism sector. Some of the uncertainties that is affecting tourism is as follows([source](https://www.tra.gov.au/international/international-tourism-forecasts/international-tourism-forecasts)):
1. risk of further outbreaks
2. travellers' concern around safety and health
3. availability of long-haul international flights. 


## Problem Statement

The project is assigned to a team of analysts in Tourism Australia, an Australian Government agency responsible for promoting Australian locations as business and leisure travel destinations, to promote tourism in Australia post-Covid. As Australia has scenic cross-city roads, the project targets at travellers who enjoy having roadtrips and explore means to encourage them to come to Australia. The project will develop a classification model to classify submissions into two shortlisted subreddits. The model will help the agency to identify which subreddit to review on various travel related topics. It will also help travellers to decide which subreddits to post their submissions for discussion during itinerary planning. The findings from the project will be presented to Tourism Australia management for support to implement the proposal and model. 

The project aims to:
- Shortlist two subreddits that are related to the problem statement for analysis. 
- Create a text classifier to determine whether a reddit post would be classified into the two shortlisted Subreddit groups.
- By using the Reddit API, submmissions on these two subreddits will be scraped, processed and used to build our NLP classifier. This classifier model will enable potential travellers to decide which subreddits to discussed online, research and plan itineraries based on their desired objectives.
    - Two models will be developed: a logistic regression and a multinomial naive Bayes classifier.
    - The model will also help the Tourism Australia to identify which subreddit to review given the list of topics of interest, e.g. flight discounts, car rental concerns etc.
- The project will be measuring the success of our classifier model by looking at several metrics, including accuracy, specificity, sensitivity and ROC AUC scores.

## Executive Summary

1. The project explore data scraped from five subreddits (AustraliaTravel, roadtrip, TravelHacks, TravelNoPics, Travel). TravelHacks & roadtrip were shortlisted due to comparable number of unique submissions, similar submissions frequency and substantial number of members.
2. Rows with deleted post, removed submissions, contained empty string and duplicated were dropped. 
3. From TravelHacks, key discussions revolves around 'flight'. 
4. From roadtrip, 'road', 'drive' and 'car' were discussed frequently. 
5. The sentiment scores for submissions in both subreddits were highly positive. 
6. Three models were developed:
    - Base model: Logistics Regression Model without Optimisation (logreg_base)
    - Logistics Regression Model with Cvec/Tvec (gs_logreg_model)
    - Naive-Bayes Model with Cvec/Tvec (gs_nb_model)
7. The gs_logreg_model provide the highest test accuracy and ROC AUC score of 92% and 97% respectively. Hence, it was recommended to be deployed online for travellers to identify which subreddit to post their queries or research on itinerary. 
8. The top 5 important features use to classify the respective subreddits are shown in the table below. This means that the probability of a submission classifying in the respective subreddit increase with the increase of the number of words in each group.

|TravelHacks|roadtrip|
|-|-|
|flight|road|
|travel|drive|
|book|roadtrip|
|ticket|stop|
|airline|route|

9. The project identify the various topics and proposals in each subreddits for Tourism Australia to review to attract travellers and promote roadtrips in Australia. 
    - TravelHacks: flight deals & availability, car rental cost & trustworthiness, covid testing, vaccination, travel insurance
    - roadtrip: safety, stops/detours, attractions, vehicle types.

## Data Dictionary 

**combined_posts data set:**

|Feature|Type|Description|
|---|---|---|
|author|object|This is the author of the submission|
|subreddit|object|This is name of the sub-reddits|
|selftext|object|This is the main content of the submissions in the sub-reddits|
|title|object|This is the title of the sub-reddits|
|created_utc|integers|This is the time of submission creation in Unix epoch format|

## Overview of all models

|Model|Cross Validated Score|Training Accuracy|Accuracy|Sensitivity|Specificity|ROC|
|-|-|-|-|-|-|-|
|logreg_base|0.898408|0.997111|0.905769|0.928315|0.879668|0.964024|
|logreg_tvec (gs_logreg_model)	|0.922237|0.953779|0.919231|0.935484|0.900415|0.969363|
|nb_cvec (gs_nb_model)|0.932595|0.932595|0.898077|0.870968|0.929461|0.959904|




## Recommendations and Future Works

### Proposed Classification Model: Logistics Regression Model with TF-IDF vectorizer (logreg_tvec)

1. The project proposed the adoption of Logistics Regression Model with TF-IDF vectorizer (logreg_tvec) to the Senior Management Team of the agency.
2. The model has highest test Accuracy score and ROC score of 95% and 97% respectively.
3. The model has a Training Cross Validation accuracy score of 92%. This means the model is able to explain 92% of the variance in the subreddit classifications.
4. It is recommended that logreg_tvec (Logistics Regression Model with tf-idf vectorizer) is the best classification model of all the models and will be proposed to the senior management to deploy online for travellers to use. 

### Proposals to Attract Travellers based on respective Subreddits. 
(based on assessment of coefficients/importance of features and sentiment analysis)

**Findings from TravelHacks**
1. Flight Deals and Availability:
    - The project may consider reviewing strategies implemented by airlines at TravelHacks and partner airlines operating in Australia to attract travellers and increase availability of flight.
2. Car Rental Cost and Trustworthiness:
    - The project could consider attracting more car rental companies to operate at the airport to provide more economical solutions (increase supply will lower costs). Grading systems for car rental companies would be beneficial for traveller to make better informed decisions and partner with a more trustworthy rental company.
3. Covid Testing:
    - The project can explore formulating policy to support travellers who are tested positively to recoup some of the costs incurred during planning or to delay their trip. 
    -  The project can explore providing testing services at airport to facilitate travellers meeting the requirements to ease the travellers' burden.
4. Vaccination Status:
    - travellers are concerned about being vaccinated or show proof of vaccine when travelling to other countries. As vaccination is up to individuals. There is not much Australia can do about it. However, marketing resources may be invested in countries where vaccination take up rate is high, for example, Singapore.
5. Travel Insurance:
    - Given the uncertainty of the evolving Covid measures, it is important that travel insurance covers the unfortunate event that a traveller being infected by Covid. The project can consider partnering travel insurance agency to provide such coverage for this event.

**Findings from roadtrip**
1. Safety:
    - The project may review the typical routes for road trips in Australia to pass through areas that are safer. Police stations could be situated at intervals along the typical routes to assure travellers or assist travellers if needed.
2. Stops/detours:
    - The project may considor building attractions or amenities pit stop along typical scenic route in Australia so that travellers could take breaks in between long drives.
    - The project may consider establishing resting areas with amenities or camping areas around nature parks or along coastal roads unique to Austrialia, e.g. the Great Ocean Road.
3. Attractions:
    - Places of interests along the route to include nature parks and coastal roads. 
4. Vehicle Types:
    - The project can also partner car rental agency to supply more SUVs or campervans for better comfort, especially for families.



### Future Work to Improve Accuracy of the Model
1. Some of the submissions contains advertisements or websites addresses with insufficient content for the model to classify accurately. Such submissions should be extracted and not be considered in the project. 
2. In order to get meaningful analysis of the submissions, submissions should be of a certain length before they may be considered for assessment by the project team. 
3. As posts are scrapped from the past 8 months, the context may evolve especially with new development in the Covid virus situations. Being up to date with the latest development would be helpful in predicting future travel needs.
4. About 50% or more of the raw data consists of images and videos without a message body.  OCR on the images may be considered on these post to document the content for analysis.
5. As the roadtrips subreddit submissions centers around travelling in US, US related words could be added to the list of stopwords when training the model to be used for Australian context. 

## Conclusion

1. Logistics Regression Model with TF-IDF vectorizer (logreg_tvec) has the highest test accuracy with highest true positive (sensitivity) and true negative rates (specificity) and is recommended to be deployed online for travellers to identify subreddits to submit their post for discussion. 
2. The model has a Training Cross Validation accuracy score of 92%, explaining 92% of the variance in the subreddit classifications.
3. The project identify the various topics and proposals in each subreddits for Tourism Australia to review to attract travellers and promote roadtrips in Australia. 
    - TravelHacks: flight deals & availability, car rental cost & trustworthiness, covid testing, vaccination, travel insurance
    - roadtrip: safety, stops/detours, attractions, vehicle types.
4. The model will also help travellers to decide which subreddits to post their submissions for discussion during itinerary planning.
5. The project also identified various areas to explore to improve the accuracy of the model. 

