---
title: "大量複製範例設定 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d4dde6ac-b8b6-4593-965a-635c8fb2dadb
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# 大量複製範例設定
<xref:System.Data.SqlClient.SqlBulkCopy> 類別可用於僅將資料寫入 SQL Server 資料表。  本主題所顯示的程式碼範例使用 SQL Server 範例資料庫 **AdventureWorks**。  為了避免變更現有資料表的程式碼範例，請將資料寫入您必須先建立的資料表中。  
  
 **BulkCopyDemoMatchingColumns** 和 **BulkCopyDemoDifferentColumns** 資料表都是以 **AdventureWorks** **Production.Products** 資料表為基礎。  在使用這些資料的程式碼範例中，資料是從 **Production.Products** 資料表加入其中一個範例資料表。  範例示範如何將資料行從來源資料對應至目的資料表時，會使用 **BulkCopyDemoDifferentColumns** 資料表，而 **BulkCopyDemoMatchingColumns** 可用於大部分其他範例。  
  
 幾個程式碼範例會示範如何使用一個 <xref:System.Data.SqlClient.SqlBulkCopy> 類別來寫入多個資料表。  針對這些範例，會使用 **BulkCopyDemoOrderHeader** 及 **BulkCopyDemoOrderDetail** 資料表做為目的資料表。  這些資料表都是以 **AdventureWorks** 中的 **Sales.SalesOrderHeader** 和 **Sales.SalesOrderDetail** 資料表為基礎。  
  
> [!NOTE]
>  **SqlBulkCopy** 程式碼範例只是為了示範使用 **SqlBulkCopy** 的語法而提供。  如果來源及目的地資料表位於相同的 SQL Server 執行個體中，則使用 Transact\-SQL `INSERT … SELECT` 陳述式來複製資料會更方便且快速。  
  
## 資料表設定  
 若要建立讓程式碼範例正確執行所需的資料表，您必須在 SQL Server 資料庫中執行下列 Transact\-SQL 陳述式。  
  
```  
USE AdventureWorks  
  
IF EXISTS (SELECT * FROM dbo.sysobjects   
 WHERE id = object_id(N'[dbo].[BulkCopyDemoMatchingColumns]')   
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoMatchingColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoMatchingColumns]([ProductID] [int] IDENTITY(1,1) NOT NULL,  
    [Name] [nvarchar](50) NOT NULL,  
    [ProductNumber] [nvarchar](25) NOT NULL,  
 CONSTRAINT [PK_ProductID] PRIMARY KEY CLUSTERED   
(  
    [ProductID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects   
 WHERE id = object_id(N'[dbo].[BulkCopyDemoDifferentColumns]')   
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoDifferentColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoDifferentColumns]([ProdID] [int] IDENTITY(1,1) NOT NULL,  
    [ProdNum] [nvarchar](25) NOT NULL,  
    [ProdName] [nvarchar](50) NOT NULL,  
 CONSTRAINT [PK_ProdID] PRIMARY KEY CLUSTERED   
(  
    [ProdID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects   
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderHeader]')   
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderHeader]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderHeader]([SalesOrderID] [int] IDENTITY(1,1) NOT NULL,  
    [OrderDate] [datetime] NOT NULL,  
    [AccountNumber] [nvarchar](15) NULL,  
 CONSTRAINT [PK_SalesOrderID] PRIMARY KEY CLUSTERED   
(  
    [SalesOrderID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects   
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderDetail]')   
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderDetail]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderDetail]([SalesOrderID] [int] NOT NULL,  
    [SalesOrderDetailID] [int] NOT NULL,  
    [OrderQty] [smallint] NOT NULL,  
    [ProductID] [int] NOT NULL,  
    [UnitPrice] [money] NOT NULL,  
 CONSTRAINT [PK_LineNumber] PRIMARY KEY CLUSTERED   
(  
    [SalesOrderID] ASC,  
    [SalesOrderDetailID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
```  
  
## 請參閱  
 [SQL Server 中的大量複製作業](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)