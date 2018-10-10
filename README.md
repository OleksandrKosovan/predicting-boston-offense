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

- Abou data: [Link](d) :limk:

NAME	| Format | Unique value |	Note
------|--------|--------------|------
YEAR |	int	| 2012-2018 |	-
MONTH |	int |	1-12 |	-
DAY |	int |	1-31 |	-
OCCURRED_ON_DATE |	datetime |	-	 | YYYY-MM-DD HH:MM:SS
DAY_OF_WEEK |	category |	Monday - Sunday |	-
HOUR |	int | 	0-23 |	-
DISTRICT |	categories	12 unique values |	"A district is a type of administrative division that, in some countries, is managed by local government."
Lat	| float | 	-	| Location latitude 
Long |	float	| -	| Location longitude
OFFENSE_CODE_GROUP |	categories |	20-23 unique values |	I used 10 groups
REPORTING_AREA	| int	| -	| Codes for reporting areas
SHOOTING | boolean	| 0/1	| Offenses with shooting or without shooting
UCR_PART	| categories |	4 unique values |	The Uniform Crime Reports (UCR)
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



- Results





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
