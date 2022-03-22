# OLAP-and-BI

For using SQL on Mac, was used Docker, where SQL Server was installed.

Instructions to install SQL Server on Mac:
https://www.quackit.com/sql_server/mac/install_sql_server_on_a_mac.cfm

Steps to install SQL Server via Docker:

**1. Install Docker (memory allocation 4 GB)**

**2. Pull the SQL Server image in Terminal**
  <p>docker pull mcr.microsoft.com/mssql/server:2019-latest<br>
  
  Latest version:
  https://hub.docker.com/_/microsoft-mssql-server</p>

**3. Launch the SQL Server Image** 
  <p>docker run -d --name Homer -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=myPassw0rd' -p 1433:1433 mcr.microsoft.com/mssql/server:2019-latest</p>

**4. Check the Docker container (optional)**
   <p>docker ps (or docker ps -all)</p>
   
To access SQL Server was used DBeaver management tool.

And as a database was used AdventureWorks2019.bak


## Tasks

#### Task 1

Create table in Microsoft Exel, using data from AdventureWorks2019-database. 

Can be used:

SELECT
  WorkOrderID,
  LocationID, 
  ProductID, ActualStartDate,
  ActualCost

FROM [Production].[WorkOrderRouting]
<style>ORDER BY{color:Blue;}</style>  
+  ActualStartDate, ProductID


#### Task 2

Create your own BD, includign fact and dimension-tables, using Star-schema.
