<h2 align="center">
<img src="https://res.cloudinary.com/web-hcmus/image/upload/v1673620680/logo_blkwpx.png" alt="Logo" width="25%">

  BUSINESS INTELLIGENCE PROJECT
</h2>


<br>

## Decription Project
---
Build and analyze data about covid-19 in 2020-2022
1. Analyze data from source system - [Datasource](https://studenthcmusedu-my.sharepoint.com/:f:/g/personal/19127449_student_hcmus_edu_vn/EhjtNkiOYDBEuiA8S2_QTT4BwTxe33EjKCXebngMMwniUw?e=reH6bS)
2. Design Data Warehouse and create ETL Process for: 
    * Statistics of the number of infections, deaths, and recoveries of the Covid-19 epidemic by each PHU in each year.
    * Statistics of Severity of the Covid-19 epidemic by PHU and by quarters in each year.
    * Statistics of total number of deaths by Gender and Age Group by years.
    * Statistics of infections and deaths by Severity by Day of Month of years.
    * Statistics of infections, deaths by Severity, region (PHU_Group, City), and number of people vaccinated in years.
    * Statistics of infections by Severity, outbreak group of each region in years.
    * Assessment of the number of infections and deaths in Ontario by age group, sex and reason of infection
3. Build OLAP CUBE and use MDX query for analysis.
4. Schedule to run ETL automatically.
3. Create Dashboard Reports.
4. Data Mining.

<br>

## Tools
---
| Name     | Reasons to use                                                                                         |
|----------|-------------------------------------------------------------------------------------------------------|
| [SSIS](https://learn.microsoft.com/en-us/sql/integration-services/install-windows/install-integration-services?view=sql-server-ver16)    | Manage ETL process, easy to use (just Drag and Drop), user-friendly interface                         |
| [SSAS](https://learn.microsoft.com/en-us/analysis-services/instances/install-windows/install-analysis-services?view=asallproducts-allversions)     | Manage OLAP CUBE for analysis and mining data for predict                                               |
| [SSMS](https://learn.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-ver16)   | Manage Data Warehouse, NDS and Metadata, automatic scheduling for ETL process, monitoring ETL process |
| [Power BI](https://powerbi.microsoft.com/en-us/downloads/) | Create Dashboard Reports for statistic                                                                 |

<br>

## Result Images
---
### NDS Design (Normalize Data Store)
![NDS Design!](https://res.cloudinary.com/web-hcmus/image/upload/v1673620485/NDS.drawio_yjhnj9.png "NDS Design")
### DDS Design (Dimensional Data Store)
![DDS Design!](https://res.cloudinary.com/web-hcmus/image/upload/v1673620487/DDS.drawio_jgrhih.png "DDS Design")
### OLAP CUBE
![OLAP CUBE!](https://res.cloudinary.com/web-hcmus/image/upload/v1673621603/cube1_wsdkxm.png "OLAP CUBE")
![OLAP CUBE!](https://res.cloudinary.com/web-hcmus/image/upload/v1673621603/cube2_zglv4m.png "OLAP CUBE")

### MDX And Dashboard Report
Statistics of the number of infections, deaths, and recoveries of the Covid-19 epidemic by each PHU in each year.

```
SELECT 
  NON EMPTY (CROSSJOIN ({
    [Dim Day].[Year].[Year]}, 
    [Dim Phu].[Phu Name].[Phu Name])) ON ROWS,
  NON EMPTY ({
    [Measures].[Infected Total], 
    [Measures].[Resolved Total], 
    [Measures].[Fataled Total]}) ON COLUMNS
FROM [Case_Amount_Cube]
```
Statistics of Severity of the Covid-19 epidemic by PHU and by quarters in each year.
```
-- Total number of infections in 1 quarter in 1 year
SELECT 
 NON EMPTY [Measures].[Case Total] ON COLUMNS,
 NON EMPTY [Dim Day].[Year].[Year] * [Dim Day].[Quarter].[Quarter] ON  ROWS
FROM [Severity_Case_Cube];

-- Total number of PHUs with cases in 1 quarter in 1 year
SELECT 
  NON EMPTY [Measures].[Measures].[Phu Total] ON COLUMNS,
  NON EMPTY [Dim Day].[Year].[Year] * [Dim Day].[Quarter].[Quarter] ON ROWS
FROM [Severity_Phu_Cube];

-- Total number of infections of 1 PHU in 1 quarter in 1 year
SELECT 
  NON EMPTY ([Measures].[Infected Total]) ON COLUMNS,
  NON EMPTY ([Dim Day].[Year].[Year] * [Dim Day].[Quarter].[Quarter] * [Dim Phu].[Phu Name].[Phu Name]) ON ROWS
FROM [Case_Amount_Cube];
```
Statistics of total number of deaths by Gender and Age Group by years.
```
SELECT 
  NON EMPTY 
   ([Dim Age].[Age].[Age] * 
   [Dim Gender].[Gender].[Gender] * 
   [Dim Day].[Year].[Year]) ON ROWS,
  NON EMPTY ([Measures].[Fataled Total]) ON COLUMNS
FROM [Case_Amount_Cube]
```
Statistics of infections and deaths by Severity by Day of Month of years.
```
-- Total number of infections in 1 day in 1 month in 1 year
SELECT 
  NON EMPTY ([Measures].[Case Total]) ON COLUMNS,
  NON EMPTY ([Dim Day].[Day].[Day] * [Dim Day].[Month].[Month] * [Dim Day].[Year].[Year]) ON ROWS FROM [Severity_Case_Cube];

-- Total number of PHUs with infections in 1 day in 1 month in 1 year
SELECT 
  NON EMPTY ([Measures].[Phu Total]) ON COLUMNS,
  NON EMPTY ([Dim Day].[Day].[Day] * [Dim Day].[Month].[Month] * [Dim Day].[Year].[Year]) ON ROWS FROM [Severity_Phu_Cube];

-- Total number of infections and deaths in 1 day in 1 month in 1 year
SELECT 
  NON EMPTY ({[Measures].[Infected Total], [Measures].[Fataled Total]}) ON COLUMNS,
  NON EMPTY ([Dim Day].[Day].[Day] * [Dim Day].[Month].[Month] * [Dim Day].[Year].[Year]) ON ROWS
FROM [Case_Amount_Cube];
```
Statistics of infections, deaths by Severity, region (PHU_Group, City), and number of people vaccinated in years.
```
-- Total number of infections in 1 year
SELECT 
 NON EMPTY ([Measures].[Case Total]) ON COLUMNS,
 NON EMPTY ([Dim Day].[Year].[Year]) ON ROWS 
FROM [Severity_Case_Cube];

-- Total number of PHU infected in 1 year
SELECT 
 NON EMPTY ([Measures].[Phu Total]) ON COLUMNS,
 NON EMPTY ([Dim Day].[Year].[Year]) ON ROWS 
FROM [Severity_Phu_Cube];

-- Total number of infections and deaths of an area in 1 year
SELECT 
 NON EMPTY ({[Measures].[Infected Total], [Measures].[Fataled Total]}) ON COLUMNS,
 NON EMPTY ([Dim Day].[Year].[Year] * [Dim Phu].[City Name].[City Name] * [Dim Phu].[Phu Group Name].[Phu Group Name]) ON ROWS
FROM [Case_Amount_Cube];

-- Total number of people vaccinated in 1 region in 1 year
SELECT 
 NON EMPTY ([Measures].[Vaccination Amount]) ON COLUMNS,
 NON EMPTY ([Dim Day].[Year].[Year] * [Dim Phu].[City Name].[City Name] * [Dim Phu].[Phu Group Name].[Phu Group Name]) ON ROWS
FROM [Vaccination_Amount_Cube];
```
Statistics of infections by Severity, outbreak group of each region in years.
```
-- Total number of infections in 1 year
SELECT 
 NON EMPTY ([Measures].[Case Total]) ON COLUMNS,
 NON EMPTY ([Dim Day].[Year].[Year]) ON ROWS
FROM [Severity_Case_Cube];

-- Total number of PHUs with infections in each year
SELECT 
 NON EMPTY ([Measures].[Phu Total]) ON COLUMNS,
 NON EMPTY ([Dim Day].[Year].[Year]) ON ROWS
FROM [Severity_Phu_Cube];

-- Total number of infections by outbreak group of each region in each year
SELECT 
 NON EMPTY ([Measures].[Infectected Amount]) ON COLUMNS,
 NON EMPTY ([Dim Day].[Year].[Year] * [Dim Phu].[City Name].[City Name] *  [Dim Phu].[Phu Group Name].[Phu Group Name] * [Dim Outbreak Group].[Ak Outbreak Group].[Ak Outbreak Group]) ON ROWS
FROM [Outbreak_Infectected_Cube];
```
Assessment of the number of infections and deaths in Ontario by age group, sex and reason of infection
```
SELECT 
 NON EMPTY ({([Dim Age].[Age].[Age], [Dim Gender].[Gender].[Gender], [Dim Exposure].[Exposure].[Exposure])}) ON ROWS,
 NON EMPTY ({[Measures].[Infected Total],[Measures].[Decreased Total], [Measures].[Recovered Total]})       ON COLUMNS
FROM [Ontario_Case_Cube]

```
### Data Mining