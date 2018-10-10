# Boston offenses. Researching and predicting

# I. Business Proposal

![alt text](https://media.giphy.com/media/3o85xm0pDVY4EkKdFe/giphy.gif)

**How safe is Boston compared with other big cities around the United States?**

It ranked roughly in the middle. Boston was more violent than New York and Seattle, but less violent than Chicago and Las Vegas, according to numbers from the FBI, based on crimes committed in 2015. Nationally, Boston ranked 47 out of 79 cities with populations of 250,000 or more. [*Sourse*](https://www.northeastern.edu/thescope/2017/06/21/boston-crime-map-how-safe-is-your-neighborhood/)

**Can we prediction offenses (*time, location, probability*)?**

It is main question and task for me. I want to prediction time, location and probability for offenses. 

You can imagine it: we have prediction map with probability for each offenses groups.

![alt text](https://i0.wp.com/www.northeastern.edu/thescope/wp-content/uploads/2017/06/Crime-map.jpg?fit=2932%2C1048&ssl=1)

**What are possible roles?**

It will be useful for:
- Each human
- Government
- Police
- Business

And it can help reduce number of offenses. 


# II. Project content

![alt text](https://thumbs.gfycat.com/DearComfortableCub-small.gif)

1. Using Kaggle data. Offenses for 2015-2018 years. (*Visualization, modeling*)[Link](https://github.com/OleksandrKosovan/predicting-boston-offense/tree/master/1-Kaggle-data) :link:

2. Merging data. Offenses for 2012-2018 years. [Link](https://github.com/OleksandrKosovan/predicting-boston-offense/tree/master/2-marge_data) :link:

3. Researching and modeling with new data after merging. Offenses for 2012-2018 years. [Link](https://github.com/OleksandrKosovan/predicting-boston-offense/tree/master/3-research-modeling-with-new_data) :link:

4. Merging and modeling with weather data. Offenses for 2012-2015 years. [Link](https://github.com/OleksandrKosovan/predicting-boston-offense/tree/master/4-merge-modeling-with-weather) :link:

5. Parsing weather for 2012-2018 years. [Link](https://github.com/OleksandrKosovan/predicting-boston-offense/tree/master/6-modeling-with-weather-data) :link:

6. Modeling with weather data. Offenses for 2012-2018 years.[Link](https://github.com/OleksandrKosovan/predicting-boston-offense/tree/master/6-modeling-with-weather-data) :link:

7. [Adding data](https://github.com/OleksandrKosovan/predicting-boston-offense/tree/master/7-Adding-new-data) :link:

# III. The best machine learning results

![alt text](http://www.sixthcents.net/images/macbook.gif)

### Multi class classification

**1. Fitting with all data**

- Data:

NAME	| Format | Unique value |	Note
------|--------|--------------|------
YEAR |	int	| 2012-2018 |	-
MONTH |	int |	1-12 |	-
DAY |	int |	1-31 |	-
OCCURRED_ON_DATE |	datetime |	-	 | YYYY-MM-DD HH:MM:SS
DAY_OF_WEEK |	category |	Monday - Sunday |	-
HOUR |	int | 	0-23 |	-
DISTRICT |	categories	| 12 unique values |	"A district is a type of administrative division that, in some countries, is managed by local government." , What district the crime was reported in
Lat	| float | 	-	| Location latitude 
Long |	float	| -	| Location longitude
OFFENSE_CODE_GROUP |	categories |	20-23 unique values |	I used 10 groups. Internal categorization of (offense_description)
REPORTING_AREA	| int	| -	| RA number associated with the where the crime was reported from.
SHOOTING | boolean	| 0/1	| Offenses with shooting or without shooting
UCR_PART	| categories |	4 unique values |	The Uniform Crime Reports (UCR). Indicated a shooting took place.
Day	| boolean |	0/1	| Day or night
Night |	boolean| 	0/1	| Night or day
ToDay	| int	| - |	Number of hour to day
ToNight |	int	|-	| Number of hour to night
**WEATHER**			
temperatureMin	| float	-	
temperatureMax	| float	-	
temperatureDifference	| float	| -	| temperatureMax - temperatureMin
precipitation	| float	| -	
snow	|float |	-	
**New data**
clust_50 | int | 50 | K-means clusters for Location (Lat, Long)
clust_100 | int | 100 | K-means clusters for Location (Lat, Long)
clust_200 | int | 200 | K-means clusters for Location (Lat, Long)
Universities_colleges_distance_25 | float | - | Percentile for all distances (25%)
Universities_colleges_distance_min | float | - | Minimum distance some object near offenses location
Universities_colleges_number_near | int | - | Number of Universities & colleges, which is nearer than 3 km for offenses location
Public_schools_distance_25 | float | - | Percentile for all distances (25%)
Public_schools_distance_min | float | - | Minimum distance some object near offenses location
Public_schools_number_near | int | - | Number of Public schools, which is nearer than 3 km for offenses location
Non-Public_schools_distance_25 | float | - | Percentile for all distances (25%)
Non-Public_schools_distance_min | float | - | Minimum distance some object near offenses location
Non-Public_schools_number_near | int | - | Number of Non Public schools, which is nearer than 3 km for offenses location

- Results:

Model | F1 Score | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10
------|---------|----|---|---|---|---|---|---|---|---|---
**Random Forest** | 0.2829 | 0.331 | 0.42 | 0.22 | 0.179 | 0.223 | 0.123 | 0.134 | 0.519 | 0.175 | 0.324 

Number of class:
 `   
    'Motor Vehicle Accident Response':1, 
    'Larceny':2, 
    'Medical Assistance':3,
    'Simple Assault':4, 
    'Violations':5, 
    'Investigate Person':6, 
    'Vandalism':7,
    'Drug Violation':8, 
    'Larceny From Motor Vehicle':9, 
    'Towed':10
`
[Link](https://github.com/OleksandrKosovan/predicting-boston-offense/blob/master/9-machine-learning/1-0-total-data.ipynb) :link:



**2. Elimination some features**



Simular fitting, bu it is without *Location (Lat & Long)*

Model | F1 Score | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10
------|---------|----|---|---|---|---|---|---|---|---|---
**Random Forest** | 0.2856 | 0.331 | 0.416 | 0.228 | 0.186 | 0.2301 | 0.132 | 0.127 | 0.527 | 0.1805 | 0.321

[Link](https://github.com/OleksandrKosovan/predicting-boston-offense/blob/master/9-machine-learning/1-1-total-data.ipynb) :link:

**3. Select 2013-2015 | 2016-2018 years

Simular fitting, but first for 2013-2015 years

Model | F1 Score | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10
------|---------|----|---|---|---|---|---|---|---|---|---
**Random Forest** | 0.269 | 0.233 | 0.4039 | 0.2104 | 0.183 | 0.2694 | 0.121 | 0.1449 | 0.517 | 0.196 | 0.291

[Link](https://github.com/OleksandrKosovan/predicting-boston-offense/blob/master/9-machine-learning/2-select-years-13-14-15.ipynb) :link:

Simular fitting, but second for 2016-2018 years

Model | F1 Score | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10
------|---------|----|---|---|---|---|---|---|---|---|---
**Random Forest** |  0.3064 | 0.4005 | 0.393 | 0.2502 | 0.1355 | 0.1687 | 0.1628 | 0.1005 | 0.5673 | 0.1258 | 0.3451

[Link](https://github.com/OleksandrKosovan/predicting-boston-offense/blob/master/9-machine-learning/2-select-years-16-17-18.ipynb) :link:
 
**4. Fitting for three classes with the best F1 score

There are `Motor Vehicle Accident Response` & `Larceny` & `Drug Violation`

Model | F1 score | Motor Vehicle Accident Response | Larceny | Drug Violation
------|----------|---------------------------------|---------|---------------
Random Forest | 0.6657 | 0.6753 | 0.6661 | 0.6444

[Link](https://github.com/OleksandrKosovan/predicting-boston-offense/blob/master/9-machine-learning/3-three-groups.ipynb) :link:

**4. Fitting for three classes with the best F1 score. And selecing 2016-2018 years

Model | F1 score | Motor Vehicle Accident Response | Larceny | Drug Violation
------|----------|---------------------------------|---------|---------------
Random Forest | 0.6827 | 0.73338225 | 0.60283871 | 0.66832093

[Link](https://github.com/OleksandrKosovan/predicting-boston-offense/blob/master/9-machine-learning/4-three-groups-and-select%20year.ipynb) :link:


# IV. Other interesting results. Visualization

### Number of offenses for each years (2013-2017)

Number of offenses increased by  **16.05 %** from 2013 to 2017.

![alt text](https://image.ibb.co/fbkAMz/download.png)

### Comprasion. Crime with shooting VS total number of offenses. Hour

Bar chart for each hours. 

![alt text](https://image.ibb.co/icM38e/shooting_1.png)


### Comprasion. Crime with shooting VS total number of offenses. Day of week

Bar chart for each day of week. 


![alt text](https://image.ibb.co/b4YVMz/shooting_2.png)

### Comprasion. Crime with shooting VS total number of offenses. Month

Bar chart for each month. 

![alt text](https://image.ibb.co/fn271z/shooting_3.png)


### Comprasion. Crime with shooting VS total number of offenses. Day / Night

Bar chart for day/night. 


![alt text](https://image.ibb.co/n0eegz/shooting_4.png)

### Comprasion. Crime with shooting VS total number of offenses. Location

Scatter plot for location (Lat.Long). 


![alt text](https://image.ibb.co/noYSZK/crime_shooting.png)

### Comprasion. Crime with shooting VS Street Lights. Location

![alt text](https://image.ibb.co/bB9CJe/crime_shooting_location.png)


### Comprasion. Crime with drugs and Universities. Location

![alt text](https://image.ibb.co/g6PJrz/drug.png)
