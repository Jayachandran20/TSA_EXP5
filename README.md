## DEVELOPED BY: M.JAYACHANDRAN
## REGISTER NUMBER: 212222240038
## DATE:
# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
 

# AIM:
To perform time series analysis and decomposition on monthly average data of a Future gold price using the multiplicative decomposition model, and visualize its trend, seasonality, and residual components.

# ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

# PROGRAM:
```python
import pandas as pd
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose


file_path = 'future_gold_price.csv'  # Update with the correct path if needed
data = pd.read_csv(file_path)

# Convert 'Date' to datetime and set it as index
data['Date'] = pd.to_datetime(data['Date'])
data.set_index('Date', inplace=True)


data['Close'] = pd.to_numeric(data['Close'], errors='coerce')
data.dropna(subset=['Close'], inplace=True)

# Perform seasonal decomposition
period = 12  # You can change the period as needed
result = seasonal_decompose(data['Close'], model='additive', period=period)

# Plot the decomposed components (trend, seasonal, and residual)
plt.figure(figsize=(12, 8))

plt.subplot(311)
plt.plot(result.trend)
plt.title('Trend')

plt.subplot(312)
plt.plot(result.seasonal)
plt.title('Seasonal')

plt.subplot(313)
plt.plot(result.resid)
plt.title('Residual')

plt.tight_layout()
plt.show()

```

### OUTPUT:
### SEASONAL PLOT REPRESENTATION :
![Screenshot 2024-09-23 110128](https://github.com/user-attachments/assets/3fee8bf0-7f4c-4d3a-9bff-78c45ea58cbc)


#### TREND PLOT REPRESENTATION :
![Screenshot 2024-09-23 110111](https://github.com/user-attachments/assets/374948ba-da99-4ddc-960c-6475dc00c46f)


#### Residual REPRESENTATION:

![Screenshot 2024-09-23 110141](https://github.com/user-attachments/assets/314f8885-4b31-4c3d-bf4f-5ead2844e058)




# RESULT:
Thus, the python code for time series decomposition was successfully performed on the future gold price of the digital currency.
