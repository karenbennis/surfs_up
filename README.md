# surfs_up
The following repository includes analysis of weather data in Oahu for the purpose of convincing investors to back a surf/ice cream shop ("surfs_up"). Investors have requested this analysis so they can be reassured that business will not be affected adversely by weather.

## Project Overview
To make an informed decision to back surfs_up, a surf and ice cream shop with a proposed location of Oahu, investors requested weather analysis.

Initially, investors were interested in seasonal variation in precipitation data. 

Investors requested that the analysis be completed on data in June and December so they could gain an understanding of seasonal variation in weather patterns.

Specifically, investors had expressed that they would feel comfortable investing in surfs_up, if the proposed location had an ideal amount of rain, such that everything is green but not too much rain such that people don't want to surf or eat ice cream. If temperatures are too low, people won't want to surf or eat ice cream, regardless of rain; therefore, the research team made the up-front decision of providing analysis on temperature observations as well.

The methodology, results, and analysis are described in the *Summary* section. 

## Resources
Data Source: hawaii.sqlite
Database: SQLite 3.31
Languages: Python 3.7.6
Software: Jupyter Lab 1.2.6, SQLAlchemy 1.3


## Summary
### Methodology
The following steps were followed to complete the analysis on the weather data:

1. Use extract function from sqlalchemy to return precipitation data for a specific month (June/December) specified as an integer between 1-12.
2. Create an empty list to store results of ORM query.
3. Perform a sqlite query to retrieve precipitation in June/December across all the stations and years.
4. Save the query results as a Pandas DataFrame.
5. Use Pandas .describe() to return statistical analysis.

### Results
#### Precipitation
The statistical analysis for precipitation in the months of June and December is summarized in the table below.

|     | June | December |
------|------|----------|
|Count| 1574| 1405 |
|Mean| 0.14'' | 0.22'' |
|Standard Deviation| 0.34'' | 0.54'' |
|Min| 0.00'' | 0.00'' |
|Lower Quartile | 0.00'' | 0.00'' |
|Median| 0.02'' | 0.03'' |
|Upper Quartile| 0.12'' | 0.15'' |
|IQR | 0.10'' | 0.12'' |
|Max| 4.43'' | 6.42'' |

The analysis of Oahu daily precipitation volume in June and December for the years 2010 to 2017 shows the following:
* On average, the daily precipitation volume is lower in June compared with December (a difference of 0.08'').
* The median daily precipitation volume is lower in June compared with December (a difference of 0.01'').
* The December precipitation data has a wider spread by comparison with that of June (i.e. standard deviation is larger by 0.20'' in December compared with June).

In both June and December, the mean precipitation seems influenced by outliers. This is based on the notion that any value greater than Upper Quartile + 1.5 * IQR would be considered an outlier. This means that values in June which are greater than 0.27'' are outliers; and values in December that are greater than 0.33''.  It is possible that in both June and December respectively, there were only a few if not less outliers.

Overall, based on this initial inspection it seems that the following are likely conclusions:
* There is generally more rainfall during December compared with June
* Generally, there is little rainfall throughout the month in the case of June and December, regardless of differences between the two months
* There is at least one day in each month where significant rainfall is observed, and these are considered outliers.
* The standard deviation is considerably larger for the December precipitation data compared with that of June, which suggests that December precipitation is less predictable than June precipitation.

After analyzing the precipitation data, it was determined that precipitation in Oahu will not to play a significant role in influencing the business decision of whether or not to set up a surf and ice cream shop in Oahu. To make a more informed decision, temperature observations must be considered.

#### Temperature Observations
The temperature observations statistical analysis for the months of June and December is summarized in the following table:

|     | June | December |
------|------|----------|
|Count| 1700 | 1517 |
|Mean| 74.94° | 71.04° |
|Standard Deviation| 3.26° | 3.75° |
|Min| 64.0° | 56.0° |
|Lower Quartile | 73.0° | 69.0° |
|Median| 75.0° | 71.0° |
|Upper Quartile| 77.0° | 74.0° |
|IQR | 4.0° | 5.0° |
|Max| 85.0° | 83.0° |

The analysis of Oahu daily temperature in June and December for the years 2010 to 2017 shows the following:
* On average, the daily temperature is lower in December compared with June (a difference of 3.90°).
* The median daily temperature is lower in December compared with June (a difference of 4.0°).
* The December temperature data has a wider spread by comparison with that of June (i.e. standard deviation is larger by 0.49° in December compared with June).

In both June and December, there are outliers. This is based on the notion that any value less than Lower Quartile - 1.5* IQR and any value greater than Upper Quartile + 1.5 * IQR would be considered an outlier. Outliers are therefore values outside the following ranges:
* June: 67° - 83°
* December: 61.5° - 81.5°

Simply looking at the Min/Max temperature values for June and December shows that these values are all outliers. They are not drastically outside of the range; however, they should be noted as outliers. Given that these data points do not fall drastically out of range, and that Min/Max outlier datapoints effectively cancel one another out, the mean was not influenced by them, as evidenced by the fact that the median temperature is almost identical to the mean temperature in both June and December, respectively.

Overall, based on this initial inspection it seems that the following are likely conclusions:
* There are generally higher temperatures observed during June compared with December.
* The difference in temperature overall is not so significant that the temperature would be too cold for surfing or ice cream in December.
* The standard deviation is considerably larger for the December temperature data compared with that of June, which suggests that December temperature is less predictable than June temperature. The wider implication is that there would be more days in December where temperatures may be low enough that people would not want to surf or eat ice cream, but there are plenty of days in December where people would want to surf and eat ice cream.


### Recommendations for further analysis
While everyone can agree that weather is a factor which should factor into the decision of whether or not to invest in surfs_up, it follows that weather should not be the only consideration in such a big decision.

In order to provide the investors with the most complete analysis possible, the following recommendations are being made:

* Analysis of the precipitation patterns and temperature patterns for the other ten months of the year
    * Looking at data from only 2 months does not provide the most complete analysis that is possible. Analyzing data from all 12 months will provide a more complete picture which will better inform monthly / yearly revenue projections.
    * It is also recommended to produce line plots to visualize the data over time.
* Market research and analysis to determine which factors consumers would consider (beyond weather) for visiting the surf and ice cream shop.
    * After determination of other factors, analysis on those would need to be taken into account.
    * For example, if market research determined that people would want to see merchandise sold in the shop, this might be something to consider in terms of feasibility / return on investment.
* Analysis of competitors in Oahu to determine whether or not there would be enough demand for another surf and ice cream shop.
    * It is important to determine if the market can actually support another business offering the same goods.
    * For example, if there is a surf and ice cream shop which has a cult following, it may not be wise to compete with such an established institution if there is no reason to believe that the offerings in surfs_up would be unique or better by comparison with the already established business.
* Feasability analysis and return on investment projections (after analysis is completed on other factors) to determine whether or not this investment is indeed worthwhile.
