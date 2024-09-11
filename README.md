## Developed by: Anbuselvan S
## Register No: 212223240008
## Date:

# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF) 

### AIM:
To Compute the AutoCorrelation Function (ACF) of the data for the first 35 lags to determine the model
type to fit the data.

### ALGORITHM:
1. Import the necessary packages
2. Find the mean, variance and then implement normalization for the data.
3. Implement the correlation using necessary logic and obtain the results
4. Store the results in an array
5. Represent the result in graphical representation as given below.
6. 
### PROGRAM:
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

df = pd.read_csv('/content/yahoo_stock.csv')
data = df['Volume'].values

mean = np.mean(data)
variance = np.var(data)

normalized_data = (data - mean) / np.sqrt(variance)

lag = 35
n = len(normalized_data)
autocorr = np.correlate(normalized_data, normalized_data, mode='full')
autocorr = autocorr[n-1:] / (variance * n)
autocorr_results = autocorr[:lag]

plt.figure(figsize=(10, 6))
plt.stem(range(lag), autocorr_results, use_line_collection=True)
plt.title('Autocorrelation Function (ACF)')
plt.xlabel('Lag')
plt.ylabel('Autocorrelation')
plt.grid(True)
plt.show()
```

### OUTPUT:
![image](https://github.com/user-attachments/assets/67d4c4bb-b7e8-40f7-b68f-4650a45a6a06)

### RESULT:
Thus , successfully implemented the auto correlation function in python.
