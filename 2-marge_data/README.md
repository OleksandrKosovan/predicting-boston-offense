
# Merging data


### Which data we merged?

First, we used data from Kaggle, but source for it is [data.boston.gov](https://data.boston.gov/). :link:

Then i take two datasets:

Crime incident reports (*JULY 2012 - AUGUST 2015*) [Link](https://data.boston.gov/dataset/crime-incident-reports-july-2012-august-2015-source-legacy-system) :link:

> See [description...](https://data.boston.gov/dataset/crime-incident-reports-july-2012-august-2015-source-legacy-system/resource/b3b7d7f6-2582-45b1-a342-cc14eaa7d14a?view_id=cfdb7de2-e9be-4ec4-a187-3911cfc15ed1) :link:


Crime incident reports (*AUGUST 2015 - TO DATE*) [Link](https://data.boston.gov/dataset/crime-incident-reports-august-2015-to-date-source-new-system) :link:

> See [description...](https://data.boston.gov/dataset/crime-incident-reports-august-2015-to-date-source-new-system/resource/9c30453a-fefa-4fe0-b51a-5fc09b0f4655?view_id=380adcd5-c841-4320-a9fa-604e7a6a94f5) :link:

After that my goal was merge it. 

**Why do we need merge these data sets?**

We have used only second data for modeling and it has not given  good results. So, we need  to merge these data sets. Then i will test different ML models with new df.

**Which column i merged?**

- REPTDISTRICT - DISTRICT
- REPORTINGAREA - REPORTING_AREA
- FROMDATE - OCCURRED_ON_DATE
- Year - YEAR
- Month - MONTH
- DAY_WEEK - DAY_OF_WEEK
- UCRPART - UCR_PART
- Shooting - SHOOTING
- Location - Lat\Long
- MAIN_CRIMECODE - OFFENSE_CODE_GROUP

**Why did i select these columns?**

I had two main casuals for it. I used these values for modeling. I deleted columns, that don't exists in two data sets simultaneously.

*So, we got data for event crime from JULY 2012 to date.*
