# SQL Data Cleaning Project

## Table of Contents
1. [Data Structure and Overview](#data-structure-and-overview)
2. [Tools](#tools)
3. [Why Data Cleaning?](#why-data-cleaning)
4. [Executive Summary](#executive-summary)
5. [Insights Deep Dive](#insights-deep-dive)
   - [Features Implemented](#features-implemented)
   - [Key Cleaning Techniques](#key-cleaning-techniques)
   - [SQL Code Snippet](#sql-code-snippet)
6. [Limitations](#limitations)
7. [References](#references)

## Data Structure and Overview
This project focuses on **cleaning a raw dataset of layoffs** using **SQL**. The dataset contained **inconsistencies, missing values, duplicates, and incorrect formats**, which were addressed through structured SQL queries.

## Tools
- **SQL (Structured Query Language)**: For data cleaning and transformation.
- **MySQL**: Database management system used for storing and manipulating data.
- **CSV Format**: Used for storing both raw and cleaned datasets.
- **Excel**: For additional data validation and visualization.

## Why Data Cleaning?
Data cleaning is essential for ensuring data quality, which leads to **better decision-making, more accurate analysis, and improved machine learning models**. The process helps in:
- **Removing inconsistencies** in data entries.
- **Handling missing values** to ensure completeness.
- **Standardizing formats** for better readability and processing.
- **Eliminating duplicates** to avoid redundancy.

## Executive Summary
The dataset originally contained **numerous errors**, such as inconsistent formatting, missing values, and incorrect data types. Through SQL queries, the dataset was **cleaned, formatted, and prepared** for analysis. The project demonstrates:
- **Use of SQL queries for efficient data transformation**
- **Handling missing values and duplicates effectively**
- **Applying best practices for data integrity**

## Insights Deep Dive
### Features Implemented:
- **Raw Data Before Cleaning**:
  The dataset initially contained missing values, duplicate entries, and unstandardized text formats.
  
  ![Raw Data](https://raw.githubusercontent.com/Fathiat-data-portfolio/Fathiat_Data_Entry_Portfolio/main/layoffs.csv)

- **Cleaned Data After Processing**:
  After executing the SQL cleaning queries, the dataset became structured, free from duplicates, and ready for analysis.
  
  ![Cleaned Data](https://raw.githubusercontent.com/Fathiat-data-portfolio/Fathiat_Data_Entry_Portfolio/main/Layoffs%20dataset%20cleaned%20in%20sql.csv)

### Key Cleaning Techniques:
1. **Removed Duplicates** using `DELETE` and `DISTINCT` functions.
2. **Handled Missing Values** by replacing them with appropriate placeholders.
3. **Formatted Date Columns** to a standard format.
4. **Standardized Text Entries** using `LOWER()` and `TRIM()` functions.
5. **Validated Numerical Data** by checking constraints and outliers.

### SQL Code Snippet:
```sql
-- Removing duplicate rows based on company and date
DELETE FROM layoffs
WHERE id NOT IN (
    SELECT MIN(id) FROM layoffs GROUP BY company, date
);

-- Standardizing text formatting
UPDATE layoffs
SET industry = LOWER(TRIM(industry));

-- Handling missing values
UPDATE layoffs
SET total_laid_off = COALESCE(total_laid_off, 0)
WHERE total_laid_off IS NULL;
```

## Limitations
- **Incomplete Data**: Some missing values had to be approximated.
- **Manual Review Still Needed**: While SQL cleans most issues, manual verification is still recommended.
- **Data Source Reliability**: The dataset accuracy depends on its original source.

## References
- [SQL Data Cleaning Techniques](https://www.sqlshack.com/sql-data-cleaning-techniques/)
- [MySQL Documentation](https://dev.mysql.com/doc/)
- [CSV Best Practices](https://www.data-to-fish.com/csv-python/)
