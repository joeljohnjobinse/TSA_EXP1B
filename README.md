# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA
# Date: 

### AIM:
To perform regular differncing,seasonal adjustment and log transformatio on international airline passenger data
### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the data preprocessing if needed and apply regular differncing,seasonal adjustment,log transformation.
4. Plot the data according to need, before and after regular differncing,seasonal adjustment,log transformation.
5. Display the overall results.
   
### PROGRAM:
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

data = pd.read_csv('Air_Traffic_Passenger_Statistics.csv')

print(data.head())

data['Activity Period'] = pd.to_datetime(data['Activity Period'], errors='coerce')

data = data.sort_values('Activity Period')

data.set_index('Activity Period', inplace=True)

series = data['Passenger Count']

plt.figure(figsize=(10,4))
plt.plot(series, label='Original Data')
plt.title('Original Time Series')
plt.legend()
plt.show()

# ===============================
# REGULAR DIFFERENCING
# ===============================
diff_series = series.diff().dropna()

plt.figure(figsize=(10,4))
plt.plot(diff_series, label='Regular Differencing')
plt.title('After Regular Differencing')
plt.legend()
plt.show()

# ===============================
# SEASONAL ADJUSTMENT
# ===============================
# Assuming monthly seasonality (lag = 12)
seasonal_diff = series.diff(12).dropna()

plt.figure(figsize=(10,4))
plt.plot(seasonal_diff, label='Seasonal Differencing (lag=12)')
plt.title('After Seasonal Adjustment')
plt.legend()
plt.show()

# ===============================
# LOG TRANSFORMATION
# ===============================
log_series = np.log(series)

plt.figure(figsize=(10,4))
plt.plot(log_series, label='Log Transformation')
plt.title('After Log Transformation')
plt.legend()
plt.show()

```

### OUTPUT:

#### ORIGINAL DATASET:
<img width="607" height="613" alt="image" src="https://github.com/user-attachments/assets/4ba22427-5244-4677-b348-f1b7c0948201" />


#### REGULAR DIFFERENCING:
<img width="604" height="241" alt="image" src="https://github.com/user-attachments/assets/e6ea8302-ff60-400d-b368-d140731f6eec" />


#### SEASONAL ADJUSTMENT:
<img width="613" height="241" alt="image" src="https://github.com/user-attachments/assets/9983756a-c17b-4fa6-81e2-c0de988b65d2" />


#### LOG TRANSFORMATION:
<img width="619" height="229" alt="image" src="https://github.com/user-attachments/assets/102f192f-70b2-47c6-9553-69fd6b7376b0" />



### RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on international airline passenger
data.
