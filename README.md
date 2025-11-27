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



**28 November Collect the data, conduct exploratory data analysis methods and hypothesis tests on the data**
All tests were conducted at a significance level of alpha=0.05 in Google Colab. Google Colab file is in the ReadMe.

**1-Statistical Hypothesis Testing Findings:**

**Main Hypothesis (Rainfall Intensity)**
•	Hypothesis Tested: H0: Rainfall intensity has no significant effect on traffic congestion in Istanbul.
•	Test Result: H_0 was Rejected. The One-Way ANOVA test yielded a highly significant result (F = 14.071, p=p 5.86 times 10^-9).
•	Conclusion: Rainfall intensity is a statistically significant factor determining the level of daily traffic congestion in Istanbul.

**Side Hypothesis(Asian vs European Side)**
•	Hypothesis Tested: H_0: Rainfall intensity affects congestion equally on the Asian and European sides.
•	Test Result: H_0 was Rejected. Separate ANOVA tests showed a highly significant effect on both : F=14.3505, p < 0.001; F=12.5162, p < 0.001$).
•	Conclusion: While both sides are significantly affected, the magnitude of the effect is slightly stronger on the Asian Side

**Additional Hypothesis (Other Weather Factors)**
•	Hypothesis Tested: H_0: Other daily weather factors do not influence.
•	Test Result: H_0 was rejected.
•	Conclusion : Simple Linear Regressions showed that Temperature {tavg} and Wind Speed {wspd} each had a marginal, yet statistically significant, individual effect (p = 0.0380 and p = 0.0384.)
	Pressure {pres} was found to be statistically non-significant ($p = 0.5916).


 2-**Exploratory Data Analysis (EDA) Findings** (All images are in the ''EDA İmages'' file in the ReadMe).

 2.1:The histogram reveals that most daily traffic index (TI) values fall between 28 and 38, showing a clear concentration around the mid-30s.The graph suggests that Istanbul’s daily traffic intensity is generally stable but occasionally experiences high-congestion outliers.
 2.2:The boxplot demonstrates that traffic congestion tends to increase as rainfall intensity rises.In contrast, “none” and “light” rain days have lower medians and more compact distributions, suggesting more stable and less extreme congestion levels.
 2.3:The boxplot highlights that the European side (TI_Av) generally experiences slightly higher traffic congestion compared to the Asian side (TI_An), as indicated by a higher median.The European side also shows a wider spread and more extreme high outliers, suggesting that congestion events are more intense and variable there.
 2.4:The correlation heatmap shows a very strong positive correlation between the overall traffic index (TI) and the traffic levels of the Asian and European sides, indicating consistent congestion patterns across the city.Rainfall (prcp) shows a weak positive correlation with TI, suggesting that rainfall alone does not directly drive congestion but may be one contributing factor.
Temperature (tavg), wind speed (wspd), and pressure (pres) exhibit very weak or near-zero correlations with TI, indicating minimal linear relationships between these weather variables and traffic intensity.


**Final Conclusion**
The most significant result is that only precipitation intensity is consistent in predicting the daily average traffic index in Istanbul. When the effect of precipitation is not included, other daily weather factors (temperature and wind speed) remain inconsistent in providing a statistically significant prediction.

**Future Work and Next Steps (02 January Deadline)**
The initial analysis confirmed that rainfall is the primary driver of traffic congestion, while the predictive power of linear models remains low. The next phase of this project will focus on advanced Machine Learning (ML) techniques to build a more robust predictive model.




