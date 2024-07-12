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

View my notebook with detailed steps here: [2_Skills_Count.ipynb](https://github.com/firaterkn/Personal_Python_Project/blob/main/3_Project/2_Skills_Demand.ipynb)