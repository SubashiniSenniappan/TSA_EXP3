# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
# Developed by:SUBASHINI S
# Date: 

### AIM:
To Compute the AutoCorrelation Function (ACF) of the data for the first 35 lags to determine the model
type to fit the data.
### ALGORITHM:
1. Import the necessary packages
2. Find the mean, variance and then implement normalization for the data.
3. Implement the correlation using necessary logic and obtain the results
4. Store the results in an array
5. Represent the result in graphical representation as given below.
### PROGRAM:
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
df = pd.read_csv('/mnt/data/weather_classification_data.csv')
data = df['Temperature'].values
mean = np.mean(data)
variance = np.var(data)
normalized_data = (data - mean) / np.sqrt(variance)
def compute_autocorrelation(data, lag):
    n = len(data)
    autocorr = np.correlate(data, data, mode='full')
    autocorr = autocorr[n-1:] / (variance * n)
    return autocorr[:lag]

lag = 35  # You can change this to the desired number of lags
autocorr_results = compute_autocorrelation(normalized_data, lag)
plt.figure(figsize=(10, 6))
plt.stem(range(lag), autocorr_results, use_line_collection=True)
plt.title('Autocorrelation Function (ACF)')
plt.xlabel('Lag')
plt.ylabel('Autocorrelation')
plt.grid(True)
plt.show()

```


### OUTPUT:

![Screenshot 2024-09-11 091307](https://github.com/user-attachments/assets/fa92bf12-70bc-48c9-8e0f-822f98fca9b9)


### RESULT:
        Thus we have successfully implemented the auto correlation function in python.
