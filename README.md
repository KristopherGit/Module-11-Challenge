# <b> Module-11-Challenge </b>

## <b> Forecasting Net Prophet </b>

## --------

## Overview

The objective of this Google Colab program is to perform a financial analysis on e-commerce company MercadoLibre. The purpose of the main body of the program is in fact to see if predictions in search traffic can be found, and if so, be a proxy to successfully trade the underlying stock.

## Features

The main tasks outlined in this project will include:

1.) Installing and importing the required libraries and dependencies including Pystan, (Facebook) Prophet, hvPlot, Holoviews, datetime, and Matplotlib.  
<br>
2.) Step 1: Finding patterns in the hourly google search traffic that may be of use. Essentially, one of the main sub-tasks of the assignment/program is to see if Google search traffic has any link/correlation to financial events at the company. Or is the search traffic data just representative of random noise. The data here is first read from a locally sourced file, put into a Panda's DataFrame. Afterwards the data is then sliced and analyzed for the month of May 2020 (coinciding with the release of MercadoLibre's quarterly financial results). HvPlots is utilized to visually represent the results. The data set is also used to calculate the total search traffic for the month and then compared to the monthly median across all months. (See Figure 1 & 2)
<br>
<br>
3.) Step 2: Next, hourly search traffic data was isolated and analyzed, per marketing department instructions. The goal was to predict interest in the company & platform at any time of day. The theory being, that they can more efficiently advertise and get a higher ROI from their marketing budget deficit if they can pinpoint the optimal advertising windows. The is completed by grouping the hourly search data and plotting the average traffic by the day of the week. This was done by compartmentalizing search traffic volume into indexed 'hours' [index.hour] and indexed 'days of the week' [index.dayofweek] as separate variable lists. Using hvPlot, they were plotted against one another in order to form a heatmap that compared search traffic during each day of the week as a function of hours of the day. Additionally, search traffic trends were found to be in an increasing uptrend through the last quarter of the year prior to Christmas, accompanied with a sharp drop afterwards. Lulls in traffic volume appear to occur right after Christmas, and during week 34 of the year. (See Figure 3, 4 & 5)
<br>
<br>
4.) Step 3: Afterwards, the relationship between search data volume and the company is analyzed to check for correlation. Stock price data is read in using read_csv again and the stock price data is plotted. (See Figure 6). The stock price data and search data (dataframe for Google Trends created earlier) is then concatenated to a single dataframe. The time series indexing of this dataframe was then sliced between 2020-01 and 2020-06 (in order to analyze the first half of the year during and after the initial onslaught of the COVID-19 pandemic to see how e-commerce companies adapted & responded to the evolving market environment).
<br>
<br>
5.) .
<br>
<br>
6.) .
<br>
<br>
7.) Again, the elbow-curve derivation is used to determine the best value of k-means for the 3-component pca dataframe created above. Again, the relationship to the inertia values of the pca dataframe (as a function of each k-means value) are plotted for visual analysis. (See Figure 4).
<br>
<br>
8.) Finally, similarly as before, the original cryptocurrencies (using pca data reduction, this time) are scatter plotted using hvplot and clustered in groups according to the optimal k-means determined value using pca components. (See Figure 5).

## Data Analysis Results and Observations

### <u>MercadoLibre - Google Search Trend data for the month of May 2020l</u>

<br>

<p align= "center" width="175">
    <img width= "50%" src="MercadoLibre_May2020.png">
</p>
<i>Figure 1. MercadoLibre Google Search Trend data for the month of May 2020.</i>

<br>

### <u>MercadoLibre - Monthly Median Search Traffic Across All Months</u>

<br>

<p align= "center" width="175">
    <img width= "50%" src="MercadoLibre_ Monthly_Median_Search_Traffic_Across_All_Months.png">
</p>
<i>Figure 2. The monthly median search traffic across all months is calculated by creating a dataframe whereby group indexing using the mean monthly values is calculated view pandas. Here, we can see that the search traffic did in fact increase during the month that MercadoLibre released its financial results - and appears to have in fact broken the decreasing trend of the past 3 years (leading up to and after May, 2020).</i>

<br>

### <u>MercadoLibre - Average Traffic By Day of the Week</u>

<br>

<p align= "center" width="50">
    <img width= "50%" src="MercadoLibre_Average_Traffic_By_Day_of_the_Week.png">
</p>
<i>Figure 3. MercadoLibre search traffic displaying maximum search traffic volume during Tuesday's, followed by Wednesday in a decreasing trend as the week progresses.</i>

<br>

### <u>MercadoLibre - Hour of Day vs Day of the Week Search Traffic Volume</u>

<br>

<p align= "center" width="175">
    <img width= "50%" src="MercadoLibre_Hour_of_Day.png">
</p>
<i>Figure 4. Hour of the day vs day of the week search traffic volume appears to indicate that Monday/Tuesday around 23:00hr-01:00hr are the busiest. However, when taking into consideration & converting the Seattle, WA based nomial UTC timestamp, this translates to an hourly shift around 9pm local Uruguay, Montevideo time (9pm local GMT-3 time, Monday). This makes more sense as customers/consumers are more likely to be shopping in the later hours of the evening on Monday, followed by Tuesday night. See below for a more detailed explanation on the local time shift rationale.</i>

<br>

### <u>MercadoLibre - Average Search Traffic By Week of the Year</u>

<br>

<p align= "center" width="175">
    <img width= "50%" src="MercadoLibre_Average_Volume_Week_Year.png">
</p>
<i>Figure 5. .</i>

<br>
<br>

<br>

### <u>MercadoLibre - Hourly Closing Stock Price</u>

<br>

<p align= "center" width="175">
    <img width= "50%" src="MercadoLibre_Hourly_Close_Price.png">
</p>
<i>Figure 6. .</i>

<br>
<br>

## Accompanying File(s)

\*Note: Refer to the crypto_market_data.csv file located within the applicable Resources folder for raw .csv data.

## Running the Project

Running the project can be accomplished by accessing the https://github.com/KristopherGit/Module-11-Challenge.git Git Repository and running each section sequentially.

## Dependencies

No other outside resources are required to run the project except a python engine / python program and the following imported libraries and modules:

(Running in Google Colab Notebook):
!pip install pystan
!pip install prophet
!pip install hvplot --upgrade
!pip install holoviews
!pip install matplotlib --upgrade

import pandas as pd
import holoviews as hv
from prophet import Prophet
import hvplot.pandas
import datetime as dt
%matplotlib inline

from pandas.io.formats.style import Axis
import matplotlib.dates as md
import matplotlib.pyplot as plt
import matplotlib.ticker as mticker
from matplotlib.dates import DateFormatter
import matplotlib.dates as mdates

## Contributors

C Ringwood
