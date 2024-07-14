# UNEMPLOYMENT ANALYSIS WITH PYTHON

Unemployment is measured by the unemployment rate, which is the number of people who are unemployed as a percentage of the total labour force. We have seen a sharp increase in the unemployment rate during Covid-19, so analyzing the unemployment rate can be a good data science project.

## 1. Business/Data Understanding

### Objective
Analyze the unemployment rate in India, focusing on the period during the COVID-19 pandemic, to understand the impact on different regions and provide actionable insights for policymakers and stakeholders.

### Key Business Questions
- How did the unemployment rate change during the COVID-19 pandemic in different regions of India?
- Which regions were most affected by unemployment during the pandemic?
- What are the trends and patterns in unemployment rates over time?
- How does the unemployment rate correlate with other economic indicators such as the estimated number of employed individuals and the labor participation rate?
- What recommendations can be made to mitigate the impact of unemployment in future crises?

### Stakeholders
- Government and policymakers
- Economists and researchers
- Employment and labor organizations
- Businesses and investors
- General public

### Dataset 1: Unemployment in India
**Columns:**
- `Region`: The region in India (e.g., Andhra Pradesh).
- `Date`: The date of the data entry.
- `Frequency`: The frequency of the data (e.g., Monthly).
- `Estimated Unemployment Rate (%)`: The estimated unemployment rate as a percentage.
- `Estimated Employed`: The estimated number of employed individuals.
- `Estimated Labour Participation Rate (%)`: The estimated labor participation rate as a percentage.
- `Area`: The area type (e.g., Rural).

### Dataset 2: Unemployment Rate up to 11_2020
**Columns:**
- `Region`: The region in India.
- `Date`: The date of the data entry.
- `Frequency`: The frequency of the data.
- `Estimated Unemployment Rate (%)`: The estimated unemployment rate as a percentage.
- `Estimated Employed`: The estimated number of employed individuals.
- `Estimated Labour Participation Rate (%)`: The estimated labor participation rate as a percentage.
- `Region.1`: Region categorization (e.g., South).
- `longitude`: Longitude of the region.
- `latitude`: Latitude of the region.

## 2. Data Preparation

```python
# Import necessary libraries
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Load datasets
df1 = pd.read_csv('/content/Unemployment in India.csv')
df2 = pd.read_csv('/content/Unemployment_Rate_upto_11_2020.csv')

# Strip leading and trailing spaces from column names
df1.columns = df1.columns.str.strip()
df2.columns = df2.columns.str.strip()

# Strip leading and trailing spaces from date values
df1['Date'] = df1['Date'].str.strip()
df2['Date'] = df2['Date'].str.strip()

# Convert 'Date' columns to datetime format
df1['Date'] = pd.to_datetime(df1['Date'], format='%d-%m-%Y')
df2['Date'] = pd.to_datetime(df2['Date'], format='%d-%m-%Y')

# Explore datasets
print("Dataset 1 info:")
df1.info()
print("\nDataset 2 info:")
df2.info()

# Check for missing values
print("\nMissing values in Dataset 1:")
print(df1.isnull().sum())
print("\nMissing values in Dataset 2:")
print(df2.isnull().sum())
