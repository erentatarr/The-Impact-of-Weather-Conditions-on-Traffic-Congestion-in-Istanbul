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
The weather data used in this study was obtained from a forecasting system and consists of forecast outputs generated for dates between 2020 and 2025. Therefore,
weather variables represent predicted conditions from the past rather than actual meteorological measurements.

This dataset was chosen due to its time span, data regularity, and direct availability for all dates matching traffic data. The aim of this project is not to evaluate forecast accuracy, but to examine the statistical relationships between traffic density and available weather information. Consequently, the analysis maintains its validity regarding the use of forecast-based weather inputs.



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
Aggregate data to daily averages for consistency

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



**28 November – Data Collection, EDA, and Hypothesis Testing**

All statistical analyses were conducted at a significance level of
α = 0.05 using Google Colab.
The complete Google Colab notebook is provided in the repository.

**1. Data Processing**

In this project, traffic data is provided with timestamp information at a minute-level resolution, while weather data is available at a daily level.

To ensure temporal consistency between the two datasets, traffic data was aggregated to a daily level. The datetime column of the traffic dataset was defined as a time index, and daily resampling was performed using the resample('D') function from the Pandas library. For each day, the arithmetic mean of minute-based traffic index (TI) values was calculated using the mean() function.

As a result, minute-level traffic measurements were transformed into a single daily average traffic index value. The aggregated daily traffic data was then merged with the daily weather dataset based on date, and all subsequent statistical analyses were conducted using this combined daily-level dataset.

**2. Exploratory Data Analysis (EDA) Findings**

**2.1 Distribution of Daily Traffic Index**

The histogram reveals that most daily traffic index (TI) values fall between 28 and 38, showing a clear concentration around the mid-30s. This suggests that Istanbul’s daily traffic intensity is generally stable, with occasional high-congestion outliers.

**2.2 Traffic Index by Rainfall Intensity**

The boxplot demonstrates that traffic congestion tends to increase as rainfall intensity rises. In contrast, “none” and “light” rain days exhibit lower medians and more compact distributions, indicating more stable congestion patterns.

**2.3 Asian vs. European Side Traffic Comparison**

The boxplot highlights that the European side (TI_Av) generally experiences slightly higher traffic congestion compared to the Asian side (TI_An). The European side also shows greater variability and more extreme congestion values.

**2.4 Correlation Analysis Between Traffic and Weather Variables**

The correlation heatmap shows a very strong positive correlation between the overall traffic index (TI) and the traffic indices of the Asian and European sides, indicating consistent city-wide congestion patterns.
Rainfall (prcp) displays a weak positive linear correlation with TI, while temperature (tavg), wind speed (wspd), and pressure (pres) show weak or near-zero linear correlations.

**2.5 Interpretation of Correlation Results**

This correlation matrix confirms the same overall pattern observed in Figure 2.4. While rainfall shows only a weak linear correlation with traffic congestion, hypothesis testing results indicate that rainfall intensity plays a statistically significant role, suggesting a non-linear or threshold-based relationship.

**3. Statistical Hypothesis Testing Findings**

**3.1 Main Hypothesis (Rainfall Intensity)**

Hypothesis Tested:
H₀: Rainfall intensity has no significant effect on traffic congestion in Istanbul.

Test Result:
H₀ was rejected. A one-way ANOVA test yielded a highly significant result
(F = 14.071, p = 5.86 × 10⁻⁹).

Conclusion:
Rainfall intensity is a statistically significant factor influencing daily traffic congestion levels in Istanbul.

**3.2 Side Hypothesis (Asian vs. European Side)**

Hypothesis Tested:
H₀: Rainfall intensity affects traffic congestion equally on the Asian and European sides of Istanbul.

Test Result:
H₀ was rejected. Separate ANOVA tests indicated statistically significant effects on both sides:

Asian Side: F = 14.3505, p < 0.001
European Side: F = 12.5162, p < 0.001

Conclusion:
While rainfall intensity significantly affects traffic congestion on both sides, the results suggest that the magnitude of this effect may differ slightly between the Asian and European sides.

**3.3 Additional Hypotheses (Other Weather Factors)**

Hypothesis Tested:
H₀: Other daily weather variables do not influence traffic congestion.

Test Result:
H₀ was partially rejected.

Conclusion:
Simple linear regression analyses indicated that average temperature (tavg) and wind speed (wspd) exhibit marginal but statistically significant relationships with traffic congestion
(p = 0.0380 and p = 0.0384, respectively).
Atmospheric pressure (pres) was found to be statistically non-significant (p = 0.5916).
However, the explanatory power of these linear models remains limited.

**Final Conclusion**

The analysis demonstrates that precipitation intensity is the most robust and consistent factor associated with daily traffic congestion in Istanbul. Although temperature and wind speed show marginal statistical significance in isolation, their overall explanatory power remains limited. These findings suggest that the effect of weather on traffic congestion is primarily driven by rainfall and is not fully captured by simple linear relationships.

**Future Work and Next Steps (02 January Deadline)**

Building on these findings, the next phase of the project will focus on applying more advanced machine learning techniques to better capture non-linear relationships and improve the predictive performance of traffic congestion models.

**02 January – Machine Learning Pipeline and Results** 

**1. Final Dataset Verification and Preparation** :The final dataset to be used in the project was verified to be correctly prepared before proceeding to the machine learning phase. For this purpose, all DataFrame objects in the notebook workspace were listed, and only the combined table containing daily weather and traffic data was selected. By avoiding modeling on raw or intermediate data tables, this phase guarantees methodological consistency. To ensure that the machine learning process uses a single reference database, the selected dataset was copied to the df variable. 

**2. Feature Selection and Target Definition** : At this stage, the feature set and target variable for the machine learning models were defined. The Traffic Index (TI), representing daily traffic density, was selected as the target variable. The feature set included climatic factors that could affect traffic density, such as temperature (average, minimum, and maximum), precipitation, wind speed, and air pressure. To ensure temporal consistency throughout the modeling phase, the data was organized chronologically.

**3. Time-Aware Train–Test Split** : The dataset was chronologically divided into training and test sets. The first 80% of the data was used for training, and the last 20% for testing. This approach prevents the model from indirectly seeing future information, eliminating the risk of data leakage and providing a realistic model evaluation. The date ranges of the training and test sets were also checked to verify that the division was consistent with the timeline.

**4. Missing Value Handling and Final Split**: Missing observations in the target variable and feature set were identified and removed from the study before modeling. At this stage, after removing the missing values, a test split operation was performed, and all machine learning models were trained using the same cleaned data. This method guarantees the consistency of the results and the comparability of the various models. The analysis included a total of 856 observations, 180 of which were excluded due to missing values.

**5. Baseline Model – Linear Regression**  : Initially, Linear Regression was used as a baseline reference model. The model produced an RMSE value of approximately 7.08 on the test data and resulted in a negative R² score. A negative R² value indicates that the model was unable to explain traffic congestion better than a simple mean-based estimate. This outcome suggests that the relationship between weather conditions and traffic congestion cannot be adequately captured through a purely linear formulation. 

**6. Nonlinear Model – Decision Tree Regressor** : A Decision Tree Regressor model was applied to detect nonlinear relationships. However, as highlighted in the lecture slides, the model suffered from an overfitting problem when used without any constraints. The decrease in performance on the test data and the further negative R² value indicated that the model overfitted the training data but could not generalize to new observations. 

**7. Ensemble Model – Random Forest Regressor** :To mitigate the overfitting problem observed in the Decision Tree model, the Random Forest Regressor was applied. By aggregating the predictions of multiple decision trees, this ensemble method produced more stable and balanced results. The Random Forest model achieved an RMSE of approximately 7.12, demonstrating improved stability compared to the Decision Tree model; however, it did not yield a substantial performance improvement over the Linear Regression baseline given the current feature set. 

**8. Model Comparison and Interpretation**: The performance of the implemented models was evaluated using RMSE and R² metrics. The results show that weather-related variables exhibit a consistent relationship with traffic congestion, but their predictive capacity alone remains limited. Precipitation emerged as the most correlated weather variable with traffic congestion. Overall, these findings confirm that model performance is influenced not only by the chosen methodology but also by the level of detail and information richness of the feature set.The  quantitative evaluation and model comparison are provided in the[Result Summary – Machine Learning Results](./Result_Summary.docx) file.


**9. Overall Evaluation** : The machine learning analysis yielded outcomes that were in line with the exploratory data analysis and hypothesis tests done at the beginning of the project.Although weather conditions do influence traffic density, accurately predicting complex urban systems such as traffic congestion requires incorporating additional contextual and behavioral factors beyond meteorological variables.This phase provides a transparent and methodologically sound evaluation of the role of weather conditions in explaining traffic congestion, reinforcing the conclusions drawn throughout the project.
