# Project-1-Group-2
Project-1-Group-2

Group members:
    Simone Nagel
    Fabiano Santos
    Lewis Trenerry
    Liwei Jiang
    
    
#### Project title: A snapshot of net overseas migration and housing prices in Australia between June 2013 - December 2021


#### Research questions:

Based on the net overseas migration data, what was the highest and lowest states/territories impacted by migration between 2013-2021?
Based on the housing data, what was the highewst and lowest states/territories impacted by housing prices between 2013-2021?
Is there any correlation between net overseas migration and housing prices?

#### How we worked as a team


This project examines the factors that may impact on housing prices in Australia using the data from June 2013 - December 2021. Specifically, we examine whether and how housing prices across Australia may be impacted by the overseas net migration by analysing property price index in each state/territory.

Our initial sample includes observations for the quartely housing price indices in eight Australia capital cities in during the period of June 2013 to December 2021. 

The housing data and net overseas migration data were both downloaded from the Australian Bureau of Statistics website in CSV format. 

*The table below summarise the original data and the final data after merging all the datasets*

Before conducting our analyses to answer the project questions, we conduct the following data cleasing and data exploration.

# Data cleansing

The ABS seperated the data for net overseas migration in two different CSV files, one for 'larger states' including NSW, VIC, QLD, and WA (Australian Bureau of Statistics, 2022a) and 'smaller states' including SA, TAS, NT, and ACT (Australian Bureau of Statistics, 2022b). The first task was to combine these two CSV files using the 'pd.merge' function into one dataframe, using the common variable of 'quarter'. The ABS data for residential property price index in capital cities (Australian Bureau of Statistics, 2022c) was also brought into the jupyter lab workbook in its own dataframe. 

As the net overseas migration data spanned from Jun-13 - Jun-23, whilst the residential property price index in capital cities data spanned Dec-11 to Dec-21, the team made a decision to analyse the period Jun-13 - Dec-21 whereby we had data for each variable. We acknowledge this as a limitation of our research, in addition to Net overaseas migration data being recorded for each state/territory, whilst Residential Property Price Indexes is recorded for just capital cities.

The 'dropna' function was used to rows with no data. Research (Pandas, 2024) was conducted on how to remove rows of data not in the Jun-13 - Dec-21 timeframe. The 'str.match' function was used to convert the Quarter column to datetime format to enable filtering. This was then filtered for values less than or equal to Dec-21 for migration data, and greater than Jun-13 for property price index data. The Quater datatime format was then converted back to the original format for cleaner visualisation. Furthermore the property price index columns were reorganised, so that the city columns aligned with the corresponding states migration data.

Finally as the migration data frame is recorded in thousands (rounded) whilst the property price index data used a reference period of 2011-12 for all city indexes, the data was replicated in both cleaned data frames to show a relative percentage change (rounded to two decimal places) from the preceeding quarter. This enabled further data analysis, allowing a comparison between the rate of change between each variable on a quarter by quarter basis.



## Calculated quartiles for all the variables of our primary interests, the housing prices, the net overseas migration, the number of population, and the interest rates, and created box plots to identify any potential outliers.


# Sort the final dataset to identify the capital cities with the highest and lowest house prices.


# Generated "Summary Statistics" as shown in the Table below.


# Created bar charts to show


# Created line plots and scatter plots to examine the relatioships between the housing price indices and the factors that may impact on the housing prices.


# Finally, we calculated the correlation coefficients and linear regression models between housing price indices and the three factors respectively. We also plot the linear regression models on top of the previous scatter plots.


As shown in the plots x, y, z, the correlation coefficient on the variable inflation rate is, p-value = , suggesting the higher the inflation rate, the lower the housing prices in general......(an expectation).....
!['my image'](images/img1.jpg)


# References
[https://www.abs.gov.au/statistics/people/population/overseas-migration/2022-23-financial-year#data-downloads]
Australian Bureau of StatisticsAustralian Bureau of Statistics
Overseas Migration, 2022-23 financial year
Statistics on Australia's international migration, by state and territory, country of birth, visa, age and sex. (60 kB)

Australian Bureau of Statistics, (2022a), "Graph 5.1 Net overseas migration(a) - larger states(b) - year ending" [CSV file]. Retrieved from https://www.abs.gov.au/statistics/people/population/overseas-migration/latest-release#cite-window1

Australian Bureau of Statistics, (2022b), "Graph 5.2 Net overseas migration(a) - smaller states and territories(b) - year ending" [CSV file]. Retrieved from https://www.abs.gov.au/statistics/people/population/overseas-migration/latest-release#cite-window1

Australian Bureau of Statistics, (2022c), "Residential Property Price Indexes, capital cities" [CSV file]. Retrieved from https://www.abs.gov.au/statistics/economy/price-indexes-and-inflation/residential-property-price-indexes-eight-capital-cities/latest-release

Pandas, (2024), pandas.Series.str.match. pandas documentation.
Retrieved from https://pandas.pydata.org/docs/reference/api/pandas.Series.str.match.html