---
title: "範例提供者中的 SQL 產生 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 範例提供者中的 SQL 產生
[Entity Framework 範例提供者](http://go.microsoft.com/fwlink/?LinkId=180616)會示範支援 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 之 ADO.NET 資料提供者的新元件。  它會使用 SQL Server 2005 資料庫並且實作成 System.Data.SqlClient ADO.NET 2.0 資料提供者的包裝函式。  
  
 此範例提供者的 SQL 產生模組 \(位於 SQL Generation 資料夾底下，但 DmlSqlGenerator.cs 檔案除外\) 會接受輸入 DbQueryCommandTree 並且產生單一 SQL SELECT 陳述式。  
  
## 本章節內容  
 本節包括下列主題：  
  
 [架構與設計](../../../../../docs/framework/data/adonet/ef/architecture-and-design.md)  
  
 [逐步解說：SQL 產生](../../../../../docs/framework/data/adonet/ef/walkthrough-sql-generation.md)  
  
## 請參閱  
 [SQL 產生](../../../../../docs/framework/data/adonet/ef/sql-generation.md)