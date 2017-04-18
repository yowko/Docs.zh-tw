---
title: "擷取資料庫結構描述資訊 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 79038d52-f122-4fd4-9bfb-aaa22d6a114b
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# 擷取資料庫結構描述資訊
從資料庫取得結構描述資訊是透過結構描述探索處理序來完成。  結構描述探索允許應用程式要求 Managed 提供者尋找並傳回給定資料庫之資料庫結構描述 \(亦稱為「*中繼資料*」\) 的相關資訊。  不同的資料庫結構描述項目 \(如資料表、資料行及預存程序\) 都透過結構描述集合公開。  每個結構描述集合都包含正在使用的提供者之各種特定的結構描述資訊。  
  
 每個 .NET Framework Managed 提供者都在 **Connection** 類別中實作 **GetSchema** 方法，且 **GetSchema** 方法傳回的結構描述資訊會以 <xref:System.Data.DataTable> 形式表示。  **GetSchema** 方法是一種多載方法，它為指定要傳回的結構描述集合及限制傳回的資訊量，提供選擇性參數。  
  
 .NET Framework Data Provider for OLE DB、ODBC、Oracle 和 SqlClient 會提供 **GetSchemaTable** 方法，可傳回描述 **DataReader** 之資料行中繼資料的 DataTable。  
  
 .NET Framework Data Provider for OLE DB 也會使用 <xref:System.Data.OleDb.OleDbConnection> 物件的 <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> 方法來公開結構描述資訊。  **GetOleDbSchemaTable** 會將 <xref:System.Data.OleDb.OleDbSchemaGuid> 當成引數，以便識別要傳回的結構描述資訊以及對那些傳回資料行的限制陣列。  **GetOleDbSchemaTable** 會傳回以所要求的結構描述資訊填入的 <xref:System.Data.DataTable>。  
  
## 在本節中  
 [GetSchema 和結構描述集合](../../../../docs/framework/data/adonet/getschema-and-schema-collections.md)  
 說明 **GetSchema** 方法及其在擷取及限制資料庫結構描述資訊時的使用方式。  
  
 結構描述限制  
 說明可搭配 **GetSchema** 使用的結構描述限制。  
  
 [通用結構描述集合](../../../../docs/framework/data/adonet/common-schema-collections.md)  
 說明所有 .NET Framework Managed 提供者支援的所有通用結構描述集合。  
  
 [SQL Server 結構描述集合](../../../../docs/framework/data/adonet/sql-server-schema-collections.md)  
 說明 .NET Framework Provider for SQL Server 所支援的結構描述集合。  
  
 [Oracle 結構描述集合](../../../../docs/framework/data/adonet/oracle-schema-collections.md)  
 說明 .NET Framework Provider for Oracle 所支援的結構描述集合。  
  
 [ODBC 結構描述集合](../../../../docs/framework/data/adonet/odbc-schema-collections.md)  
 說明 ODBC 驅動程式的結構描述集合。  
  
 [OLE DB 結構描述集合](../../../../docs/framework/data/adonet/ole-db-schema-collections.md)  
 說明 OLE DB 提供者的結構描述集合。  
  
## 參考  
 <xref:System.Data.Common.DbConnection.GetSchema%2A>  
 說明 <xref:System.Data.Common.DbConnection> 類別的 **GetSchema** 方法。  
  
 <xref:System.Data.Odbc.OdbcConnection.GetSchema%2A>  
 說明 <xref:System.Data.Odbc.OdbcConnection> 類別的 **GetSchema** 方法。  
  
 <xref:System.Data.OleDb.OleDbConnection.GetSchema%2A>  
 說明 <xref:System.Data.OleDb.OleDbConnection> 類別的 **GetSchema** 方法。  
  
 <xref:System.Data.OracleClient.OracleConnection.GetSchema%2A>  
 說明 <xref:System.Data.OracleClient.OracleConnection> 類別的 **GetSchema** 方法。  
  
 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>  
 說明 <xref:System.Data.SqlClient.SqlConnection> 類別的 **GetSchema** 方法。  
  
 <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A>  
 說明 <xref:System.Data.Common.DbDataReader> 類別的 **GetSchemaTable** 方法。  
  
 <xref:System.Data.Odbc.OdbcDataReader.GetSchemaTable%2A>  
 說明 <xref:System.Data.Odbc.OdbcDataReader> 類別的 **GetSchemaTable** 方法。  
  
 <xref:System.Data.OleDb.OleDbDataReader.GetSchemaTable%2A>  
 說明 <xref:System.Data.OleDb.OleDbDataReader> 類別的 **GetSchemaTable** 方法。  
  
 <xref:System.Data.OracleClient.OracleDataReader.GetSchemaTable%2A>  
 說明 <xref:System.Data.OracleClient.OracleDataReader> 類別的 **GetSchemaTable** 方法。  
  
 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>  
 說明 <xref:System.Data.SqlClient.SqlDataReader> 類別的 **GetSchemaTable** 方法。  
  
## 請參閱  
 [擷取和修改 ADO.NET 中的資料](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)