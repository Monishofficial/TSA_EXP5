# Ex: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 30-09-2025


### AIM:
To Illustrates how to perform time series analysis and decomposition on the monthly average temperature of a city/country and for airline passengers.

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:
```
#Developed By: MONISH N
#Reg No: 212223240097


import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose


gold_data = pd.read_csv("/content/Gold Price (2013-2023).csv")

# Clean and preprocess
gold_data['Date'] = pd.to_datetime(gold_data['Date'])
gold_data['Price'] = gold_data['Price'].str.replace(',', '').astype(float)

# Sort by date (important for time series)
gold_data = gold_data.sort_values('Date')

# Set Date as index
gold_data.set_index('Date', inplace=True)

# Decompose (monthly seasonality, so period=30 for daily data, or 12 for monthly averages)
decomposition = seasonal_decompose(gold_data['Price'], model='additive', period=30)

# Plot results
plt.figure(figsize=(10, 12))

plt.subplot(411)
plt.plot(gold_data['Price'], label='Gold Price')
plt.legend(loc='upper left')
plt.title('Gold Price (2013–2023)')

plt.subplot(412)
plt.plot(decomposition.trend, label='Trend', color='orange')
plt.legend(loc='upper left')
plt.title('Trend Plot')

plt.subplot(413)
plt.plot(decomposition.seasonal, label='Seasonal', color='green')
plt.legend(loc='upper left')
plt.title('Seasonality Plot')

plt.subplot(414)
plt.plot(decomposition.resid, label='Residual', color='red')
plt.legend(loc='upper left')
plt.title('Residual Plot')

plt.tight_layout()
plt.show()
```


### OUTPUT:

<img width="1277" height="382" alt="image" src="https://github.com/user-attachments/assets/cc160ae1-a9c9-4c8d-a374-7be5587c5f70" />
<img width="1265" height="364" alt="image" src="https://github.com/user-attachments/assets/039e36fb-9295-42ab-a61d-9a021ae84571" />
<img width="1247" height="365" alt="image" src="https://github.com/user-attachments/assets/d54c060c-67f4-48e3-aac2-11ecadbc79b3" />
<img width="1302" height="376" alt="image" src="https://github.com/user-attachments/assets/917b1881-843f-4619-b0b5-be4336ad415b" />


### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
