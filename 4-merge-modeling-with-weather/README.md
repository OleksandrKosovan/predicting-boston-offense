
# I. Merging offenses data with weather data


I founded weather data for Boston (Jul 2012 - Aug 2015). [Link:](https://www.kaggle.com/naveenpandianv/weather-data-boston-jul-2012-aug-2015)

Contains weather information for the City of Boston that was scraped from a weather website. 

So, weather data set have columns:
- 'Precipitation',
- 'Day',
- 'Month',
- 'year', 
- 'Temperature',
- 'Dewpoint',
- 'humidity', 
- 'wind'

I will merge it with crimes data set. Then i will fit models with it. 

**How i merged it?**

Crimes data set have columns - years, months, days. Weather data set have it too. I used this column for merging.

Yes. I will use weather information for each days. If it will be useful, i will found weather for each hours.

# II. Modeling for offnses code groups

[Jupyter Notebook - modeling](https://github.com/OleksandrKosovan/predicting-boston-offense/blob/master/4-merge-modeling-with-weather/2-w-modeling-offense-code-group.ipynb) :link:

My last the best result is **0.4725** (f1 score). I added new weather features. Then i got new not better result than it was. It is **0.4461**. So, data set with our features didn't improve models.

*Input data:*
- DAY_OF_WEEK, 
- DISTRICT, 
- HOUR, 
- Lat, 
- Long, 
- MONTH, 
- REPORTING_AREA, 
- Day, 
- Night, 
- ToNight, 
- ToDay, 
- precipitation, 
- temperature, 
- dewpoint, 
- humidity, 
- wind.

![alt text](https://image.ibb.co/cPgUBz/offen.png)

# III. Modeling for district

[Jupyter Notebook - modeling](https://github.com/OleksandrKosovan/predicting-boston-offense/blob/master/4-merge-modeling-with-weather/3-w-modeling-district.ipynb) :link:
 
New data set with weather features improved models. But it is no enough. We got result - **0.1746**. It is 0.01 better than it was. 

*Input data:* 
- DAY_OF_WEEK, 
- HOUR, 
- MONTH, 
- UCR_PART, 
- Day, 
- Night, 
- ToNight, 
- ToDay, 
- precipitation, 
- temperature, 
- dewpoint, 
- humidity, 
- wind.

Model |	F1
------|--------------
Decision Tree | 0.1441
Extra Tree | 0.1432
Random Forest | 0.1315
LGBM | 0.1746
BernoulliNB | 0.1428
KNeighbors | 0.1408
GaussianNB | 0.1622

# IV. Modeling for UCR psrt

[Jupyter Notebook - modeling](https://github.com/OleksandrKosovan/predicting-boston-offense/blob/master/4-merge-modeling-with-weather/4-w-modeling-ucr-part.ipynb) :link:

Results for this multi classification is better than others. Score is 0.1 better than it was latter. F1 score is **0.4838**.
And we have second good news. Some categories have good f1 score. For example, it is **0.7755** for 3st category and **0.7089** for 2nd category.

Model |	F1
------|---------------
Decision Tree | 0.3974
Extra Tree | 0.3806
Random Forest | 0.4145
LGBM | 0.4461
BernoulliNB | 0.3863
KNeighbors | 0.3768
GaussianNB	0.3458


### So, what am i going to do?

I want to clean and comment my Jupyter Notebooks. Then i will research category, which i predict. And i will found new data for merging. 

