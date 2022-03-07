# OLAP-and-BI

For using SQL on Mac, was used Docker, where SQL Server was installed

Steps to install SQL Server via Docker:

1. Install Docker (memory allocation 4 GB)

2. Pull the SQL Server image in Terminal
  ####docker pull mcr.microsoft.com/mssql/server:2019-latest
  
  Latest version:
  https://hub.docker.com/_/microsoft-mssql-server

3. Launch the SQL Server Image 
  docker run -d --name Homer -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=myPassw0rd' -p 1433:1433 mcr.microsoft.com/mssql/server:2019-latest

4. Check the Docker container (optional)
   docker ps (or docker ps -all)
   
To access SQL Server was used DBeaver management tool.

