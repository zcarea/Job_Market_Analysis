# The Analysis:

## 1. What are the most demended skills for the top 3 most popular data roles? 

To find the most demanded skills for the top 3 most popular data roles. 
I filtred out those positions by which ones were the most popular, 
and got the top 5 skills for these top 3 roles.
this query highlights the most popular job titles and their top skills, 
showing which skills, I should pay attention to depending on the role I'm targeting.

View my notebook with detailed steps here: [2_Skill_Demand.ipynb](Project\2_Skill_Demand.ipynb)

## Visualize Data
 ``` Python
fig, ax = plt.subplots(len(job_titles), 1)

sns.set_theme(style='ticks')

for i, job_title in enumerate(job_titles):
    df_plot = df_skills_perc[df_skills_perc['job_title_short'] == job_title].head(5)

    sns.barplot(data=df_plot, x='skill_percent', y='job_skills', ax=ax[i], hue='skill_count', palette='dark:b_r', legend=False)
    ax[i].set_title(job_title)
    ax[i].set_ylabel('')
    ax[i].set_xlabel('')
    ax[i].set_xlim(0, 78)

    for n, v in enumerate(df_plot['skill_percent']):
        ax[i].text(v + 1, n, f'{v:.0f}%',va='center')

    if i != len(job_title) - 1:
        ax[i].set_xticks([])
    
    fig.suptitle('Likelihood of Skills Requested in US Job Posting', fontsize=15)
    fig.tight_layout(h_pad=0.5) #Fix overlapping subplots
 ```

 ### Results 
 ![Visualization of Top Skills](Project\Images\skill_demand_all_data_roles.png)

### Insights
- Python is a versatile skill, highly demanded across all three roles, but most prominently for Data Scientists (72%) and Data Engineers (65%).
- SQL is the most requested skill for Data Analysts and Data Scientistse with it in over half the job postings for both roles. For Data Engineerse Python is the most sought-after skille appearing in 68% of job postings.
- Data Engineers require more specialized
technical skills (AWSe Azure, Spark) compared to Data Analysts and Data Scientists who are expected to be proficient in more general data management
and analysis tools (Excel, Tableau).

## 2. How are in-demand skills trending for Data Analysts?

### Visualize Data

```python

from matplotlib.ticker import PercentFormatter

df_plot = df_DA_US_percent.iloc[:,:5]
sns.lineplot(data=df_plot, dashes=False, palette='tab10', legend='full')

plt.gca().yaxis.set_major_formatter(PercentFormatter(decimals=0))

plt.show()

```
### Results 
![Trending Skills for Data Analysts in the US](Project\Images\Skills_trend_DA.png)
*Bar graph visualizing the trending top skills for data analysts in the US in 2023.* 

- SQL remains the most consistently demanded skill throughout the year, although it shows agradual decrease in demand. 
- Excel experienced a significant incrase in demand starting around September, surpassing both Python and Tabeau by the end of the year.
- Both Python and Tableau show relatively stable demand throughout the year with some fluctuations but remain essential skills for data analysts.
Power BI, while less demanded compared to the others, shows a slight upward trend towards the year's end.