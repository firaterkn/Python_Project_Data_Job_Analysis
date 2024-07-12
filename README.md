# Overview

Welcome to analysis of the data job market, focusing on data analyst roles. This project was created out of a desire to navigate and understand the job market more effectively. It delves into the top-paying and in-demand skills to help find optimal job opportunities for data analysts.

The data sourced from Hugging Face which provides a foundation for the analysis, containing detailed information on job titles, salaries, locations, and essential skills. Through a series of Python scripts, key questions explored, such as the most demanded skills, salary trends, and the intersection of demand and salary in data analytics.


# The Questions

The questions to be answered in the project are below:

    1. What are the skills most in demand for the top 3 most popular data roles?
    2. How are in-demand skills trending for Data Analysts?
    3. How well do jobs and skills pay for Data Analysts?
    4. What are the optimal skills for data analysts to learn? (High Demand AND High Paying)



# Tools Used

For the deep dive into the data analyst job market, the power of a few key tools were leveraged

    1. Python: The backbone of the analysis, allowing to analyze the data and find critical insights. Also following Python libraries were used:

        1.1 Pandas Library: Analyzing the data.
        1.2 Matplotlib Library: Visualizing the data.
        1.3 Seaborn Library: To create more advanced visuals.
        
    2. Jupyter Notebooks: Tool used to run Python scripts that allow easy addition of notes and analysis.

    3. Visual Studio Code: Go-to for executing the Python scripts.
    
    4. Git & GitHub: Essential for version control and sharing the Python code and analysis, ensuring collaboration and project tracking.


# Data Preparation and Cleanup    

This section outlines the steps taken to prepare the data for analysis, ensuring accuracy and usability.


## Import & Clean Up Data

Start by importing necessary libraries and loading the dataset, followed by initial data cleaning tasks to ensure data quality.


```python
# Import Libraries
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np
import ast
import seaborn as sns

# Load Data
df = pd.read_csv("C:\\Users\\ERKAN\\Downloads\\data_jobs.csv")

# Data Cleanup
df["job_posted_date"] = pd.to_datetime(df.job_posted_date)
df["job_skills"] = df["job_skills"].apply(lambda x: ast.literal_eval(x) if pd.notna(x) else x)

```


# Filter US Jobs

To focus the analysis on the U.S. job market, filters applied to the dataset, narrowing down to roles based in the United States.

```python

df_US = df[df.job_country == "United States"]

```

# The Analysis

Each Jupyter notebook for this project aimed at investigating specific aspects of the data job market. Each question was approached as follows:


### 1. What are the most demanded skills for the top 3 most popular data roles?

To find the most demanded skills for the top 3 most popular data roles. The data filtered out those positions by which ones were the most popular, and got the top 5 skills for these top 3 roles. This query highlights the most popular job titles and their top skills, showing which skills people should pay attention to depending on the role they are targeting.

View the notebook with detailed steps here: [2_Skills_Demand.ipynb](https://github.com/firaterkn/Personal_Python_Project/blob/main/3_Project/2_Skills_Demand.ipynb)


# Visusalize Data

```python

fig, ax = plt.subplots(len(job_titles), 1, figsize= (10,6))


for i, job_title in enumerate(job_titles):
    df_plotter = df_skill_percent[df_skill_percent.job_title_short == job_title].head()
    bars = sns.barplot(data=df_plotter, y="job_skills", x="skill_percent", ax=ax[i], hue="skill_count", ci=None, dodge=False, palette="dark:b")
    
plt.show()

```

# Result
![Visualization for the code](https://github.com/firaterkn/Personal_Python_Project/blob/main/3_Project/output2.png?raw=true)

Bar graph visualizing the salary for the top 3 data roles and their top 5 skills associated with each.

# Insights About the Graph

- SQL is the most requested skill for Data Analysts and Data Engineers, with it in over half the job postings for both roles. For Data Scientist, Python is the most sought-after skill, appearing in 72% of job postings.
    
- Data Engineers require more specialized technical skills (AWS, Azure, Spark) compared to Data Analysts and Data Scientists who are expected to be proficient in more general data management and analysis tools (Excel, Tableau).
    
- Python is a versatile skill, highly demanded across all three roles, but most prominently for Data Scientists (72%) and Data Engineers (65%).



### 2. How are in-demand skills trending for Data Analysts?

To find how skills are trending in 2023 for Data Analysts, data analyst positions were filtered and grouped the skills by the month of the job postings. This got the top 5 skills of data analysts by month, showing how popular skills were throughout 2023.

View the notebook with detailed steps here: [3_Skills_Trend.ipynb](https://github.com/firaterkn/Personal_Python_Project/blob/main/3_Project/3_Skills_Trend.ipynb)


```python
from matplotlib.ticker import PercentFormatter

df_plot = df_DA_US_percent.iloc[:, :5]
sns.lineplot(data=df_plot, dashes=False, palette='tab10')

plt.gca().yaxis.set_major_formatter(PercentFormatter(decimals=0))

plt.show()
```

# Result

![Visualization for the code](https://github.com/firaterkn/Personal_Python_Project/blob/main/3_Project/output3.png)

Line graph visualizing the trending top skills for data analysts in the US in 2023.

# Insights About the Graph

- SQL remains the most consistently demanded skill throughout the year, although it shows a gradual decrease in demand.

- Excel experienced a significant increase in demand starting around June, surpassing both Python and Tableau by the end of the year.

- Both Python and Tableau show relatively stable demand throughout the year with some fluctuations but remain essential skills for data analysts. 

- Power BI, while less demanded compared to the others, shows a slight upward trend towards the year's start.

