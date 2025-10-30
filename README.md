# The-Impact-of-Weather-Conditions-on-Traffic-Congestion-in-Istanbul

Motivation :

Traffic congestion is one of the most pressing urban issues in Istanbul, causing lost time, increased fuel consumption, and economic inefficiency.
This project aims to analyze how weather conditions (temperature, rainfall, wind, and humidity) affect traffic congestion levels across Istanbul.
Understanding these relationships can help urban planners and transportation authorities improve mobility strategies, reduce delays, and enhance city life quality.

Data Sources:

1- Istanbul Traffic Index: https://www.kaggle.com/datasets/leonardo00/istanbul-traffic-index : This dataset provides the dependent variable — traffic congestion index.

Istanbul Traffic Index Content:
Minute-by-minute traffic congestion index values for Istanbul
Contains timestamp and congestion metrics for different periods of the day
Measures overall city-level traffic intensity


2-Istanbul Weather Forecast Logs 2020–2025 : https://www.kaggle.com/datasets/msacar/istanbul-weather-forecast-logs-dataset-2020-25  : This dataset serves as enrichment data, allowing the analysis of how weather variations influence the traffic index. Both datasets will be merged using the datetime field.

Istanbul Weather Forecast Logs 2020–2025 Content:
Daily and hourly weather data from Istanbul (2020–2025)
Includes temperature (°C), rainfall (mm), humidity (%), and wind speed (km/h
Collected from meteorological stations and forecast systems

 
Research Questions:
Does rainfall significantly increase traffic congestion in Istanbul?
How do temperature and wind speed affect congestion levels?
Are there seasonal or time-based patterns in the relationship between weather and traffic?

Hypotheses:
H0 (Null Hypothesis): Weather variables (rain, wind, temperature) have no significant impact on traffic congestion.
H1 (Alternative Hypothesis): Weather variables have a statistically significant effect on traffic congestion.

 Methodology
1. Data Cleaning
Converting  date and time fields to datetime format
Handle missing or duplicated values
Aggregate data to hourly averages for consistency

2. Data Integration
Merge the two datasets using datetime
Create derived features such as is_rainy, is_peak_hour, season, and weekday

3. Exploratory Data Analysis (EDA)
Distribution of congestion levels by day, hour, and weather type
Correlation heatmap between weather and congestion
Boxplots and time-series plots (rainfall vs. congestion index)

4. Hypothesis Testing
t-test:Compare mean congestion between rainy and non-rainy periods
ANOVA:Examine seasonal differences in traffic congestion
Correlation: Evaluate relationships between weather metrics and traffic index

5. Visualization
Time-series plots of weather vs. congestion
Heatmaps showing correlation strength
Boxplots of congestion by weather conditions


Expected Results:
Rainfall and low temperatures are likely to correlate with higher congestion levels.
Peak-hour congestion increases more sharply on rainy days.
Wind and humidity may have weaker or indirect effects.

Limitations:
The traffic dataset is aggregated at a city level, not by district or street.
Weather data may come from one station, not accounting for micro-climate variations.
The analysis demonstrates correlation, not causation.

My Project Timeline :
Date	Task
Oct 31	Submit project proposal
Nov 28	Complete data collection, cleaning, and EDA with hypothesis testing
Jan 02	Apply machine learning methods (optional regression model)
Jan 09	Final submission (report + visuals + code)

Tools and Libraries
Python Libraries: pandas, numpy, matplotlib, statsmodels, 
Platform:  Google Colab



Ethical Integrity:
All datasets are publicly available from Kaggle.

