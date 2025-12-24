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

**Important Note Regarding the Use of Weather Data:**

Although the dataset is named "Istanbul Weather Forecast Logs," the data used in this project consists of daily weather records from past dates. The analysis is entirely retrospective, focusing on examining past traffic density along with past weather conditions on the same dates.

No future or predictive weather forecasts were used in this study. Weather records were treated as actual daily meteorological observations and combined with traffic data according to matching dates.

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
2-The Asian and European sides may respond differently to rainfall intensity.
2-Other weather variables (wind, pressure, temperature) may play secondary or moderating roles.


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



## 28 November – Data Collection, EDA, and Hypothesis Testing

All statistical analyses were conducted at a significance level of  
**α = 0.05** using **Google Colab**.  
The complete Google Colab notebook is provided in the repository.



## 1. Statistical Hypothesis Testing Findings

### 1.1 Main Hypothesis (Rainfall Intensity)

**Hypothesis Tested:**  
H₀: Rainfall intensity has no significant effect on traffic congestion in Istanbul.

**Test Result:**  
H₀ was rejected. A one-way ANOVA test yielded a highly significant result  
(F = 14.071, p = 5.86 × 10⁻⁹).

**Conclusion:**  
Rainfall intensity is a statistically significant factor influencing daily traffic congestion levels in Istanbul.



### 1.2 Side Hypothesis (Asian vs. European Side)

**Hypothesis Tested:**  
H₀: Rainfall intensity affects traffic congestion equally on the Asian and European sides of Istanbul.

**Test Result:**  
H₀ was rejected. Separate ANOVA tests indicated statistically significant effects on both sides:  
- Asian Side: F = 14.3505, p < 0.001  
- European Side: F = 12.5162, p < 0.001  

**Conclusion:**  
While rainfall intensity significantly affects traffic congestion on both sides, the results suggest that the magnitude of this effect may differ slightly between the Asian and European sides.



### 1.3 Additional Hypotheses (Other Weather Factors)

**Hypothesis Tested:**  
H₀: Other daily weather variables do not influence traffic congestion.

**Test Result:**  
H₀ was partially rejected.

**Conclusion:**  
Simple linear regression analyses indicated that average temperature (tavg) and wind speed (wspd) exhibit marginal but statistically significant relationships with traffic congestion  
(p = 0.0380 and p = 0.0384, respectively).  
Atmospheric pressure (pres) was found to be statistically non-significant (p = 0.5916).  
However, the explanatory power of these linear models remains limited.



## 2. Data Processing

In this project, traffic data is provided with timestamp information at a minute-level resolution, while weather data is available at a daily level.

To ensure temporal consistency between the two datasets, traffic data was aggregated to a daily level. The datetime column of the traffic dataset was defined as a time index, and daily resampling was performed using the `resample('D')` function from the Pandas library. For each day, the arithmetic mean of minute-based traffic index (TI) values was calculated using the `mean()` function.

As a result, minute-level traffic measurements were transformed into a single daily average traffic index value. The aggregated daily traffic data was then merged with the daily weather dataset based on date, and all subsequent statistical analyses were conducted using this combined daily-level dataset.



## 3. Exploratory Data Analysis (EDA) Findings

### 3.1 Distribution of Daily Traffic Index

The histogram reveals that most daily traffic index (TI) values fall between 28 and 38, showing a clear concentration around the mid-30s. This suggests that Istanbul’s daily traffic intensity is generally stable, with occasional high-congestion outliers.



### 3.2 Traffic Index by Rainfall Intensity

The boxplot demonstrates that traffic congestion tends to increase as rainfall intensity rises. In contrast, “none” and “light” rain days exhibit lower medians and more compact distributions, indicating more stable congestion patterns.



### 3.3 Asian vs. European Side Traffic Comparison

The boxplot highlights that the European side (TI_Av) generally experiences slightly higher traffic congestion compared to the Asian side (TI_An). The European side also shows greater variability and more extreme congestion values.



### 3.4 Correlation Analysis Between Traffic and Weather Variables

The correlation heatmap shows a very strong positive correlation between the overall traffic index (TI) and the traffic indices of the Asian and European sides, indicating consistent city-wide congestion patterns.  
Rainfall (prcp) displays a weak positive linear correlation with TI, while temperature (tavg), wind speed (wspd), and pressure (pres) show weak or near-zero linear correlations.



### 3.5 Interpretation of Correlation Results

This correlation matrix confirms the same overall pattern observed in Figure 3.4. While rainfall shows only a weak linear correlation with traffic congestion, hypothesis testing results indicate that rainfall intensity plays a statistically significant role, suggesting a non-linear or threshold-based relationship.



## Final Conclusion

The analysis demonstrates that precipitation intensity is the most robust and consistent factor associated with daily traffic congestion in Istanbul. Although temperature and wind speed show marginal statistical significance in isolation, their overall explanatory power remains limited. These findings suggest that the effect of weather on traffic congestion is primarily driven by rainfall and is not fully captured by simple linear relationships.



## Future Work and Next Steps (02 January Deadline)

Building on these findings, the next phase of the project will focus on applying more advanced machine learning techniques to better capture non-linear relationships and improve the predictive performance of traffic congestion models.




