# Tracking-Atmospheric-co2-A-Historical-Analysis-of-Emission-Trends-1958-2016-
This data science research project investigates the long-term trends in atmospheric carbon dioxide (CO₂) concentrations from 1958 to 2016.
## Project Overview
This data science research project investigates the long-term trends in atmospheric carbon dioxide (CO₂) concentrations from 1958 to 2016.

Utilizing high-resolution time-series data from the Mauna Loa Observatory and other verified sources, the project explores the seasonal and annual patterns of CO₂ emissions over nearly six decades.

Through trend analysis and robust data visualization, the study provides compelling evidence of the accelerating rise in CO₂ levels driven by anthropogenic activity.

By presenting clear, data-backed insights into historical CO₂ emissions, this project aims to inform public discourse, support environmental advocacy, and encourage policy interventions for climate action.
### Objectives
- To analyze the trend of atmospheric CO₂ concentrations from 1958 to 2016.

- To quantify the annual growth rate in CO₂ levels.

- To communicate findings using visualizations that are accessible to both scientific and non-scientific audiences.
### Data Source
**Mauna Loa Observatory CO₂ Data:** Provided by NOAA [National Oceanic and Atmospheric Administration](https://gml.noaa.gov/ccgg/trends/)
### Methodology
- Loaded the data from a CSV file into a Pandas Dataframe

- Converted the data into time-series format for seasonal decomposition

- Handled missing values and smoothed data using rolling averages

- Visualized the data to uncover the trend in co2 emmision from 1958 to 2016.

### Data Pre-Processing
he dataset is provided by NOAA [National Oceanic and Atmospheric Administration](https://gml.noaa.gov/ccgg/trends/),  contains records of the change in climate in the last half a century or so. 

The data is in a CSV file called `climate_change` with three columns. 

- 1. The `"date"` column indicates when the recording was made and is stored in the year-month-date format.
     A measurement was taken on the 6th day of every month from 1958 until 2016. 


- 2. The  `"co2"` column contains measurements of the carbon dioxide in the atmosphere.
     The number shown in each row is parts-per-million of carbon dioxide. 


- 3. The  `"relative_temp"` column denotes the temperature measured at this date, relative to a baseline which is the average        temperature in the first ten years of measurements. 
### Data Loading

~~~python

import pandas as pd 

climate_change_df = pd.read_csv('C:/Users/Admin/Documents/_EXCLUSIVE DATA SCIENCE BOOT CAMP_STUDENT FOLDER/_DATASET/climate_change.csv', parse_dates = ["date"], index_col =[ "date"])

climate_change_df.head()

~~~
![Capture](https://github.com/user-attachments/assets/48f3a860-cde8-4a6f-b423-fab78b8eabd6)

###  Data Analysis
- **Time-Series Decomposition**: This was used to separate trend, seasonality, and residuals.

- **Visualization:** Created line plots,  seasonal subseries plots, and anomaly detection visuals using Python library (Matplotlib)
###  Data Inspection(check for missing values),  
~~~python
# check for any missing on each column
climate_change_df.isna().any()

~~~
![capture105](https://github.com/user-attachments/assets/4d0c91ba-f5b6-46c4-af4a-9254a067a9cb)


~~~python
# counting the number of  missing values

climate_change_df.isna().sum()
~~~
![Capture100](https://github.com/user-attachments/assets/174d5227-eb89-44d3-aba7-29026fff3e54)


### Data Cleaning (handling missing values) 
~~~python
climate_change_df.shape
~~~

![Capture101](https://github.com/user-attachments/assets/bd7fc59b-828f-4a7a-ab57-d0ec6be51bb5)

~~~python
climate_change_df["co2"].mean() 
~~~

![Capture102](https://github.com/user-attachments/assets/1a1a1546-6882-496b-8606-4b12b4542288)


~~~python
# filling the missing value with the mean value 352.32 on the co2 column

climate_change_df= climate_change_df.fillna(352.32)

climate_change_df.head()
~~~

![Capture103](https://github.com/user-attachments/assets/b7707cc0-91bb-42a0-b993-986924a38e5f)

~~~python
# to cnfirm there arw no more missing value

climate_change_df.isna().any()
~~~
![capture105](https://github.com/user-attachments/assets/c85fd3cd-5366-4a3e-8e15-11da7d62367f)


### Data Visualization

~~~python
# Data Visiualization using the object oriented interface of matplotlib

import matplotlib.pyplot as plt

fig, ax = plt.subplots()


# visualizing the co2 emission vs Time (date)

ax.plot(climate_change_df.index, climate_change_df["co2"], color = "r")

# labelling the x-axis and y-axis

ax.set_xlabel("Time")
ax.set_ylabel("co2 (part per million)")

# adding a title
fig.suptitle("The Atmospheric c02 Emission Trends (1958–2016)")

# to show plot

plt.show()              
           
~~~
![The Atmospheric c02 Emission Trend](https://github.com/user-attachments/assets/5db6f9a9-d6df-4294-92cf-d03aa1b19674)

###  Data Interpretation
- The data visualization above shows that there is a overall steady increase of co2 emission from 1958 to 2016.
### Key Findings  

**Steady Increase**: CO₂ levels rose from approximately 315 ppm in 1958 to over 403 ppm by 2016.

**Seasonal Patterns**: A regular saw-tooth pattern was observed, corresponding to seasonal plant activity (photosynthesis cycles).

**Acceleration in Emissions**: Linear curve indicates steady growth and increasing acceleration in emissions, especially post-2000.

### Conclusion
The findings of this study provide compelling evidence of the dramatic rise in atmospheric CO₂ over the last half-century.

While natural seasonal variations exist, the long-term upward trend is unmistakably driven by industrialization, fossil fuel combustion, and land-use changes. 

These results underscore the urgency for global climate mitigation strategies and support the scientific consensus on anthropogenic climate change.

## Recommendations
- I strongly reconmmend  the global adoption of renewable energy sources.

- I strongly reconmmend the Promotion of  global CO₂ emission monitoring for real-time policy response.

- I strongly reconmmend that this  findings should be used as part of educational material in environmental science curricula.

- I strongly reconmmend the Extension of this  study to include temperature anomaly data for correlation analysis.
