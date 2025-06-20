-- Counting the number of companies and the total number of people laid off in all those companies, which country's companies laid off the most

```sql
SELECT Country, COUNT(Company) AS total_companies, SUM(Total_Laid_Off) AS All_laid_off
FROM `data1234.layoffs_table`
GROUP BY Country
ORDER BY All_laid_off
```

-- Companies from United States laid off the most and the least laid off were from Poland

-- Countries that laid off employees in more than one country

```sql
SELECT DISTINCT Company, COUNT(DISTINCT Country) AS in_countries
FROM data1234.layoffs_table
GROUP BY Company
HAVING in_countries > 1
```

-- Uber was the only company that laid off in 4 countries

-- Computing the total, average and maximum employees laid off for each industry, sorting them in decreasing order by total employees laid off

```sql
SELECT Industry, SUM(Total_Laid_Off) AS all_laid_off, ROUND(AVG(Total_Laid_Off),2) AS avg_laid_off, MAX(TotaL_Laid_Off) AS max_laid_off
FROM data1234.layoffs_table
GROUP BY Industry
ORDER BY all_laid_off DESC
```

-- Consumer indutry laid off the most people while Manufacturing laid off the least, highest average observed was for Sales industry

-- Finding the top 5 months (YYYY-MM) across the entire dataset with the highest total layoffs

```sql
SELECT FORMAT_DATE('%Y-%m', DATE) AS month, SUM(Total_Laid_Off) AS all_laid_off
FROM `data1234.layoffs_table`
GROUP BY month
ORDER BY all_laid_off DESC
LIMIT 5
```

-- Most layoffs happened in November,2022

-- Computing the global percentage of layoffs per Industry ->(Industry_total/Global total)*100

```sql
SELECT Industry, 
ROUND((SUM(Total_Laid_Off)/(SELECT SUM(Total_Laid_Off) FROM `data1234.layoffs_table`))*100,2) AS percentage_laid_off
FROM `data1234.layoffs_table`
GROUP BY Industry
```

-- Identifying layoff events that exceeded the overall average of all events

```sql
SELECT Company, Total_Laid_Off AS big_number
FROM `data1234.layoffs_table`
WHERE Total_Laid_Off > (SELECT AVG(Total_Laid_Off) FROM `data1234.layoffs_table`)
```

-- There are 246 such events out of total 1351 events

-- Months where total layoffs were below the dataset’s monthly average

```sql
WITH monthly_layoffs AS
(
  SELECT FORMAT_DATE('%Y-%m', DATE) AS month, SUM(Total_Laid_Off) AS monthly_total
  FROM `data1234.layoffs_table`
  GROUP BY month
),
average_monthly AS
(
  SELECT AVG(monthly_total) AS average FROM monthly_layoffs
)
SELECT m.month, m.monthly_total
FROM monthly_layoffs AS m
JOIN average_monthly AS a
ON m.monthly_total < a.average
ORDER BY m.month
```

-- Finding companies per industry with the maximum layoff number
-- Using window function and common table expression

```sql
WITH data AS
(
  SELECT DISTINCT Industry,
  Company,Total_Laid_Off,
  RANK() OVER (PARTITION BY Industry ORDER BY Total_Laid_Off DESC) AS rank
  FROM `data1234.layoffs_table`
)
SELECT Industry, Company FROM data
WHERE rank = 1
```

-- OneTrust laid off the most from both the Security and Legal industries

-- Counting companies whose name starts with "Tech" or ends with "Tech"

```sql
SELECT Company
FROM `data1234.layoffs_table`
WHERE REGEXP_CONTAINS(Company, r'^Tech') OR REGEXP_CONTAINS(Company, r'Tech$')
```

-- TechTarget, BeeTech, PuduTech, BloomTech

-- Categorizing lay off size on the basis of the number of people laid off
-- First for single events

```sql
SELECT Company, Total_Laid_Off,
(CASE WHEN Total_Laid_Off < 100 THEN 'Small'
      WHEN Total_Laid_Off >= 100 AND Total_Laid_Off <= 999 THEN 'Medium'
      ELSE 'Large' END) AS Lay_Off_Size
      FROM `data1234.layoffs_table`
```

--Now for entire layoff event

```sql
SELECT Company, SUM(Total_Laid_Off) AS SUM_Total_Lay_Off, COUNT(DISTINCT Country) AS number_of_countries, 
(CASE WHEN SUM(Total_Laid_Off) < 500 THEN 'Small'
      WHEN SUM(Total_Laid_Off) >= 500 AND SUM(Total_Laid_Off) <= 999 THEN 'Medium'
      ELSE 'Large' END) AS Total_Lay_Off_Size
      FROM `data1234.layoffs_table`
      GROUP BY Company
```

-- Calculating the 1)rank of each layoff event within the industry on the basis of the layoff size and the 2)average layoff size of the industry

```sql
SELECT Company, Industry,
RANK() OVER (PARTITION BY Industry ORDER BY Total_Laid_Off) AS Industry_Rank,
ROUND(AVG(Total_Laid_Off) OVER (PARTITION BY Industry),2) AS Avg_Industry_Layoff
FROM `data1234.layoffs_table`
```

-- Arranging the entries as per the highest difference observed in the sum head count laid off in the year

```sql
WITH data AS
( 
  SELECT Country,
  EXTRACT(YEAR FROM Date) AS year,
  SUM(Total_Laid_Off) AS sum_total_laid_off
  FROM `data1234.layoffs_table`
  GROUP BY Country, year
  ORDER BY Country
),
yearly_delta AS
(
  SELECT curr.Country,
  curr.year AS layoff_year,
  curr.sum_total_laid_off AS current_year_sum,
  prev.sum_total_laid_off AS previous_year_sum,
  (curr.sum_total_laid_off - prev.sum_total_laid_off) AS year_delta
  FROM data AS curr
  JOIN data AS prev
  ON curr.Country = prev.Country AND
  curr.year = prev.year + 1
)
SELECT * FROM yearly_delta
ORDER BY year_delta DESC
```

-- Highest increase in lay off was observed from 2021 to 2022 in United States, followed by India and Canada in the same two years
