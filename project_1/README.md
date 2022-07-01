<img src="http://imgur.com/1ZcRyrc.png" style="float: left; margin: 20px; height: 55px">

# Project 1: Standardized Test Analysis

--- 
## Problem Statement

In the United States, SAT and ACT are two popular college admission tests. The introduction of the new SAT format in March 2016, as an employee of the College Board - the organization that administers the SAT, the project aims to analyse statewide participation and to provide recommendations to improve SAT participation rates in selected states.

## Executive Summary

SAT and ACT are two popular college admission tests in the United States. This project presents findings showing the relationships between participation rates of both test, as well as the test scores. 

The analysis showed that most of the states have either high SAT participation rate or high ACT participation rates. It is evident that most states adopt ACT. On the other hand, SAT participation rate has improved from 2017 to 2019, especially with the introduction of the new test format. The number of states with 100% SAT participation rate has doubled from 4 in 2017 to 8 in 2019. 

Many states (about 30% of the states in 2019) mandate ACT test, while only about 16% of the state mandate SAT test. The higher the participation rates in a either test usually the lower the test score. Also, the higher the participation in one test, the lower the participation rates in the other.

The project established a set of requirement to identify potential states to increase SAT participation rate. The project recommend to focus increasing SAT participation rate in **Minnesota** due to the following requirements.
1. Minnesota do not have any mandatory testing and seen from the decrease in ACT participation rate (about 5% from 2017 to 2019). 
2. Minnesota has low SAT participation of 4% and high ACT participation rate of 95% in 2019. SAT is likely acceptable to the students. 
3. Minnesota has a ACT composite score of 21.4, higher than the median of 21.1, given the high ACT participation rate. Students are likely to perform well for SAT. 
4. Minnesota also has the highest SAT score from 2017 to 2019.

The project found out that Illinois and Colorado have significant increase in SAT participation rate to 100% from about 10% between 2017 and 2019. Measures implemented in these states were considered. Hence, the project recommend the following:

1. Subsidies or fee waivers may be given to selected students. As the cost of the test decrease, there will be more students who will consider taking the test. Given the capacity of the students, they are likely to do well and will further encourage the younger students to consider SAT. 

2. Partnering established agency, such as [Manhattan Review](https://www.manhattanreview.com/minneapolis-sat-prep-courses/), to conduct SAT preparatory courses to provide students the confidence and support them in the switch from ACT to SAT. The course may be customised for Minnesota schools, highlighting key differences and benefits for taking SAT. 

## Data Dictionary 

**For Standardized Test dataframe (std_test_merged):**

|Feature|Type|Dataset|Description|
|---|---|---|---|
|state|object|sat_2017.csv, sat_2018.csv, sat_2019.csv|The United States of America is a federal republic consisting of 50 states and a federal district. ([source](https://2009-2017.state.gov/documents/organization/251864.pdf))|
|sat_2017_participation, sat_2018_participation, sat_2019_participation|float|sat_2017.csv, sat_2018.csv, sat_2019.csv|This is the participation rate for the SAT in the respective year.| 
|sat_2017_reading_and_writing, sat_2017_math, sat_2018_reading_and_writing, sat_2018_math, sat_2019_reading_and_writing, sat_2019_math |float|sat_2017.csv, sat_2018.csv, sat_2019.csv|The SAT scores includes the scores of Evidence-Based Reading and Writing, and Math in the respective year. Each SAT subjects are scored at between 200 and 800.([source](https://satsuite.collegeboard.org/sat/scores/understanding-scores/how-scores-are-calculated)) |
|sat_2017_total, sat_2018_total, sat_2019_total|float|sat_2017.csv, sat_2018.csv, sat_2019.csv|This is the total score from the scores of Evidence-Based Reading and Writing, and Math. Each SAT subjects are scored at between 200 and 800, with a total score of between 400 and 1600.([source](https://satsuite.collegeboard.org/sat/scores/understanding-scores/how-scores-are-calculated)) |
|act_2017_acrticipation, act_2018_participation, act_2019_participation|float|act_2017.csv, act_2018.csv, act_2019.csv|This is the participation rate for the ACT in the respective year.|
|act_2017_english, act_2017_math, act_2017_reading, act_2017_science|float|act_2017.csv|The ACT scores data in the respective years includes the scaled scores of English, Mathematics, Reading, Science tests. The composite score is then calculated as the average of the four test scores, rounded to the nearest whole number. It ranges from 1 to 36. ([source](https://www.act.org/content/act/en/products-and-services/the-act/scores/understanding-your-scores.html))|
|act_2017_composite, act_2018_composite, act_2019_composite|float|act_2017.csv, act_2018.csv, act_2019.csv|The ACT scores data in the respective years includes the scaled scores of English, Mathematics, Reading, Science tests. The composite score is then calculated as the average of the four test scores, rounded to the nearest whole number. It ranges from 1 to 36. ([source](https://www.act.org/content/act/en/products-and-services/the-act/scores/understanding-your-scores.html))|
|sat_2017_act_equivalent, sat_2018_act_equivalent, sat_2019_act_equivalent|float|Calculated using concordance_table.txt|For comparing SAT and ACT scores, the College Board organisation provides conversion charts to show how ACT composite score compare with SAT total score. Additional variables called 'ACT equivalent' is added into the merged dataframe. ([source](https://satsuite.collegeboard.org/media/pdf/guide-2018-act-sat-concordance.pdf))|

## Recommendation 

**Criteria in selecting states to increase SAT participation rate:**

1. State should not have mandatory ACT test (no contractual agreement). This will allow students to choose either SAT or ACT test, as it is observed that states with high ACT participation is likely to have low SAT participation. 
2. State should have low SAT participation and relatively higher ACT participation rate. This indicates that it is a social norm to take standardise test and pursue college/university education. There is also sufficient room to increase the participation rate. 
3. State should have ACT composite scores above the median. This indicates that the students have the capability to do well in the test given the high participation rate. This is also beneficial in building SAT's branding to further increase SAT participation in other states.
4. Given the above, the shortlisted states are Iowa, Kansas, Minnesota and South Dakota (refer to Exploratory Data Analysis, Investigate Trends, point 3). Of the 4 states, Minnesota has the highest ACT Participation rate (close to 100%) while the rest has about 60% to 80% ACT participation rate. Hence, it is assessed that **Minnesota** has the highest potential to convert from ACT to SAT participation
    - Minnesota do not have any mandatory testing and seen from the decrease in ACT participation rate (about 5% from 2017 to 2019). 
    - Minnesota has low SAT participation of 4% and high ACT participation rate of 95% in 2019. SAT is likely acceptable to the students. 
    - Minnesota has a ACT composite score of 21.4, higher than the median of 21.1, given the high ACT participation rate.
    - Minnesota also has the highest SAT score from 2017 to 2019. 
  
**Recommendations to improve SAT participation rates:**

1. Subsidies or fee waivers may be given to selected students. As the cost of the test decrease, there will be more students who will consider taking the test. Given the capacity of the students, they are likely to do well and will further encourage the younger students to consider SAT.
2. Partnering established agency, such as [Manhattan Review](https://www.manhattanreview.com/minneapolis-sat-prep-courses/), to conduct SAT preparatory courses to provide students the confident and support them in the switch from ACT to SAT. The course may be customised for Minnesota schools, highlighting key differences and benefits for taking SAT. 

**Limitation of data sets:**
    
1. Data sets consists of summarise data in the states. They do not include the number of students who took the respective tests. Hence, it is not possible to assess if the data points are skewed towards any biasness.
2. The analysis did not consider the demographics of the student population in the various states taking the tests, for example, access to education, family income etc. 



## Conclusion

The analysis showed that most of the states have either high SAT participation rate or high ACT participation rates. It is evident that most states adopt ACT. On the other hand, SAT participation rate has improved from 2017 to 2019, especially with the introduction of the new test format. The number of states with 100% SAT participation rate has doubled from 4 in 2017 to 8 in 2019. 

Many states (about 30% of the states in 2019) mandate ACT test, while only about 16% of the state mandate SAT test. The higher the participation rates in a either test usually the lower the test score. Also, the higher the participation in one test, the lower the participation rates in the other.

The project established a set of state selection requirements and shortlisted Minnesota for the College Board to consider investing resources to increase its participation rate. 