### Introduction

Welcome to your first project using pandas in Jupyter Notebook! Pandas is widely acclaimed as the premier data-management tool in Python, making it indispensable for Data Analysis and Data Science tasks.

Here's a glimpse of what pandas can do:

- **Loading and Exporting Data**: Effortlessly import data from various formats like CSV, XML, HTML, Excel, JSON, and even directly from the Internet. Exporting data is just as seamless.
- **Data Analysis**: Conduct detailed statistical analysis, query datasets, identify discrepancies, and more.
- **Data Cleaning**: Quickly identify and handle missing values, duplicates, and incorrect entries.
- **Visualizations**: Combine the power of pandas with matplotlib to create insightful visual representations of your data.
- **Data Wrangling/Munging**: Perform complex data manipulation tasks such as merging datasets, creating derived datasets, and grouping data.

While this project won't delve deeply into the mechanics of using pandas, it will give us a firsthand look at its capabilities. Don't fret if you're not yet comfortable executing these tasks; subsequent projects will provide thorough explanations and hands-on practice.

Ready to dive in? Let's move to the next page and start your Jupyter Notebook.

### 1. Loading the Data

Let's start by importing the pandas library and loading our dataset:

```python
import pandas as pd
df = pd.read_csv("C:/Users/wasee/OneDrive/Desktop/Kaggle/Stock_market.csv", index_col='Date', parse_dates=True, dayfirst=True)
df.head()
```

This code snippet imports the pandas library and reads our dataset using the `read_csv` method. The dataset is now stored in a DataFrame named `df`. We then display the first few rows of the DataFrame using the `head()` method.

### 2. Analyzing the Data

During the analysis phase, we can leverage pandas to gain insights into our dataset:

```python
# Summary statistics
df.describe()

# Specific column statistics
df['Close'].min()
df['Close'].max()

# Visualizations
import matplotlib.pyplot as plt

# Simple line chart for Close price
df['Close'].plot(figsize=(12, 6), title='Closing Price (2017 - 2022)')

# More advanced chart combining Close Price and Volume
ax1 = df['Close'].plot(figsize=(12, 6), title='S&P Closing Price | 2017 - 2022')
ax2 = ax1.twinx()
df['Volume'].plot(ax=ax2, color='red', ylim=[df['Volume'].min(), df['Volume'].max() * 5])

# Subplots for Close price and Volume
fig, axes = plt.subplots(nrows=2, ncols=1, figsize=(12, 6))
df['Close'].plot(ax=axes[0], title='S&P Closing Price', legend=True, color='blue')
df['Volume'].plot(ax=axes[1], title='Volume', legend=True, color='green')

# Histogram of Volume
df['Volume'].plot(kind='hist')
plt.title('Histogram of Volume')

# Box plot of Volume
df['Volume'].plot(kind='box', vert=False)
plt.title('Box Plot of Volume')
```

### 3. Data Wrangling

Data wrangling involves cleaning, transforming, and enriching raw data:

```python
# Calculate Simple Moving Average (SMA) for Close price
df['Close SMA'] = df['Close'].rolling(60).mean()

# Calculate Lower and Upper Bollinger Bands
df['Lower Band'] = df['Close SMA'] - (2 * df['Close'].rolling(60).std())
df['Upper Band'] = df['Close SMA'] + (2 * df['Close'].rolling(60).std())

# Plot Close price and SMA
df[['Close', 'Close SMA']].plot(figsize=(14, 7), title='Close Price & its SMA')
```

These operations demonstrate pandas' capabilities in handling various data wrangling tasks effectively.

### Final Thoughts

As you've witnessed, pandas is a powerful library that facilitates data analysis and manipulation tasks with ease. With practice and exploration, you'll harness its full potential and become proficient in utilizing it for your Data Science endeavors.

Now, let's dive into the world of pandas and embark on an exciting journey of learning and discovery!

*End of Notebook*

If you want to share this code on GitHub, you can create a new repository and upload the Jupyter Notebook file (.ipynb) along with any necessary dataset files.
