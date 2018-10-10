# I. Parsing

I have used weather data for 2012-1015 years.  But i have crime data for 2012-2018 years. So, i need get weather data for it.
I didn't found good weather data for this time. But i found useful website with information about weather for Boston. 

[Link:](https://www.usclimatedata.com/climate/boston/massachusetts/united-states/usma0046/2012/1) :link:


Then i want to get weather data from this website in csv format. I will use BeautifulSoup for parsing. 

Jupyter Notebook - parsing - [link](https://github.com/OleksandrKosovan/predicting-boston-offense/blob/master/5-weather-data/1-parsing-for-weather-data.ipynb) :link:

After that, i got weather data for 2012-2018 year (for each days). This dataset contain next column:

- 'date', 
- 'temperatureMin', 
- 'temperatureMax', 
- 'precipitation', 
- 'snow',
- 'year', 
- 'month', 
- 'day'

I am going to merge it with total crime data.

Jupyter Notebook - preparation data for merging - [link](https://github.com/OleksandrKosovan/predicting-boston-offense/blob/master/5-weather-data/2-preparation-weather-data-for-merging.ipynb) :link:

# II. Merging data & Features engineering

Jupyter Notebook - [Link](https://github.com/OleksandrKosovan/Boston-offenses-research-predict/blob/master/5-weather-data/3-merge-offenses-data-with-weather.ipynb) :link:

I merged crime and weather data. I used “year”, “month”, “day” for merging. It is weather data, which we got:
- Temperature min
- Temperature max
- Precipitation 
- Snow

**Features engineering **

I created new feature - *“temperature difference”*

`“temperature difference” = “temperature MAX” - “temperature MIN”`










