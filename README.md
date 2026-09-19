# The Analysis:

## 1. What are thr most demended skills for the top 3 most popular data roles? 

To find the most demanded skiils for the top 3 most popular data roles. 
I filtred out those positions by wich ones were the most popular, 
and got the top 5 skills for these top 3 roles.
this query highlights the most popular job titles and their top skiils, 
showing which skills, I should pay attention to depending on the role I'm targeting.

view my notebook with detailed steps here: [2_Slill_Demand.ipynb](Project\2_Skill_Demand.ipynb)

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