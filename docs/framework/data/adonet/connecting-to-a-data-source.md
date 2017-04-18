---
title: "在 ADO.NET 中連接至資料來源 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# 在 ADO.NET 中連接至資料來源
您可以在 ADO.NET 內使用 **Connection** 物件來連接特定資料來源，方法是在連接字串中提供必要的驗證資訊。  使用的 **Connection** 物件取決於資料來源的型別。  
  
 內含在 .NET Framework 中的每個 .NET Framework 資料提供者都有 <xref:System.Data.Common.DbConnection> 物件：.NET Framework Data Provider for OLE DB 包含 <xref:System.Data.OleDb.OleDbConnection> 物件、.NET Framework Data Provider for SQL Server 包含 <xref:System.Data.SqlClient.SqlConnection> 物件、.NET Framework Data Provider for ODBC 包含 <xref:System.Data.Odbc.OdbcConnection> 物件，而且 .NET Framework Data Provider for Oracle 包含 <xref:System.Data.OracleClient.OracleConnection> 物件。  
  
## 在本節中  
 [建立連接](../../../../docs/framework/data/adonet/establishing-the-connection.md)  
 說明如何使用 **Connection** 物件來建立資料來源的連接。  
  
 [連接事件](../../../../docs/framework/data/adonet/connection-events.md)  
 說明如何使用 **InfoMessage** 事件，從資料來源擷取資訊訊息。  
  
## 請參閱  
 [連接字串](../../../../docs/framework/data/adonet/connection-strings.md)   
 [連接共用](../../../../docs/framework/data/adonet/connection-pooling.md)   
 [命令和參數](../../../../docs/framework/data/adonet/commands-and-parameters.md)   
 [DataAdapter 和 DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)   
 [交易和並行](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)