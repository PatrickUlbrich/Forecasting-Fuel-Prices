# Forecasting Fuel Prices

The code and the analysis in this repository was used in a study project as part of my Master's Degree in Data Science. My final examination paper can be found in the file *tankerkoenig_analysis.pdf*. 

The file tankerkoenig.Rmd contains all code and analysis. The references.bib contains all literature references used in the analysis.

## Results

In this analysis price event change data for all German gas stations is filtered, aggregated by a daily median and an ETS as well as an ARIMA model is calculated. The simple methods of Mean, Naive and Drift are also analyzed as benchmarks. The Naive forecast has the lowest AICc (corrected Akaike Information Criterion).  It is also best or almost identical in terms of absolute performance metrics on the test set. For most practical intents and purposes daily fuel price changes follow a random walk so that there is no value to an end user to "wait for the next cheaper day" to come. The best forecast for the next price is the current price + a random change that is equally likely positive or negative.

Performance metrics used:
- MAE (Mean Absolute Error)
- RMSE (Root Mean Squared Error)
- MAPE (Mean Absolute Percentage Error)
- MASE (Mean Absolute Scaled Error)
- RMSSE (Root Mean Squared Scaled Error)


## Download the dataset

The dataset contains fuel prices for all German gas stations going back to June 2014 and is provided by: https://dev.azure.com/tankerkoenig/_git/tankerkoenig-data.
The data shows the event based changes of every single price change for the fuel types e5, e10 and diesel. The dataset is updated every day.

**Caution**: As of 20.08.2024 the complete dataset had a size of 94.4GB. It is possible to initially download the dataset via:

```git clone https://tankerkoenig@dev.azure.com/tankerkoenig/tankerkoenig-data/_git/tankerkoenig-data```

 The daily updates can then be pulled by a simple:

```git pull```

For additional dataset description please visit https://dev.azure.com/tankerkoenig/_git/tankerkoenig-data

This raw data is aggregated on a daily median basis in codeblock 7 *dataset-creation* and saved as a csv. The csv is also provided in this repo as *daily_focused_prices.csv*.


## Requirements

The tankerkoenig.Rmd requires R and the University-specific fhswf package to be knitted. A guide for downloading the required packages is provided here: https://bchwtz.github.io/bchwtz-stat/fhswf-package.html

The tankerkoenig.Rmd file also requires the following environment variables to be defined:

- **STATIONS_ROOT_DIR**: The file path of the stations.csv file from the dataset (example: *additional_path/tankerkoenig-data/stations/stations.csv*).

- **PRICES_ROOT_DIR**: The prices folder from the dataset (example: *additional_path/tankerkoenig-data/prices*)

- **DAILY_DATA_FILE_PATH**: Codeblock 7 *dataset-creation* calculates a daily median price time series for all three fuel types from the event data. The time series is saved as a csv file at this file path for later use.
