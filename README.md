# layoff-data-analysis


# 📊 Layoffs Data Analysis using BigQuery & SQL

This project involves cleaning, transforming, and analyzing a dataset on various company layoffs using **Google BigQuery** and **SQL**. The dataset includes global layoff data from over 1300 events and was used to uncover key patterns and insights.

## 📁 Dataset

- **Source:** [Google Sheet](https://docs.google.com/spreadsheets/d/1FyNqg4anny5IfMVu1FdwpgoEhgLwi5WVBdNy2N-cs34/edit?gid=2049841169#gid=2049841169)
- **Size:** 1351 rows × 9 columns
- **Content:** Layoff details by company, country, industry, date, and number of employees affected.

## 🛠️ Tools Used

- **Google BigQuery:** SQL execution and data storage
- **SQL:** Data cleaning, transformation, and analysis
- **Sublime Text:** SQL development

## 🧹 Data Cleaning

- Missing values found in `Percentage_Laid_Off` and `Funds_Raised`, but they did not impact major analysis.
- Ensured no null rows/columns existed to prevent upload issues in BigQuery.

## 🔍 Analysis Performed

### 1. **Total layoffs by country**
[View Result Table 1 »](https://console.cloud.google.com/bigquery?ws=!1m5!1m4!4m3!1smy-project-no-7-462009!2sdata1234!3sresult_table1)

> United States had the highest total layoffs; Poland had the least.

---

### 2. **Companies that laid off in multiple countries**
[View Result Table 2 »](https://console.cloud.google.com/bigquery?ws=!1m5!1m4!4m3!1smy-project-no-7-462009!2sdata1234!3sresult_table2)

> Uber laid off in 4 countries — the highest.

---

### 3. **Layoff stats by industry (Total, Avg, Max)**
[View Result Table 3 »](https://console.cloud.google.com/bigquery?ws=!1m5!1m4!4m3!1smy-project-no-7-462009!2sdata1234!3sresult_table3)

> Consumer industry led in total layoffs; Sales had the highest average.

---

### 4. **Top 5 months with highest layoffs**
[View Result Table 4 »](https://console.cloud.google.com/bigquery?ws=!1m5!1m4!4m3!1smy-project-no-7-462009!2sdata1234!3sresult_table4)

> Most layoffs occurred in **November 2022**.

---

### 5. **Industry contribution to global layoffs (%)**
[View Result Table 5 »](https://console.cloud.google.com/bigquery?ws=!1m5!1m4!4m3!1smy-project-no-7-462009!2sdata1234!3sresult_table5)

---

### 6. **Events with layoffs above global average**
[View Result Table 6 »](https://console.cloud.google.com/bigquery?ws=!1m5!1m4!4m3!1smy-project-no-7-462009!2sdata1234!3sresult_table6)

> 246 out of 1351 events exceeded the average.

---

### 7. **Months below average layoff totals**
[View Result Table 7 »](https://console.cloud.google.com/bigquery?ws=!1m5!1m4!4m3!1smy-project-no-7-462009!2sdata1234!3sresult_table7)

---

### 8. **Top layoff company per industry**
[View Result Table 8 »](https://console.cloud.google.com/bigquery?ws=!1m5!1m4!4m3!1smy-project-no-7-462009!2sdata1234!3sresult_table8)

> OneTrust led layoffs in both Security and Legal sectors.

---

### 9. **Companies with names starting/ending with "Tech"**
[View Result Table 9 »](https://console.cloud.google.com/bigquery?ws=!1m5!1m4!4m3!1smy-project-no-7-462009!2sdata1234!3sresult_table9)

> Found: TechTarget, BeeTech, PuduTech, BloomTech

---

### 10. **Categorizing layoff sizes (Single Events & Aggregated)**
[View Result Table 10 »](https://console.cloud.google.com/bigquery?ws=!1m5!1m4!4m3!1smy-project-no-7-462009!2sdata1234!3sresult_table10)  
[View Result Table 11 »](https://console.cloud.google.com/bigquery?ws=!1m5!1m4!4m3!1smy-project-no-7-462009!2sdata1234!3sresult_table11)

> Categories: Small (<100), Medium (100–999), Large (1000+)

---

### 11. **Industry-wise ranking and average of layoffs per company**
[View Result Table 13 »](https://console.cloud.google.com/bigquery?ws=!1m5!1m4!4m3!1smy-project-no-7-462009!2sdata1234!3sresult_table13)

---

### 12. **Year-over-year delta in layoffs by country**
[View Result Table 12 »](https://console.cloud.google.com/bigquery?ws=!1m5!1m4!4m3!1smy-project-no-7-462009!2sdata1234!3sresult_table12)

> The U.S. saw the largest jump in layoffs from 2021 to 2022, followed by India and Canada.

---

-- SQL queries have been attached in the code.

## 📌 Conclusion

This analysis provided critical insights into layoff patterns by:
- Country and industry
- Time (monthly and yearly)
- Company behavior
- Magnitude of layoffs

It demonstrates how structured SQL analysis in BigQuery can surface real-world trends from raw business data.
