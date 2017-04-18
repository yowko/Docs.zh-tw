---
title: "DbProviderFactories | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2a8e2640-3a49-42a1-a3a9-b43026907ae1
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# DbProviderFactories
<xref:System.Data.Common> 命名空間 \(Namespace\) 提供類別 \(Class\)，可用於建立 <xref:System.Data.Common.DbProviderFactory> 執行個體 \(Instance\) 以使用特定的資料來源。  當您建立 <xref:System.Data.Common.DbProviderFactory> 執行個體並將資料提供者相關資訊傳遞給它時，`DbProviderFactory` 可以根據所提供的資訊來決定要傳回的正確強型別 \(Strongly Typed\) 物件。  
  
 從 .NET Framework 版本 4 開始，資料提供者 \(例如：<xref:System.Data.Odbc>, <xref:System.Data.OleDb>、<xref:System.Data.SqlClient> 及 <xref:System.Data.OracleClient>\) 不會再列於 machine.config 檔案中，但自訂提供者會繼續列於該檔案中。  
  
## 本章節內容  
 [Factory 模型概觀](../../../../docs/framework/data/adonet/factory-model-overview.md)  
 提供 Factory 設計模式和程式設計介面的概觀。  
  
 [取得 DbProviderFactory](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)  
 示範如何列出已安裝的資料提供者，以及如何從 `DbProviderFactory` 建立 <xref:System.Data.Common.DbConnection>。  
  
 [DbConnection、DbCommand 和 DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 示範如何建立 <xref:System.Data.Common.DbCommand> 和 <xref:System.Data.Common.DbDataReader>，以及如何使用 <xref:System.Data.Common.DbException> 處理資料錯誤。  
  
 [使用 DbDataAdapter 來修改資料](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)  
 示範如何使用具有 <xref:System.Data.Common.DbDataAdapter> 的 <xref:System.Data.Common.DbCommandBuilder> 擷取及修改資料。  
  
## 請參閱  
 [擷取和修改 ADO.NET 中的資料](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)