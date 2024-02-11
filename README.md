# Project-1-Group-2
Project-1-Group-2

Group members:
    Fabiano Santos
    Lewis Trenerry
    Liwei Jiang
    Simone Nagel
    
    
#### Project title: A snapshot of net overseas migration and housing prices in Australia between June 2013 - December 2021


#### Introduction
There has been discussion in the media about overseas migration fuelling property price increases. An article in the Australian Financial Review (Kehoe, 2024) proposes migration in Australia has materially influenced rising property prices. Conversely an article from The Guardian (Nicholas, 2023) suggests that there is no conclusive evidence on migration affecting the Australian housing market.  As a team we set out to support or reject these conflicting hypotheses.
This project examines net overseas migration and property prices in Australia using data from June 2013 - December 2021. Specifically, we examine whether and how property prices across Australia may be impacted by overseas net migration by analysing property price index in each state/territory.
The housing data and net overseas migration data were both downloaded from the Australian Bureau of Statistics website in CSV format. 
After numerous team discussions and preliminary research, we formulated the below research questions to begin collating and cleansing data, to then develop visualisations to better enable us to develop analytical insight.

#### Research questions:
1). What was the highest and lowest states/territories impacted by net overseas migration between Jun 2013- Dec 2021?
2). What was the highest and lowest states/territories impacted by housing price change between Jun 2013- Dec 2021?
3). Is there correlation between net overseas migration and the property pices index in each state/territory?


#### Data cleansing

The ABS separated the data for net overseas migration in two different CSV files, one for 'larger states' including NSW, VIC, QLD, and WA (Australian Bureau of Statistics, 2022a) and 'smaller states' including SA, TAS, NT, and ACT (Australian Bureau of Statistics, 2022b). The first task was to combine these two CSV files using the 'pd.merge' function into one dataframe, using the common variable of 'quarter'. The ABS data for residential property price index in capital cities (Australian Bureau of Statistics, 2022c) was also brought into its own data frame. 

The net overseas migration data spanned from Jun-13 - Jun-23, whilst the residential property price index in capital cities data spanned Dec-11 to Dec-21 when the ABS ceased production of this data. The team therefore decided to analyse the period Jun-13 - Dec-21 whereby we had data for each variable. We acknowledge this as a limitation of our research. In addition to net overseas migration data being recorded for each state/territory, whilst residential property price indexes are recorded for capital cities. This is another limitation of the data, but we decided to proceed as over two thirds of Australia’s population is centred in Australian Capital cities (Australian Bureau of Statistics, 2022d), hence we extrapolated that most overseas migrants would also reside in Australian capital cities.

The 'dropna' function was used to remove rows with no data. Research (Pandas, 2024) was conducted on how to remove rows of data not in the Jun-13 - Dec-21 timeframe. The 'str.match' function was used to remove non-date values, and then the quarter text was convert the Quarter column to datetime format ‘pd.to_datetime’ to enable filtering. This was then filtered for values less than or equal to Dec-21 for migration data, and greater than Jun-13 for property price index data. The ‘Quarter’ datetime format was then converted back to the original format (using ‘dt.strftime’ function) for cleaner visualisation. Furthermore, the property price index columns were reorganised, so that the city columns aligned with the corresponding states migration data.

Finally as the migration data frame is recorded in thousands (rounded) whilst the property price index data used a reference period of 2011-12 for all city indexes, the data was replicated in both cleaned data frames to show a relative percentage change (rounded to two decimal places) from the preceding quarter utilising the ‘pct_change’ function. This enabled further data analysis, allowing a comparison between the rate of change between each variable on a quarter-by-quarter basis.

## Based on the property data, what was the highest and lowest states/territories impacted by housing prices between 2013-2021?

To identify which state/territory has the highest and lowest housing price or price movements between June 2013 and December 2023, as reflected in the housing price for the capital cities, we generated the summary statistics as well as the total variation from the beginning to the end of the period. As shown below, the capital city that has the the highest price is undoubtedly Sydney while the housing price in Hobart increased the most during the period. The only city where the housing price actually decreased is Darwin. The housing price in the capital city would be expected to be largely in line with the trend in the state.

![Property Boxplot Plot](Screenshots/BoxPlotPropertyScreenshot.png)

To show the movements of housing price for each city, line charts are generated as below.

![Line Chart Property](Screenshots/LineChartPropertyScreenshot.png)

The housing price has, in general, presented increasing trend for 6 of the capital cities with Perth and Darwin presenting a declining trend. The dynamic changes of housing price in Melbourne and Hobart are also worth noting. In combination with the movements of net migration in these two cities, it seems that more people may have moved from Melbourne to Hobart, which in turn may have caused the increased housing price in Hobart and decreased housing price in Melbourne. The charts also suggest that Perth and Darwin are most affordable cities to own a residential property. 


#### Correlation between Migration and the Property Prices Index in each State/Territory


Until now, we have analysed the variables independently and which states and capitals have presented the highest and lowest impacts. 

But how do they interact with each other? Is there any correlation? Some people suggest that the increase in housing prices can be explained by the rise in migrants coming to Australia. Do we have data to support those allegations?

We can use the quarterly data from June 2013 to December 2021, comprising 35 measurements to investigate these questions.

By comparing the total net migration per state within that period with the property price index total variation in that same period, we have the following graph:

![Scatter Plot](Screenshots/ScatterPlotScreenshot.png)

The scatter plot above indicates that the results vary significantly from state to state. For instance, Tasmania and Northern Territory recorded the lowest net migration figures. Interestingly, these states differ in terms of the variation in the property price index. Tasmania had the highest positive variation, whereas the Northern Territory had the highest negative variation. 

Western Australia, Victoria and New South Wales followed a similar ascending line in the chart, but the Australian Capital Territory, South Australia, and Queensland presented random patterns.

The result is also inconclusive if we look at the numbers and calculate the correlation between these two variables per state.

At first glance, it may suggest a strong negative correlation between them. 

![Correlation Table](Screenshots/CorrelationScreenshot.PNG)

However, it is important to keep in mind that part of the data available refers to a period that was heavily affected by the COVID-19 pandemic, which can drastically influence the data.

![Correlation Table COVID](Screenshots/CorrelationCOVIDComparisonScreenshot.PNG)

Let’s make an exercise and limit the measurements to the period not affected by the pandemic. As a result, we observe that the results are higher in all states, moving from negative to positive indexes in some of them. Nevertheless, it is still insufficient to establish a significant correlation between the variables.

From a more visual perspective, it is clear from the line charts that these two indexes have entirely different and unrelated behaviours. 

![Line Chart - Migration](Screenshots/LineChartMigrationScreenshot.png)

![Line Chart - Vartiation](LineChartVariationPropertyIndexScreenshot.png)

# References

Australian Bureau of Statistics, (2022a), "Graph 5.1 Net overseas migration(a) - larger states(b) - year ending" [CSV file]. Retrieved from https://www.abs.gov.au/statistics/people/population/overseas-migration/latest-release#cite-window1

Australian Bureau of Statistics, (2022b), "Graph 5.2 Net overseas migration(a) - smaller states and territories(b) - year ending" [CSV file]. Retrieved from https://www.abs.gov.au/statistics/people/population/overseas-migration/latest-release#cite-window1

Australian Bureau of Statistics, (2022c), "Residential Property Price Indexes, capital cities" [CSV file]. Retrieved from https://www.abs.gov.au/statistics/economy/price-indexes-and-inflation/residential-property-price-indexes-eight-capital-cities/latest-release

Australian Bureau of Statistics. (2022d). Location Census. Australian Bureau of Statistics. https://www.abs.gov.au/statistics/people/people-and-communities/location-census/latest-release

Kehoe, J. (2024, January 19). Migration boosts house prices but not inflation. Australian Financial Review. https://www.afr.com/policy/economy/migration-boosts-house-prices-but-not-inflation-20240119-p5eyni#:~:text=Migration%20surges%20in%20Australia%20have,the%20International%20Monetary%20Fund%20suggests

Nicholas, J. (2023, December 12). Australia sees immigration data spike driving migration rate and housing prices. The Guardian. Retrieved from https://www.theguardian.com/news/datablog/2023/dec/12/australia-immigration-data-spike-migration-rate-housing-prices

Pandas, (2024), pandas.Series.str.match. pandas documentation.
Retrieved from https://pandas.pydata.org/docs/reference/api/pandas.Series.str.match.html

OpenAI. (2022). ChatGPT [Computer software]. 
Retrieved from https://openai.com/chatgpt
