---

## ⚽ Premier League 2020–21 Data Exploration with Python

### 👨‍💻 By Goutham

### 🧠 Objective

This project focuses on analyzing performance data from players in the 2020–2021 English Premier League (EPL) season. Using Python, we extract key performance indicators and visualize patterns related to scoring, discipline, age distribution, and club-level contributions.

---

### 📌 Tools Required

Ensure the following software and packages are installed:

* Python ≥ 3.8
* Jupyter Notebook or VS Code with Jupyter support
* Python libraries:

  * `pandas`
  * `numpy`
  * `matplotlib`
  * `seaborn`

---

### 🛠️ Setup Guide

```bash
pip install pandas numpy matplotlib seaborn jupyterlab
```

Run the notebook using:

```bash
jupyter notebook
```

Make sure the file `premier_league_2020_21.csv` is saved in your working directory.

---

## 🧾 Data Overview

The dataset includes stats for players from the 2020–21 EPL season, such as:

* Player names, age, and nationality
* Club associations
* Minutes played, goals, assists
* Penalties attempted/conversions
* Discipline (yellow/red cards)

---

## 🧹 Step-by-Step Analysis

### 1️⃣ Load Packages and Dataset

```python
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt

%matplotlib inline

df = pd.read_csv("premier_league_2020_21.csv")
df.head()
```

---

### 2️⃣ Basic Exploration

```python
df.info()
df.describe()
df.isnull().sum()
```

---

### 3️⃣ Feature Engineering

```python
df["MinutesPerGame"] = (df["Minutes"] / df["Appearances"]).astype(int)
df["GoalsPerGame"] = (df["Goals"] / df["Appearances"]).round(2)
```

---

### 4️⃣ Penalty Analysis

```python
total_goals = df["Goals"].sum()
penalties_made = df["Penalties_Scored"].sum()
penalties_attempted = df["Penalties_Taken"].sum()
```

#### 📊 Penalty Accuracy Pie Chart

```python
missed = penalties_attempted - penalties_made
plt.figure(figsize=(8, 5))
plt.pie([missed, penalties_made], labels=["Missed", "Scored"], colors=["red", "green"], autopct="%.1f%%")
plt.title("Penalty Conversion Rate")
plt.show()
```

---

### 5️⃣ Player Position and Nationality

```python
df["Role"].unique()
top_countries = df["Nationality"].value_counts().head(10)

plt.figure(figsize=(10,5))
sns.barplot(x=top_countries.index, y=top_countries.values, palette="flare")
plt.title("Top Nationalities in EPL 20/21")
plt.xticks(rotation=45)
plt.show()
```

---

### 6️⃣ Squad Size by Club

```python
top_squads = df["Team"].value_counts().nlargest(5)
sns.barplot(x=top_squads.index, y=top_squads.values, palette="coolwarm")
plt.title("Clubs with Largest Squads")
plt.show()

smallest_squads = df["Team"].value_counts().nsmallest(5)
sns.barplot(x=smallest_squads.index, y=smallest_squads.values, palette="mako")
plt.title("Clubs with Smallest Squads")
plt.show()
```

---

### 7️⃣ Age Distribution Analysis

```python
u20 = df[df["Age"] <= 20]
b20_25 = df[(df["Age"] > 20) & (df["Age"] <= 25)]
b25_30 = df[(df["Age"] > 25) & (df["Age"] <= 30)]
o30 = df[df["Age"] > 30]

age_groups = [len(u20), len(b20_25), len(b25_30), len(o30)]
labels = ["≤20", "21–25", "26–30", "30+"]

plt.pie(age_groups, labels=labels, autopct="%.1f%%", colors=sns.color_palette("pastel"))
plt.title("Player Age Groups")
plt.show()
```

---

### 8️⃣ Age per Club (Boxplot)

```python
plt.figure(figsize=(14,6))
sns.boxplot(data=df, x="Team", y="Age")
plt.xticks(rotation=90)
plt.title("Age Range by Club")
plt.show()
```

---

### 9️⃣ Club-Level Scoring & Assists

```python
# Assists by Club
assists = df.groupby("Team")["Assists"].sum().sort_values(ascending=False)
assists.plot(kind="bar", figsize=(12,6), color="skyblue", title="Total Assists per Club")
plt.xticks(rotation=75)
plt.show()

# Goals by Club
goals = df.groupby("Team")["Goals"].sum().sort_values(ascending=False)
goals.plot(kind="bar", figsize=(12,6), color="salmon", title="Total Goals per Club")
plt.xticks(rotation=75)
plt.show()
```

---

### 🔟 Top Performers

```python
# Most Goals
df[['Name', 'Team', 'Goals']].sort_values(by='Goals', ascending=False).head(10)

# Most Assists
df[['Name', 'Team', 'Assists']].sort_values(by='Assists', ascending=False).head(10)

# Most Efficient (Goals per Game)
df[['Name', 'GoalsPerGame', 'Goals']].sort_values(by='GoalsPerGame', ascending=False).head(10)
```

---

### 🟨 Most Yellow Cards

```python
top_yellow = df.sort_values(by="Yellow_Cards", ascending=False).head(10)

plt.figure(figsize=(14,6))
sns.barplot(data=top_yellow, x="Name", y="Yellow_Cards", color="gold")
plt.title("Top 10 Players with Most Yellow Cards")
plt.xticks(rotation=45)
plt.show()
```

---

## 📈 Summary

This project demonstrates how football data can be transformed into performance insights using Python. From basic data exploration to advanced visualizations, we examined:

* Penalty effectiveness
* Age demographics
* Club-based statistics
* Top scorers, assisters, and discipline records

### 👋 Made with Python by Goutham

---

