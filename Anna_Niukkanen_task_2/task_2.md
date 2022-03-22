# Task 2

#### Creating DB based on AdventureWorks2019-db, using Star Schema.

1. First creating Stamp-db, and tables into created db.

Tables: <br>
[dbo].[FctSales] <br>
[dbo].[DmnDate] <br>
[dbo].[DmnOrder] <br>
[dbo].[DmnProduct] <br>

CREATE DATABASE Stamp;

CREATE TABLE [dbo].[FctSales] ( <br>
    SalesOrderID int IDENTITY(1,1) NOT NULL PRIMARY KEY, <br>
    ProductID int NOT NULL, <br>
    OrderQty smallint NOT NULL, <br>
    UnitPrice money NOT NULL, <br>
    ModifiedDate DATE NULL <br>
); <br>

CREATE TABLE [dbo].[DmnDate] (
    ProductID int IDENTITY(1,1) NOT NULL PRIMARY KEY,
    OrderDate DATE NULL,

    -- CONSTRAINT FK_FctSales_DmnDate FOREIGN KEY (OrderDate)     
    -- REFERENCES [dbo].[FctSales] (OrderDate)     
    -- ON DELETE NO ACTION    
    -- ON UPDATE NO ACTION 
);

(DROP TABLE [dbo].[DmnOrder])

CREATE TABLE [dbo].[DmnOrder]( <br>
    SalesOrderID int IDENTITY(1,1) NOT NULL PRIMARY KEY, <br>
    SalesOrderNumber nvarchar(255) NOT NULL, <br>
    AccountNumber nvarchar(255) NOT NULL, <br>
    CreditCardID int, <br>
    OrderDate datetime NOT NULL, <br>
    ModifiedDate datetime NULL <br>
  
    -- CONSTRAINT FK_FctTable_DmnOrder FOREIGN KEY (SalesOrderID)     
    -- REFERENCES [dbo].[FctSales] (SalesOrderID)     
    -- ON DELETE NO ACTION    
    -- ON UPDATE NO ACTION    
);


CREATE TABLE [dbo].[DmnProduct] ( <br>
    ProductID int IDENTITY(1,1) NOT NULL PRIMARY KEY, <br>
    Name nvarchar(50) NOT NULL, <br>
    ProductNumber nvarchar(25) NOT NULL, <br>
    ListPrice money NOT NULL, <br>
    Size nvarchar(5), <br>
    ModifiedDate datetime <br>

    -- CONSTRAINT FK_FctTable_DmnProduct FOREIGN KEY (ProductID)     
    -- REFERENCES [dbo].[FctSales] (ProductID)     
    -- ON DELETE NO ACTION    
    -- ON UPDATE NO ACTION 
);

**2. Insert data into tables from AdventureWorks2019-db

#### [dbo].[FctSales]

SET IDENTITY_INSERT [dbo].[FctSales] ON

INSERT INTO [Stamp].[dbo].[FctSales]
    ([SalesOrderID]
      ,[ProductID]
      ,[OrderQty]
      ,[UnitPrice]
      ,[ModifiedDate])

SELECT SalesOrderID
      ,ProductID
      ,OrderQty
      ,UnitPrice
      ,ModifiedDate
FROM [AdventureWorks2019].[Sales].[SalesOrderDetail]

SET IDENTITY_INSERT [dbo].[FctSales] OFF

#### [dbo].[DmnOrder]

SET IDENTITY_INSERT [dbo].[DmnOrder] OFF

USE [Stamp];

CREATE TABLE [dbo].[DmnOrder](
    SalesOrderID int IDENTITY(1,1) NOT NULL PRIMARY KEY,
    SalesOrderNumber nvarchar(255) NOT NULL,
    AccountNumber nvarchar(255) NOT NULL,
    CreditCardID int,
    OrderDate datetime NOT NULL,
    ModifiedDate datetime NULL
  
    -- CONSTRAINT FK_FctTable_DmnOrder FOREIGN KEY (SalesOrderID)     
    -- REFERENCES [dbo].[FctSales] (SalesOrderID)     
    -- ON DELETE NO ACTION    
    -- ON UPDATE NO ACTION    
);

DROP TABLE [Stamp].[dbo].[DmnOrder]

#### [dbo].[DmnProduct]

SET IDENTITY_INSERT [dbo].[DmnProduct] ON

INSERT INTO [dbo].[DmnProduct]
    ([ProductID]
      ,[Name]
      ,[ProductNumber]
      ,[ListPrice]
      ,[Size]
      ,[ModifiedDate])

SELECT p.ProductID
      ,p.Name
      ,p.ProductNumber
      ,p.ListPrice
      ,p.Size
      ,ModifiedDate
FROM [AdventureWorks2019].[Production].[Product] p

SET IDENTITY_INSERT [dbo].[DmnProduct] OFF
