<h2 align="center">
<img src="https://res.cloudinary.com/web-hcmus/image/upload/v1673620680/logo_blkwpx.png" alt="Logo" width="25%">

  BUSINESS INTELLIGENCE PROJECT
</h2>


<br>

## Decription Project
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
| Name     | Reasons to use                                                                                         |
|----------|-------------------------------------------------------------------------------------------------------|
| [SSIS](https://learn.microsoft.com/en-us/sql/integration-services/install-windows/install-integration-services?view=sql-server-ver16)    | Manage ETL process, easy to use (just Drag and Drop), user-friendly interface                         |
| [SSAS](https://learn.microsoft.com/en-us/analysis-services/instances/install-windows/install-analysis-services?view=asallproducts-allversions)     | Manage OLAP CUBE for analysis and mining data for predict                                               |
| [SSMS](https://learn.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-ver16)   | Manage Data Warehouse, NDS and Metadata, automatic scheduling for ETL process, monitoring ETL process |
| [Power BI](https://powerbi.microsoft.com/en-us/downloads/) | Create Dashboard Reports for statistic                                                                 |

<br>

## Result Images
### NDS Design (Normalize Data Store)
![NDS Design!](https://res.cloudinary.com/web-hcmus/image/upload/v1673620485/NDS.drawio_yjhnj9.png "NDS Design")

### DDS Design (Dimensional Data Store)
![DDS Design!](https://res.cloudinary.com/web-hcmus/image/upload/v1673620487/DDS.drawio_jgrhih.png "DDS Design")

### OLAP CUBE
![OLAP CUBE!](https://res.cloudinary.com/web-hcmus/image/upload/v1673621603/cube1_wsdkxm.png "OLAP CUBE")
![OLAP CUBE!](https://res.cloudinary.com/web-hcmus/image/upload/v1673621603/cube2_zglv4m.png "OLAP CUBE")

### Dashboard Report
Statistics of the number of infections, deaths, and recoveries of the Covid-19 epidemic by each PHU in each year.
![](https://res.cloudinary.com/web-hcmus/image/upload/v1673665263/req1_xohbu8.png)
Statistics of Severity of the Covid-19 epidemic by PHU and by quarters in each year.
![](https://res.cloudinary.com/web-hcmus/image/upload/v1673665263/req2_er94fe.png)
Statistics of total number of deaths by Gender and Age Group by years.
![](https://res.cloudinary.com/web-hcmus/image/upload/v1673665263/req3_xcyqld.png)
Statistics of infections and deaths by Severity by Day of Month of years.
![](https://res.cloudinary.com/web-hcmus/image/upload/v1673665263/req4_fvek2o.png)
Statistics of infections, deaths by Severity, region (PHU_Group, City), and number of people vaccinated in years.
![](https://res.cloudinary.com/web-hcmus/image/upload/v1673665263/req5_zdlmk0.png)
Statistics of infections by Severity, outbreak group of each region in years.
![](https://res.cloudinary.com/web-hcmus/image/upload/v1673665264/req6_xipjpx.png)
Assessment of the number of infections and deaths in Ontario by age group, gender and reason of infection
![](https://res.cloudinary.com/web-hcmus/image/upload/v1673665263/req7_zl6x67.png)

### OLAP - [Link Github](https://github.com/HTTT-BI/DATH-OLAP.git)
### Data Mining - [Link Github](https://github.com/HTTT-BI/DATH-DATAMINING.git)

<br>

## Link And Video
[Data Source for testing](https://studenthcmusedu-my.sharepoint.com/:f:/g/personal/19127449_student_hcmus_edu_vn/Eq5dEfPO_1NFttZ4Lz5Q66wBw3ju7dHydu6IarMRe0bR9A?e=KOunuN) 

[Script For Create DB](https://studenthcmusedu-my.sharepoint.com/:f:/g/personal/19127449_student_hcmus_edu_vn/EtCfO6QTMFZDtSEvAAPgPcoBraIZH_AqMVl_OsAYP99QyA?e=hiGfjG)                   

[MDX Query](https://studenthcmusedu-my.sharepoint.com/:f:/g/personal/19127449_student_hcmus_edu_vn/EuzfVPMa7mpClsF6eYzIUGQBiEIKOrrCJTKXkD3vjXa3eQ?e=uXI9Xt)                    

[Video Load From Source System To Stage](https://youtu.be/MkJes25QH6A)

[Video Load From Stage To NDS](https://youtu.be/J_3ziX1aWN4) 

[Video Load From NDS To DDS](https://youtu.be/7v2MKvfZyjw)             

[Video ETL Process](https://youtu.be/5lBuqcZvSZo)                    

[Video Run ETL Automatically](https://youtu.be/1qzFXsCf8n4)            

[Video OLAP CUBE & REPORT](https://youtu.be/jFRxOFOaN9Y)     

[Video DATA MINING](https://youtu.be/gmwkjz8UwSA)                      
