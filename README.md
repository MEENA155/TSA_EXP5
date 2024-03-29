# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 


### AIM:
To illustrate how to perform time series analysis and decomposition on the monthly average temperature of a city/country and for airline passengers.

### ALGORITHM:
1. Import the required packages like pandas and Numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:
```py
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

df = pd.read_csv('US_City_Temp_Data.csv')

df.isnull().sum()

df['time'] = pd.to_datetime(df['time'])

temperature_data = df['new_york']

new_index = pd.date_range(start=temperature_data.index.min(), periods=len(temperature_data), freq='MS')[:len(temperature_data)]

temperature_data.index = new_index

decomposition = seasonal_decompose(temperature_data, model='additive')

# Extract trend, seasonal, and residuals components
trend = decomposition.trend
seasonal = decomposition.seasonal
residuals = decomposition.resid

# Original data
plt.figure(figsize=(12, 6))
plt.plot(temperature_data, label='Original Temperature')
plt.legend()

# Trend plot
plt.figure(figsize=(12, 6))
plt.plot(trend, label='Trend')
plt.legend()

# Seasonal plot (optional)
plt.figure(figsize=(12, 6))
plt.plot(seasonal, label='Seasonal')
plt.legend()

# Residuals plot (optional)
plt.figure(figsize=(12, 6))
plt.plot(residuals, label='Residuals')
plt.legend()


```

### OUTPUT:
#### FIRST FIVE ROWS:

![DATA](https://github.com/JEEVAABI/TSA_EXP5/assets/93427098/794c93f5-9194-44c8-90ba-284528bf28a2)

#### PLOTTING THE DATA:

![ORIGINAL](https://github.com/JEEVAABI/TSA_EXP5/assets/93427098/9cd90975-c613-48b3-b6e3-9b9aebbe376f)

#### SEASONAL PLOT REPRESENTATION :

![SEASONAL](https://github.com/JEEVAABI/TSA_EXP5/assets/93427098/b51f467f-b9e6-40ff-82c8-656c29ed90a5)

#### TREND PLOT REPRESENTATION :

![TREND](https://github.com/JEEVAABI/TSA_EXP5/assets/93427098/f9442973-58bb-480a-b040-9624b3a965ec)

#### RESIDUAL PLOT REPRESENTATION :

![RESI](https://github.com/JEEVAABI/TSA_EXP5/assets/93427098/fcfc1201-a671-4676-81ab-478c131420c7)


### RESULT:
Thus we have created the Python code for the time series analysis and decomposition.
