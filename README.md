# The Analysis

## 1. What are the most demanded skills for the Top 3 most popular data roles?

View my notebook with detailed steps here: [2_Skills_Count.ipynb](Project\2_Skills_Count.ipynb)

## My example code to visualize data
```python
fig, ax = plt.subplots(len(job_titles), 1)


for i, job_title in enumerate(job_titles):
    df_plot = df_skills_perc[df_skills_perc['job_title_short'] == job_title].head(5)
    sns.barplot(data=df_plot, x='skill_percent', y='job_skills', ax=ax[i], hue='skill_count', palette='dark:b_r')
    ax[i].set_title(job_title)
    ax[i].set_ylabel('')
    ax[i].set_xlabel('')
    ax[i].get_legend().remove()
    ax[i].set_xlim(0, 78)
    # remove the x-axis tick labels for better readability
    if i != len(job_titles) - 1:
        ax[i].set_xticks([])

    # label the percentage on the bars
    for n, v in enumerate(df_plot['skill_percent']):
        ax[i].text(v + 1, n, f'{v:.0f}%', va='center')

fig.suptitle('Likelihood of Skills Requested in US Job Postings', fontsize=15)
fig.tight_layout(h_pad=.8)
plt.show()
```
### Results

![Visualization of Top Skills for Data Roles](Project\images\skill_demand_all_data_roles.png)

### Insights

- SQL is a mass tool in Data roles
- Data Scientist uses Python mostly
- Python is less popular tool in Data Analyst Field

## 2. How are in-demand skills trending for Data Analyst?

View my notebook with detailed steps here: [3_Skills_Trend](Project\3_Skills_Trend.ipynb)

### Example Coding
```python
df_plot = df_DA_US_percent.iloc[:, :5]

sns.lineplot(data=df_plot, dashes=False, palette='tab10')
sns.set_theme(style='ticks')
sns.despine()

plt.title('Trending Top Skills for Data Analysts in the US')
plt.ylabel('Likelihood in Job Posting')
plt.xlabel('2023')
plt.legend().remove()
plt.gca().yaxis.set_major_formatter(PercentFormatter(decimals=0))

for i in range(5):
    plt.text(11.2, df_plot.iloc[-1, i], df_plot.columns[i], color='black')

plt.show()
```

### Results

![Visualization of trending skills demand](Project\images\skill_trend.png)

### Insights

- SQL dominates — the foundational skill for querying and working with databases.
- Excel remains strong — traditional but still widely used in business analytics.
- Python is rising steadily — indicating more technical, data-driven analyst roles.
- Visualization tools (Tableau, Power BI) are critical but secondary — showing that visualization is important but built on top of data skills like SQL/Python.
- No skill declined sharply, meaning demand for these tools stayed stable across 2023, with slight dips mid-year (Jul–Sep) — possibly due to fewer job postings during that period.


## 3. How well do jobs and skills pay for Data Analyst?

View my notebook with detailed steps here: [4_Salary_Analysis](Project\4_Salary_Analysis.ipynb)


## 4. What is the most optimal skill to learn for Data Analyst?
