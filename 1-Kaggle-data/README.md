# Kaggle kernel. Boston offenses data

## **I.** About data :cop:

You can found this data on Kaggle. 
**Link:** [Kaggle](https://www.kaggle.com/ankkur13/boston-crime-data) :link:

This is a dataset containing records from the new crime incident report system, which includes a reduced set of fields focused on capturing the type of incident as well as when and where it occurred.

*This dataset has 2,60,760 rows and 17 columns.* More information about data [**in my JN**](https://github.com/OleksandrKosovan/Boston-offenses-research-predict/blob/master/1-Kaggle-data/1-research-for-each-column.ipynb) :link:

## **II.** Inspiration / First hypothesis and questions :shipit:

1. How has crime changed over the years?
2. Is it possible to predict where or when a crime will be committed?
3. Which areas of the city have evolved over this time span?
4. In which area most crimes are committed?

## **III.** Visualization  :chart_with_downwards_trend:

I built bar charts and scatter plot  for each useful columns. You can see it in my Kaggle Kernel. 
[**Link**](https://github.com/OleksandrKosovan/Boston-offenses-research-predict/blob/master/1-Kaggle-data/2-visualization-for-each-column.ipynb) :link:

## **IV.** Modeling :boom:

:one: For offense code groups

:two: For district

:three: For UCR part

:four: Clustering

### IV.1. Modeling for offense code groups

**Why i select it for predict?**

This column don't have many unique values. And, i think, it will be useful for predict. 

*My hypothesis* is: 
`when we know information about location, district and date time, we can predict some offense groups.`

Then i selected groups with many offenses. It is 12 groups (value_counts > 10k).

So, i built multi classification models for next category:

- Motor Vehicle Accident Response
- Larceny
- Medical Assistance
- Investigate Person
- Other
- Drug Violation
- Simple Assault
- Vandalism
- Verbal Disputes
- Towed
- Investigate Property
- Larceny From Motor Vehicle

**About input data**

I used next values for modeling: 

- DISTRICT, 
- REPORTING_AREA, 
- MONTH, 
- DAY_OF_WEEK, 
- HOUR, 
- Lat, 
- Long,  
- OFFENSE_CODE_GROUP, 
- Day, 
- Night.

I didn't use other values, because it contains information about offence code groups or other columns is hard for preparation and difficult for use.

After that i preparation and splitted data.

I got some results. [(F1 score)](http://scikit-learn.org/stable/modules/generated/sklearn.metrics.f1_score.html)

![alt text](https://image.ibb.co/kYuRPK/screen.png)

*The best result*:

:muscle: LGBM. F1 score = **0.26421**

Our goal is getting 0.7 f1 score. I need to get better result for it. 


### IV.2. Modeling for district

**Why i select it for predict?**

District have 12 unique values and it is enough for multi classification. My hypothesis: Some district have dependence with other values.

**About input data:**

I use it for modeling: 

- OFFENSE_CODE, 
- DISTRICT, 
- MONTH, 
- DAY_OF_WEEK, 
- HOUR, 
- Day, 
- Night.

Then i preparation and splitted data. After that i got some results. 

 [(F1 score)](http://scikit-learn.org/stable/modules/generated/sklearn.metrics.f1_score.html)

![alt text](https://image.ibb.co/bOdpBz/screen_district.png)

*My the best result* is: 

:muscle: Decision Tree. F1 score = **0.1144**

But it is not our goal. It is not enough.

### IV.3. Modeling for UCR part

**Why i select it for predict?**

UCR (Uniform Crime Reports) have 4 parts, but i used 3 parts for modeling. 

*My hypothesis*: `Some location district and time have dependence with UCR parts. `

**About input data:**

I used it for modeling: 
- DISTRICT, 
- REPORTING_AREA, 
- MONTH, 
- DAY_OF_WEEK, 
- HOUR,
- LATITUDE,
- LONGITUDE

Then i got results. 

![alt text](https://image.ibb.co/bMRbrz/screen_ucr.png)

*The best result:*

:muscle: Random Forest. F1 score = **0.4338**
 
It is better result than result for other models. But i want get f1 score - 0.7

### IV.4. Clustering

I used [K Means](http://scikit-learn.org/stable/modules/generated/sklearn.cluster.KMeans.html) for clustering. 
First, i clustered location (lat and long). And i got next clusters. For 2 / 5 clusters.

**For example, 10 clusters visualization:**

![alt text](https://image.ibb.co/mx9RPK/clusters_10.png)

Then i added other values for it. Location and offense code.

**Clustering for location and OFFENSE_CODE**

![alt text](https://image.ibb.co/dFXkJe/clust_different.png)

It is interest result, because clusters are not district. Clusters are different streets. For location and months. Result is similar with last. 

## V. Conclusion for modeling :eight_spoked_asterisk:

Jupiter Notebook with modeling - [**LINK**](https://github.com/OleksandrKosovan/Boston-offenses-research-predict/blob/master/1-Kaggle-data/3-Boston-offenses-research-visualization-modeling.ipynb) :link:

Our first goal is get result - f1 score = 0.7. But models didn't have it. I think, problem was not enough data.  

So, my next steps are data engineering and data merging. 

## VI. Kaggle kernel :pushpin:

Finish i created Kaggle Kernel - [**LINK**](https://www.kaggle.com/kosovanolexandr/crimes-in-boston-multiclass-clustering) :link:

![alt text](https://image.ibb.co/h1LY4K/kaggle.png)
