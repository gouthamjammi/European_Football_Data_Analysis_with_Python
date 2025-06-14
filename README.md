# European_Football_Data_Analysis_with_Python
This project is a beginner-friendly data analysis exercise using Python, focused on European football data (sample data from the English Premier League). The project includes loading, exploring, visualizing, and deriving insights from football statistics.

Project Overview

We analyze a small dataset containing football players' information such as goals, assists, positions, club affiliation, age, etc. Using Python and libraries like Pandas, NumPy, Matplotlib, and Seaborn, we uncover various patterns in the data such as:

Who scored the most goals?

What is the penalty conversion rate?

Which clubs have the youngest players?

Which players received the most yellow cards?

This project is beginner-friendly and designed to showcase essential data analysis skills.

Prerequisites

You need the following tools installed on your system:

Python 3.x

Jupyter Notebook or JupyterLab

Pandas

NumPy

Matplotlib

Seaborn

Install dependencies using pip:

pip install pandas numpy matplotlib seaborn jupyter

Dataset Used

We use a simplified sample of the English Premier League 2020/21 season:
EPL_20_21_sample.csv

Project Files

Football_Data_Analysis.ipynb - Main notebook for analysis

EPL_20_21_sample.csv - Dataset used in the project

Key Sections in the Notebook

1. Import Libraries

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
%matplotlib inline

2. Load Dataset

df_football = pd.read_csv('EPL_20_21_sample.csv')
df_football.head()

3. Explore Dataset

View structure: df_football.info()

Descriptive statistics: df_football.describe()

Check missing values: df_football.isnull().sum()

4. Create New Metrics

Minutes per match

Goals per match

df_football['MinsPerMatch'] = (df_football['Mins'] / df_football['Matches']).astype(int)
df_football['GoalsPerMatch'] = (df_football['Goals'] / df_football['Matches']).astype(float)

5. Analyze Goals and Penalties

Total goals

Penalties scored vs missed

Pie chart visualization

6. Nationalities & Positions

Unique player positions

Players by nationality

7. Top Performers

Top 3 goal scorers

Players with most yellow cards (bar chart)

8. Visualization Examples

# Penalty conversion pie chart
plt.pie([missed, penalty_goals], labels=['Missed', 'Scored'], autopct='%.1f%%')
plt.title("Penalty Conversion")
plt.show()

# Yellow cards bar chart
sns.barplot(data=df_football.sort_values(by='Yellow_Cards', ascending=False),
            x='Name', y='Yellow_Cards')

Outcome

This project demonstrates:

How to handle real-world sports datasets

How to derive insights using basic statistics

How to visualize results effectively

Future Improvements

Use a complete season dataset

Add player performance trends over time

Integrate advanced metrics (xG, xA)

License

This project is for educational purposes. You may use and modify it with proper attribution.

Built with ❤️ by Goutham
