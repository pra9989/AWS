1) what is AWS glue and what is it used for ?
2) AWS Glue components and console walkthrough
3) Prep-for hands on Lab
4) AWS Glue data catalog - databases & tables
5) AWS Glue Data catalog - crawlers and connections
6) AWS glue ETL - Glue jobs
7) AWS glue ETL - Triggers
   https://www.youtube.com/watch?v=weWeaM5-EHc&t=862s
Glue: It is a fully managed ETL service by AWS.
Has two main features - Data Catalog and spark ETL -Engine
Data Catalog: Persistent technical metadata store can connect to 70 different data sources and manage your data in a cnetralized data catalog.
ETL Engine: Visually create run, and monitor extract transform and load(ETL) pipelines to load data into your data lakes spark inbuilt.

AWS Glue Components
AWS Glue data catalog 
  1) database
  2) tables
  3) crawlers
  4) connections
AWS Glue ETL
  1) ETL Jobs
  2) Triggers
  3) Workflows
Crawler is a program that connects to the data source and automatically scans data in various data sources to determine its schema and create metadata tables in the AWS glue data catalog.
AWS Glue ETL jobs
ETL job to transform your data
Leverage the power of spark
serverless
create the ETL Jobs visually or bring your own script with bussiness logic
sources, transforms, target, popular
transform > change schema, join, sql query, aggregrate, drop feilds, custom transform, drop duplicates
<img width="1245" height="808" alt="image" src="https://github.com/user-attachments/assets/4c0c7ec6-3223-4392-9c0b-8be57d6451db" />
glue will automatically generate the script when we select it visually our flow
<img width="1787" height="726" alt="image" src="https://github.com/user-attachments/assets/7d687427-5126-4e7e-98fd-fe5bbbd83196" />


<img width="1775" height="590" alt="image" src="https://github.com/user-attachments/assets/5d7f9833-c876-44c0-a241-a84f662f715f" />
<img width="1693" height="751" alt="image" src="https://github.com/user-attachments/assets/13376875-e4a4-4d6e-ac38-5742908d908f" />
Triggers

<img width="1836" height="764" alt="image" src="https://github.com/user-attachments/assets/a70aff2c-f422-43dd-ab16-d9c54fb84e6f" />
<img width="1755" height="748" alt="image" src="https://github.com/user-attachments/assets/6d96fff7-e542-467b-a73b-e70719169601" />
<img width="1639" height="834" alt="image" src="https://github.com/user-attachments/assets/8fe5490b-8024-4d06-9edf-6a4860a86ce7" />


