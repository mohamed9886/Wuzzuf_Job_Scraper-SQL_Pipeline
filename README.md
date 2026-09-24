# 🕷️ Wuzzuf Job Scraper & SQL Pipeline

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Selenium](https://img.shields.io/badge/Selenium-43B02A?style=for-the-badge&logo=selenium&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![SQL Server](https://img.shields.io/badge/SQL_Server-CC2927?style=for-the-badge&logo=microsoft-sql-server&logoColor=white)

## 📌 Project Overview
This project is an automated **Web Scraping and Data Integration Pipeline** designed to extract job market data from **Wuzzuf.net**, one of the leading job portals in the Middle East. The script utilizes **Selenium WebDriver** to bypass anti-bot protections, navigates through multiple paginated results for highly targeted tech roles, and stores the cleansed dataset into a **Microsoft SQL Server** database.

## 🚀 Key Features & Pipeline Architecture

### 1. Automated Web Scraping (Selenium) 🕵️‍♂️
- **Targeted Roles:** Dynamically searches for specific high-demand roles: *Data Engineer, Data Science, AI Developer, and Machine Learning Engineer*.
- **Anti-Bot Evasion:** Configured Chrome WebDriver options (`--disable-blink-features=AutomationControlled`, `--no-sandbox`) to mimic human behavior and bypass Wuzzuf's automated scraping protections.
- **Dynamic DOM Navigation:** Handled HTML/DOM elements and automated the "Next Page" clicks to extract data across multiple paginated results.

### 2. Data Transformation (Pandas) 🔄
- **Data Cleansing:** Extracted raw text fields and handled missing values using `try/except` blocks to prevent script termination on empty HTML tags.
- **Deduplication:** Converted the list of dictionaries into a `pandas` DataFrame, removed duplicate job postings based on unique Job URLs, and exported the raw data to a CSV file (`wuzzuf jobs.csv`) for backup.

### 3. Database Loading (SQL Server) 📤
- Engineered a SQL schema (`wuzzuf_secured`) to house the scraped data.
- Established a secure connection to a local **SQL Server** using `pyodbc` and `python-dotenv`.
- Executed batch inserts (`executemany`) to load the structured job data seamlessly into the database for further analytical querying.

## 🗂️ Data Dictionary

| Column Name | Description |
|---|---|
| `job_number` | Sequential ID tracking the extracted job |
| `job_title` | The official job title (e.g., Senior Data Engineer) |
| `job_href` | The URL link directly to the job posting |
| `job_company` | The name of the hiring company |
| `job_location` | City and country of the job |
| `job_type` | Work type (e.g., Full Time/On-site, Remote) |
| `job_exp` | Required years of experience |
| `job_category` | The search keyword used to find the job |

## 🛠️ Technologies & Libraries Used
- **Language:** Python 3
- **Web Scraping:** `selenium`, `webdriver`
- **Data Manipulation:** `pandas`
- **Database Connection:** `pyodbc`
- **Environment Management:** `python-dotenv`
- **Database:** Microsoft SQL Server

