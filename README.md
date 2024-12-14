import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import os

# Function to create 'gdp_data.csv' if it doesn't exist
def create_gdp_file():
    data = """Year,Country,GDP
2000,United States,10252345
2000,China,1211357
2000,India,476392
2005,United States,13036637
2005,China,2285965
2005,India,834928
2010,United States,15056773
2010,China,6105048
2010,India,1675838
2015,United States,18219297
2015,China,11137916
2015,India,2103586
2020,United States,20936600
2020,China,14722731
2020,India,2626220"""
    


# Check if 'gdp_data.csv' exists; if not, create it
if not os.path.exists("gdp_data.csv"):
    create_gdp_file()

# Load GDP data
data = pd.read_csv('gdp_data.csv')

# Basic analysis
print(data.describe())
print(data.info())

# Visualizing GDP trends
plt.figure(figsize=(12, 6))
sns.lineplot(data=data, x='Year', y='GDP', hue='Country')
plt.title('GDP Trends Over Years')
plt.xlabel('Year')
plt.ylabel('GDP in Trillions')
plt.legend(title='Country')
plt.show()

# Correlation matrix
correlation = data.corr()
plt.figure(figsize=(10, 8))
sns.heatmap(correlation, annot=True, fmt='.2f', cmap='coolwarm')
plt.title('Correlation Matrix of GDP Factors')
plt.show()
