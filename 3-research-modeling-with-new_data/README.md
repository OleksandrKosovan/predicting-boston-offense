
# I.Feature engineering

*I created 4 new weakly relevant features.*
- Day
- Night
- ToNight
- ToDay

### 1. Day

Values: 0/1

> 1 - 418 241 - *DAY*

> 0 - 156 985 - *NIGHT*

![alt text](https://image.ibb.co/m9r4uK/day.png)

**How did i create this feature?**

I used information about Yearly Sun Graph for Boston. [Link](https://www.timeanddate.com/sun/usa/boston) :link:

![alt text](https://image.ibb.co/gjgyMz/day_night.png)

And i created array which i used for select of day or night crimes. 

`day_night_period = [
    [1,6,18],  
    [2,6,19], 
    [3,6,20], 
    [4,5,20],
    [5,5,21], 
    [6,4,21], 
    [7,5,21], 
    [8,5,21],
    [9,6,20], 
    [10,6,19], 
    [11,6,17],
    [12,7,17]
]`

> *Array description:* 0 - month / 1 - day start / 2 - night start


### 2. Night

Values: 0/1
> 0 - 418 241 - Day

> 1 - 156 985 - Night

![alt text](https://image.ibb.co/mPkfZK/night.png)

**How did i create this feature?**

*I did next simple steps:*

`(Day == 0) => Night = 1`

`(Day ==1) => Night = 0`


### 3.ToNight

It is feature, which shows number of hours to night.I used information about Yearly Sun Graph for Boston and i selected different values. Then i calculated it. 

![alt text](https://image.ibb.co/d5SV1z/tonight.png)

### 4.ToDay

It is feature, which shows number of hours to day. I used information about Yearly Sun Graph for Boston and i selected different values. Then i calculated it. 

![alt text](https://image.ibb.co/n77V1z/today.png)


# II. Modeling for offense code groups

Our **main goal** is answer on this question:

`“Is it possible to predict where or when a crime will be committed?”`

We need to test different combinations of data for answer.	I think, good result is more than **0.6-0.7** ([f1 score](http://scikit-learn.org/stable/modules/generated/sklearn.metrics.f1_score.html)).

I have used old data (*August 2015 - To Date*) for modeling. And it didn't get good results. But i merged different data sets and i got bigger information than i had (*July 2012 - To Date*). Then i fitted models with new data frame. First we analyzed  models for predicting offense code group. 

**Why did i chose it?**

I think, we can predict offence type, when we have information about location and datetime. So, our task is multi classification for 10 categories. 
- Other                          
- Motor Vehicle Accident Response
- Larceny
- Medical Assistance
- Simple Assault
- Violations
- Investigate Person
- Vandalism
- Drug Violation
- Larceny From Motor Vehicle

**About input data**

I use information about location and datetime. Other data is not good for this task. For example, OFFENSE_CODE contain information about value, which we predict.

*So, it is input data:*
- DISTRICT
- REPORTING_AREA
- MONTH
- DAY_OF_WEEK
- HOUR
- Lat
- Long
	
*My first results:*

OLD DATA - Crime Incident Reports (August 2015 - To Date)
NEW DATA - Crime Incident Reports (July 2012 - August 2015) + Crime Incident Reports (August 2015 - To Date)

When i used old data, my the best result was LGBM (f1 score = **0.2641**). Then i added two new features - Day and Night, and got new result -  LGBM (f1 score = **0.2642**). Good result is more than 0.6-0.7 (f1 score). So, it is not good results. After that, i increased old data. 

**Results after increased data:**

New data give for us new opportunities. Results are not good enough. The best result -  LGBM (f1 score = **0.2862**). 	When i added new featured - (Day, Night, ToDay, ToNight), i didn't get better result, than i had.

[Jupyter Notebook Link](https://github.com/OleksandrKosovan/predicting-boston-offense/blob/master/3-research-modeling-with-new_data/2-modeling-offense-crime-code.ipynb) :link:
	
![alt text](https://image.ibb.co/itbOMz/newresults.png)
    
So, the best result - LGBM (f1 score = **0.2862**).

**What will i do?**

I want to testing models for other output and input data. (District, UCR part). Then i will build models with information about location, datetime and weather.


# III. Modeling for district

Next my step was fit model for predict ‘District’. I used information about date, time and crime codes. So, our output data is “DISTRICT” (12 categories).

*And our input data:*
- OFFENSE_CODE
- MONTH
- DAY_OF_WEEK
- HOUR
- Day
- Night
	
When i used old data, i got not good results. The best f1 score - 0.1171 with Random Forest.We didn't get good result with new data too. F1 score is **0.1602** with LGBM.

[Jupyter Notebook Link](https://github.com/OleksandrKosovan/predicting-boston-offense/blob/master/3-research-modeling-with-new_data/3-modeling-district.ipynb) :link:


Model | F1 score
------|-----------
Decision Tree | 0.1558
ExtraTree | 0.1558
RandomForest | 0.1531
LGBM | **0.1602**
BernoulliNB | 0.1449
KNeighbors | 0.1316
GaussianNB | 0.152


# IV. Modeling for UCR parts

Predicting for “UCR part” is the most successful. 

**What is UCR?**

*The Uniform Crime Reports (UCR)* compiles official data on crime in the United States, published by the Federal Bureau of Investigation (FBI). UCR is "a nationwide, cooperative statistical effort of nearly 18,000 city, university and college, county, state, tribal, and federal law enforcement agencies voluntarily reporting data on crimes brought to their attention".

So, our output data is *UCR part* (3 categories/ 3 different parts).

**And input data:**

- DISTRICT
- REPORTING_AREA
- MONTH
- DAY_OF_WEEK
- HOUR
- Lat
- Long
	
**About our results**

[Jupyter Notebook Link](https://github.com/OleksandrKosovan/predicting-boston-offense/blob/master/3-research-modeling-with-new_data/4-modeling-UCR_PART.ipynb) :link:

The best result for old data is  **0.4338** with Random Forest model. It is better result than with other models. But it is not enough. Then i used new data and i got next result - **0.4714** with LGBM model.

When i added new features (Day, Night, ToDay and ToNight), i got new result - **0.4725** with LGBM model.

![alt text](https://image.ibb.co/bZ2Brz/ucr.png)

So, after that i want create comments for my code and clean Jupyter Notebooks. And i will fit models with new data (location,datetime, weather).

