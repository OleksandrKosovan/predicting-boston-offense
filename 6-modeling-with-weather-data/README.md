# I. Modeling - offense code groups - multi class classification

I fitted multi classification models for offense code groups.

Jupyter Notebook - [modeling](https://github.com/OleksandrKosovan/Boston-offenses-research-predict/blob/master/6-modeling-with-weather-data/1-modeling.ipynb) :link:

Groups (categories), which we predict:
- 'Other', 
- 'Motor Vehicle Accident Response', 
- 'Larceny',
- 'Medical Assistance', 
- 'Simple Assault',
- 'Violations',
- 'Investigate Person', 
- 'Vandalism',
- 'Drug Violation',
- 'Larceny From Motor Vehicle'
	
So, i got worse results, than we had.

Last the best result was - **0.4838** (LGBM, data for crime 2012-2015 years, with weather. You can see these results in table “model-results”- “w-offense”).

But the best result for these models is **0.2853** (LGBM) (1st)
	
Than i fitted models without category - “Other” (2nd). 	The best result - **0.2856** (LGBM)

After that i added new category - “Towed”. 	New the best result - **0.2797** (LGBM)

**Analytics**

So, we got results, which is worse than last time. I think, problem is overfitting for last modeling.

**What can we do?**

I have two hypothesis for it. We can use multi label classification, because some crimes can event in one time. We need to add new features.


# II. Preparation data for multi label classifiaction

I want to do multi label classification for my dataset. But my data is no preparation for it. My data is like it. There are some input data and column with our classes. 

Jupyter Notebook - [Link](https://github.com/OleksandrKosovan/Boston-offenses-research-predict/blob/master/6-modeling-with-weather-data/2-preparation-data-for-multi-label-classifiaction.ipynb) :link:

**I need data like it:**

![alt text](https://s3-ap-south-1.amazonaws.com/av-blog-media/wp-content/uploads/2017/08/25230858/Screen-Shot-2017-08-25-at-12.46.30-AM.png)

**I have data like it:**

![alt text](https://s3-ap-south-1.amazonaws.com/av-blog-media/wp-content/uploads/2017/08/25230915/Screen-Shot-2017-08-25-at-12.46.37-AM.png)

**SO, how did i preparation data?**

First, i selected columns, which i will use, and which can be identical. 
It is each columns, but without LOCATION.

After preparation i got next dataframe. 

Then i will fit models for multi label classification.

# III. Multi label classifiaction

Jupyter Notebook - [Link](https://github.com/OleksandrKosovan/Boston-offenses-research-predict/blob/master/6-modeling-with-weather-data/3-modeling-multi-labels.ipynb) :link:

I fitted models for multi label classification with my data. And i got some results. 

*I used 3 models:*

- Decision Tree
- Extra Tree
- Random Forest

Model | F1 score
------|----------
Decision Tree | 0.1886
Extra Tree | 0.1817
Random Forest | 0.0856

The best result is **0.1886** (Decision Tree).

So, multi label classification did not give better results than multi class classification. Main problem with bad score is not enough data. Then i want to select data which we add for our dataset.
