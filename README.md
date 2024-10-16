### DEVELOPED BY: SABARI S
### REGISTER NO:  212222240085
### Date:
# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
 

### AIM:
To Compute the Auto Correlation Function (ACF) of the Petrol Price dataset for the first 35 lags to determine the model type to fit the data.

### ALGORITHM:
1. Import the necessary packages
2. Find the mean, variance and then implement normalization for the data.
3. Define a Function to Compute Autocorrelation Function (ACF).
4. Implement the correlation using necessary logic and obtain the results
5. Store the results in an array
6. Represent the result in graphical representation as given below.
### PROGRAM:
```python
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd

# Load your dataset
file_path = 'data_date.csv'  # Ensure this is the correct path to your CSV file
data = pd.read_csv(file_path)

# Extract AQI values for a specific country, e.g., 'India'
country_data = data[data['Country'] == 'India'].copy()

# Extract the 'AQI Value' column
price_data = country_data['AQI Value'].values

# Calculate mean and variance
mean_price = np.mean(price_data)
var_price = np.var(price_data)

# Normalize the data (subtract mean and divide by standard deviation)
normalized_price = (price_data - mean_price) / np.sqrt(var_price)

# Compute the ACF for the first 35 lags
def compute_acf(data, max_lag):
    acf_values = []
    n = len(data)
    for lag in range(max_lag + 1):
        if lag == 0:
            acf_values.append(1)  # ACF at lag 0 is always 1
        else:
            acf = np.corrcoef(data[:-lag], data[lag:])[0, 1]
            acf_values.append(acf)
    return acf_values

lags = range(35)
acf_values = compute_acf(normalized_price, 34)

# Plot the ACF results
plt.figure(figsize=(10, 6))
plt.stem(lags, acf_values, use_line_collection=True)
plt.title('Autocorrelation Function (ACF) for AQI Values')
plt.xlabel('Lag')
plt.ylabel('ACF')
plt.grid(True)
plt.show()

```

### OUTPUT:
![Untitled](https://github.com/user-attachments/assets/d4f07887-bcc6-42d3-86a3-87702bc31d12)

### RESULT:
Thus, the python code for implementing the auto correlation function is executed successfully.
