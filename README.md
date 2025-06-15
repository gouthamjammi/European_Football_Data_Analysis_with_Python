---

# ⚽ EuSoccer Data Analysis

Explore real football statistics through this beginner-friendly data analysis project using Python. Dive into key performance metrics of football players and clubs from a sample of the 2020/21 English Premier League season.

---

## 📌 Overview

This project analyzes a dataset containing player statistics such as goals, assists, age, position, club, and more. Using popular Python libraries, we examine patterns and answer questions like:

* Which player scored the most goals?
* How effective are players at converting penalties?
* Which clubs have the youngest squads?
* Who collected the most yellow cards?
* What’s the age distribution among all players?
* Which teams lead in goals and assists?

The goal is to develop data analysis and visualization skills through a real-world sports dataset.

---

## 🛠️ Technologies Used

* **Python 3.x**
* **Jupyter Notebook / JupyterLab**
* **Pandas**
* **NumPy**
* **Matplotlib**
* **Seaborn**

Install the libraries using pip:

```bash
pip install pandas numpy matplotlib seaborn jupyterlab
```

---

## 📂 Project Setup

To run the notebook locally:

1. Install Python from the [official site](https://www.python.org/).
2. Open terminal and install Jupyter + dependencies:

```bash
pip install jupyterlab pandas numpy matplotlib seaborn
```

3. Launch Jupyter in your project directory:

```bash
cd path/to/project
jupyter notebook
```

4. Open the `Football_Data_Analysis.ipynb` notebook and follow along.

---

## 📊 Dataset Description

We use a sample dataset from the English Premier League 2020/21 season, containing player stats like:

* Name, Age, Club, Position
* Goals, Assists, Minutes played
* Penalties taken/scored, Yellow cards

🗂 File: `EPL_20_21_sample.csv`

---

## 🔍 What’s Inside the Notebook?

The notebook walks through these steps:

### 🔹 Data Loading & Exploration

* Preview and understand the structure of the dataset
* Identify missing values and get summary stats

### 🔹 Feature Engineering

* Create new columns like:

  * **Minutes per Match**
  * **Goals per Match**

### 🔹 Visual Analysis

* Penalty success rate (pie chart)
* Nationality and Position breakdown (bar charts)
* Player age distribution (pie chart)
* Club-wise player count and age range (barplot, boxplot)

### 🔹 Performance Analysis

* Top goal scorers & assist providers
* Club-level stats for goals and assists
* Yellow card leaderboard

---

## 📈 Sample Insights

* Penalty conversion rates visualized in a pie chart
* Clubs like Manchester United and Liverpool stand out in total goals and assists
* Most yellow cards came from midfielders aged 25–30
* Youngest average squad: Arsenal
* Top scorer: \[Example Player Name from data]

---

## 🌱 Room for Growth

Potential ideas to expand this project:

* Add expected goals (xG), expected assists (xA), and passing data
* Integrate time-series plots for performance over the season
* Build an interactive dashboard using **Plotly Dash** or **Streamlit**
* Include match-level statistics and historical comparisons

---

## 📘 License

This project is open-source and created for learning purposes. You’re welcome to use, adapt, and build on it.

---

**Made with passion for data and football.**

---
**Made with ❤️ by Goutham**



