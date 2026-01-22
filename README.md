
# Job Market Data Pipeline  
## Table of Contents

1. [Project Overview](#1-project-overview)
2. [Pipeline Stages](#2-pipeline-stages)
3. [Information Extracted from the Site](#3-information-extracted-from-the-site)
4. [Overall Pipeline Workflow](#4-overall-pipeline-workflow)
5. [User Input & Dynamic URL Building](#5-user-input--dynamic-url-building)
6. [Web Scraping Process](#6-web-scraping-process)
   - [Main Listings Page Scraping](#61-main-listings-page-scraping)
   - [Job Details Page Scraping](#62-job-details-page-scraping)
7. [Data Cleaning & Modeling](#7-data-cleaning--modeling)
8. [Output & Usage](#8-output--usage)
9. [Project Deliverables](#9-project-deliverables)


---

## 1. Project Overview

This project implements an **end-to-end data pipeline** to collect, clean, and structure **job market data** from an online job portal (**Wuzzuf**), which **does not provide a public API**.

The pipeline demonstrates how to:

- Scrape job data from a real-world website
- Handle both **static and dynamic web content**
- Clean and normalize **raw scraped data**
- Design **fact-like and dimension tables** suitable for analysis

### Project Goal
Transform raw job postings into **structured, analysis-ready datasets** that enable meaningful **job market insights**.

---

## 2. Pipeline Stages

The project follows a clear, step-by-step pipeline:

1. **User Input & Selection**
2. **Dynamic URL Building**
3. **Pagination Handling**
4. **Web Scraping**
   - Main listings pages
   - Individual job detail pages
5. **Data Cleaning & Transformation**
6. **Data Modeling**
   - Fact-like tables
   - Dimension tables
7. **Data Saving**

---

## 3. Information Extracted from the Site

The pipeline extracts structured job-related information, including:

### Main Job Information 

- Job Title  
- Company Name  
- Location  
- Job Type (Full-time / Part-time)  
- Job Link  

### Detailed Job Information 

- Job Description  
- Job Requirements  
- Required Experience  
- Career Level  
- Skills & Tools  
- Job Categories  

---

## 4. Overall Pipeline Workflow

The workflow of the pipeline can be summarized as follows:

1. User selects job parameters (country & job title)
2. A search URL is dynamically generated
3. Job listings are scraped page by page
4. Each job link is visited individually
5. Raw data is cleaned and structured
6. Final datasets are saved for analysis

---

## 5. User Input & Dynamic URL Building

Using a static URL limits scraping to a single job title and country.

### Problem
- Hard-coded parameters
- No flexibility for different search scenarios

### Solution
The pipeline allows dynamic user input:

- **Country**
- **Job Title**

Based on user selection, the search URL is automatically generated.

### Supported Input Cases
- Specific country + job title  
- All countries + job title  
- Invalid input → default values applied  

---

## 6. Web Scraping Process

### 6.1 Main Listings Page Scraping

From the main job listings pages, the pipeline extracts:

- Job overview information
- Links to individual job detail pages

---

### 6.2 Job Details Page Scraping

Each job link is visited to extract:

- Job description
- Job requirements
- Skills & tools
- Career level
- Experience requirements

---

## 7. Data Cleaning & Modeling

### Raw Data

After scraping, multiple raw DataFrames are produced, including:

- Main listings data
- Job details data
- Description and requirements data

### Data Cleaning

The cleaning process includes:

- Handling missing values
- Removing unnecessary characters
- Dropping irrelevant columns
- Standardizing text formats

### Data Modeling & Normalization

Some attributes (such as **Skills** and **Job Categories**) contain **multiple values per job**, which is not suitable for analysis.

**Solution:**
- Normalize the data into separate **dimension tables**
- One skill per row
- One category per row
- Tables are linked using the job URL

### Final Output

- Cleaned fact-like datasets
- Separate dimension tables for skills and categories
- Fully analysis-ready data

---

## 8. Output & Usage

The final datasets can be used for:

- SQL-based analysis
- Power BI dashboards
- Job market trend analysis

### Data Saving Path
A relative path (`data/output`) is used to ensure the project runs seamlessly on any machine without modifying file paths.

---

## 9. Project Deliverables

- Jupyter Notebook containing the full pipeline
- Project presentation (PDF)
- Organized images for scraping and workflow explanation
- Clean and reusable project structure


