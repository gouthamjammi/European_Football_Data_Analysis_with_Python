# European Football Data Analysis with Python

This project is a beginner-friendly data analysis exercise using Python, focused on European football data (sample data from the English Premier League). The project includes loading, exploring, visualizing, and deriving insights from football statistics.


## Project Overview

We analyze a small dataset containing football players' information such as goals, assists, positions, club affiliation, age, etc. Using Python and libraries like Pandas, NumPy, Matplotlib, and Seaborn, we uncover various patterns in the data such as:

* Who scored the most goals?
* What is the penalty conversion rate?
* Which clubs have the youngest players?
* Which players received the most yellow cards?
* What is the age distribution of players?
* Which clubs contribute the most assists or goals?

This project is beginner-friendly and designed to showcase essential data analysis skills from end-to-end.

## Prerequisites

You need the following tools installed on your system:

* Python 3.x
* Jupyter Notebook or JupyterLab
* Pandas
* NumPy
* Matplotlib
* Seaborn

Install dependencies using pip:

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

## Installation Guide

To get started:

1. Install Python 3.x from the [official website](https://www.python.org/downloads/).
2. Install JupyterLab and required libraries:

```bash
pip install jupyterlab pandas numpy matplotlib seaborn
```

3. Open your project folder and launch Jupyter Notebook:

```bash
cd path/to/your/project/folder
jupyter notebook
```

## Dataset Used

We use a simplified sample of the English Premier League 2020/21 season:
**[EPL\_20\_21\_sample.csv](sandbox:/mnt/data/EPL_20_21_sample.csv)**

## Project Files

* **Football\_Data\_Analysis.ipynb** - Main notebook for analysis
* **EPL\_20\_21\_sample.csv** - Dataset used in the project

## Key Sections in the Notebook

### 1. Import Libraries

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
%matplotlib inline
```

### 2. Load Dataset

```python
df_football = pd.read_csv('EPL_20_21_sample.csv')
df_football.head()
```

### 3. Explore Dataset

* View structure: `df_football.info()`
* Descriptive statistics: `df_football.describe()`
* Check missing values: `df_football.isnull().sum()`

### 4. Create New Metrics

* Minutes per match
* Goals per match

```python
df_football['MinsPerMatch'] = (df_football['Mins'] / df_football['Matches']).astype(int)
df_football['GoalsPerMatch'] = (df_football['Goals'] / df_football['Matches']).astype(float)
```

### 5. Analyze Goals and Penalties

```python
Total_Goals = df_football['Goals'].sum()
penalty_goals = df_football['Penalty_Goals'].sum()
penalty_attempts = df_football['Penalty_Attempted'].sum()
missed = penalty_attempts - penalty_goals
```

* **Pie chart for Penalty Conversion**

```python
plt.figure(figsize=(7,7))
plt.pie([missed, penalty_goals], labels=['Missed', 'Scored'], autopct='%.1f%%')
plt.title("Penalty Conversion")
plt.show()
```

### 6. Nationalities & Positions

* Unique positions: `df_football['Position'].unique()`
* Total players by nationality:

```python
df_football['Nationality'].value_counts().head(10).plot(kind='bar')
```

### 7. Age-Based Analysis

```python
Under20 = df_football[df_football['Age'] <= 20]
age20_25 = df_football[(df_football['Age'] > 20) & (df_football['Age'] <= 25)]
age25_30 = df_football[(df_football['Age'] > 25) & (df_football['Age'] <= 30)]
Above30 = df_football[df_football['Age'] > 30]

x = [len(Under20), len(age20_25), len(age25_30), len(Above30)]
labels = ['<=20', '21-25', '26-30', '>30']
plt.pie(x, labels=labels, autopct='%.1f%%')
plt.title("Player Age Distribution")
plt.show()
```

### 8. Club-Wise Insights

* Players per club:

```python
df_football['Club'].value_counts().plot(kind='bar')
```

* Average age per club using boxplot:

```python
plt.figure(figsize=(12,6))
sns.boxplot(x='Club', y='Age', data=df_football)
plt.xticks(rotation=90)
```

### 9. Performance Metrics

* Top scorers:

```python
df_football[['Name','Club','Goals']].sort_values(by='Goals', ascending=False).head(10)
```

* Goals per match:

```python
df_football[['Name','GoalsPerMatch']].sort_values(by='GoalsPerMatch', ascending=False).head(10)
```

* Top assists:

```python
df_football[['Name','Assists']].sort_values(by='Assists', ascending=False).head(10)
```

* Assists by club:

```python
assists_by_club = df_football.groupby('Club')['Assists'].sum().sort_values(ascending=False)
assists_by_club.plot(kind='bar', figsize=(12,6))
```

* Goals by club:

```python
goals_by_club = df_football.groupby('Club')['Goals'].sum().sort_values(ascending=False)
goals_by_club.plot(kind='bar', figsize=(12,6))
```

### 10. Yellow Cards Analysis

```python
df_football[['Name','Yellow_Cards']].sort_values(by='Yellow_Cards', ascending=False).head(10)
```

```python
plt.figure(figsize=(10,6))
sns.barplot(data=df_football.sort_values(by='Yellow_Cards', ascending=False).head(10),
            x='Name', y='Yellow_Cards', palette='flare')
plt.xticks(rotation=45)
plt.title("Top 10 Players with Most Yellow Cards")
plt.show()
```

## Outcome

This project demonstrates:

* How to handle real-world sports datasets
* How to derive insights using basic statistics
* How to visualize results effectively with Python

## Future Improvements

* Use a complete season dataset with additional features (e.g. xG, xA, match location)
* Add time series analysis for player trends
* Build a dashboard using Plotly or Streamlit

## License

This project is for educational purposes. You may use and modify it with proper attribution.

---

Built with ❤️ by Goutham
