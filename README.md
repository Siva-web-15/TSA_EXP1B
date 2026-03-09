# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA
# Date: 01.03.2026
# NAME : SIVABALAN M
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
# ===============================
# IMPORT REQUIRED PACKAGES
# ===============================
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

# ===============================
# READ THE DATA
# ===============================
file_path = "Gold Price (2013-2023).csv"
df = pd.read_csv(file_path)

# ===============================
# DATA PREPROCESSING
# ===============================

# Convert Date column to datetime
df['Date'] = pd.to_datetime(df['Date'])

# Remove commas from Price and convert to float
df['Price'] = df['Price'].str.replace(',', '')
df['Price'] = df['Price'].astype(float)

# Sort data in ascending order
df = df.sort_values('Date')

# Set Date as index
df.set_index('Date', inplace=True)

# Keep only Price column
ts = df['Price']

# ===============================
# ORIGINAL DATA PLOT
# ===============================
plt.figure()
plt.plot(ts)
plt.title("Original Gold Price Time Series")
plt.xlabel("Date")
plt.ylabel("Price")
plt.show()

# ===============================
# REGULAR DIFFERENCING
# ===============================
regular_diff = ts.diff().dropna()

plt.figure()
plt.plot(regular_diff)
plt.title("Regular Differencing")
plt.xlabel("Date")
plt.ylabel("Differenced Price")
plt.show()

# ===============================
# SEASONAL ADJUSTMENT
# (Assuming yearly seasonality = 365 for daily data)
# ===============================
decomposition = seasonal_decompose(ts, model='additive', period=365)
seasonal_component = decomposition.seasonal
seasonally_adjusted = ts - seasonal_component

plt.figure()
plt.plot(seasonally_adjusted)
plt.title("Seasonally Adjusted Series")
plt.xlabel("Date")
plt.ylabel("Adjusted Price")
plt.show()

# ===============================
# LOG TRANSFORMATION
# ===============================
log_transformed = np.log(ts)

plt.figure()
plt.plot(log_transformed)
plt.title("Log Transformed Series")
plt.xlabel("Date")
plt.ylabel("Log Price")
plt.show()

# ===============================
# DISPLAY RESULTS
# ===============================
print("\nOUTPUT:")
print("\nOriginal Data:")
print(ts.head())

print("\nREGULAR DIFFERENCING:")
print(regular_diff.head())

print("\nSEASONAL ADJUSTMENT:")
print(seasonally_adjusted.head())

print("\nLOG TRANSFORMATION:")
print(log_transformed.head())
```

### OUTPUT:
### ORIGINAL :

<img width="797" height="620" alt="image" src="https://github.com/user-attachments/assets/aff402c7-72f0-4171-894c-a81e475f4159" />


### REGULAR DIFFERENCING:


<img width="801" height="649" alt="image" src="https://github.com/user-attachments/assets/01c94019-191f-47a4-81e7-3f27be136893" />


### SEASONAL ADJUSTMENT:


<img width="792" height="616" alt="image" src="https://github.com/user-attachments/assets/cacf2b1b-8698-47be-8e02-2cf0b63e58cb" />


### LOG TRANSFORMATION:


<img width="776" height="642" alt="image" src="https://github.com/user-attachments/assets/8ec6f38f-27ec-4ffd-9925-0fa675fe543e" />



### RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on international airline passenger
data.
