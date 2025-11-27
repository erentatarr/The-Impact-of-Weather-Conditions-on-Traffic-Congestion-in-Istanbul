# The-Impact-of-Weather-Conditions-on-Traffic-Congestion-in-Istanbul

**Motivation** :
Traffic congestion is one of the most pressing urban issues in Istanbul, causing lost time, increased fuel consumption, and economic inefficiency.
This project aims to analyze how weather conditions (temperature, rainfall, wind, and humidity) affect traffic congestion levels across Istanbul.
Understanding these relationships can help urban planners and transportation authorities improve mobility strategies, reduce delays, and enhance city life quality.

**Data Sources**:

1- **Istanbul Traffic Index**: https://www.kaggle.com/datasets/leonardo00/istanbul-traffic-index : This dataset provides the dependent variable — traffic congestion index.

**Istanbul Traffic Index Content:**
Minute-by-minute traffic congestion index values for Istanbul
Contains timestamp and congestion metrics for different periods of the day
Measures overall city-level traffic intensity


2-**Istanbul Weather Forecast Logs 2020–2025**: https://www.kaggle.com/datasets/msacar/istanbul-weather-forecast-logs-dataset-2020-25  : This dataset serves as enrichment data, allowing the analysis of how weather variations influence the traffic index. Both datasets will be merged using the datetime field.

**Istanbul Weather Forecast Logs 2020–2025 Content:**
Daily and hourly weather data from Istanbul (2020–2025)
Includes temperature (°C), rainfall (mm), humidity (%), and wind speed (km/h
Collected from meteorological stations and forecast systems

 
**Research Questions:**
1-Does rainfall intensity (none, light, moderate, heavy) significantly affect traffic congestion levels in Istanbul?
2-Does rainfall intensity impact traffic congestion differently on the Asian and European sides of the city?
3-Do other daily weather variables (temperature, wind speed, pressure) influence daily congestion levels?


**Hypotheses:**

**1-Main Hypothesis**

H0: Rainfall intensity has no significant effect on traffic congestion in Istanbul.
H1: Rainfall intensity has a significant effect on traffic congestion in Istanbul.

**2-Side Hypothesis 1 – Asian vs European Side**

H0: Rainfall intensity affects traffic congestion equally on the Asian and European sides.
H1: Rainfall intensity affects traffic congestion differently on the Asian and European sides.

3-**Additional Hypothesis**:

H0: Other daily weather factors (temperature, wind speed, pressure) do not influence traffic congestion.
H1: Other daily weather factors significantly influence traffic congestion.

**Methodology**
**1**. **Data Cleaning**
Converting  date and time fields to datetime format
Handle missing or duplicated values
Aggregate data to hourly averages for consistency

**2**. **Data Integration**
Merge the two datasets using datetime
Create derived features such as is_rainy, is_peak_hour, season, and weekday

**3**. **Feature Engineering**
**Rainfall Intensity Classification**:
Create categories based on precipitation values (e.g., none, light, moderate, heavy).
**Side-Specific Traffic Features:**
Use TI_An and TI_Av to separately analyze Asian and European side congestion.
**Weekday/Weekend Split**:
Extract day-of-week information from timestamps to assess behavioral differences.

**4**. **Exploratory Data Analysis (EDA)**
Distribution of congestion levels by day, hour, and weather type
Correlation heatmap between weather and congestion
Boxplots and time-series plots (rainfall vs. congestion index)

**5**. **Hypothesis Testing**
t-test:Compare mean congestion between rainy and non-rainy periods
ANOVA:Examine seasonal differences in traffic congestion
Correlation: Evaluate relationships between weather metrics and traffic index

**6**. **Visualization**
Time-series plots of weather vs. congestion
Heatmaps showing correlation strength
Boxplots of congestion by weather conditions


**Expected Results:**
1-Heavy rainfall is expected to produce noticeably higher congestion levels than light or moderate rainfall.
2-Rainfall may have a stronger effect during peak traffic hours.
3-The Asian and European sides may respond differently to rainfall intensity.
4-Other weather variables (wind, pressure, temperature) may play secondary or moderating roles.


**Limitations**:
1-Rainfall data represents city-level weather and may not capture micro-climate variations across Istanbul.
2-Traffic index is aggregated by region (Asian/European) and may not reflect district-level differences.
3-Observational analysis demonstrates correlation, not causation.
4-Weather forecasts may not perfectly match real-time conditions.

**Tools and Libraries**:
Python Libraries: pandas, numpy, matplotlib, statsmodels, 
Platform:  Google Colab



**Ethical Integrity**:
All datasets are publicly available from Kaggle.

