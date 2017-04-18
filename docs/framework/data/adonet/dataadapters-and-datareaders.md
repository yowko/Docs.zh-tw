---
title: "DataAdapter 和 DataReader | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cc952ca2-ec19-46ab-9189-15174b52cb74
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# DataAdapter 和 DataReader
您可以使用 ADO.NET **DataReader**，從資料庫擷取順向唯讀資料流。  執行查詢時會傳回結果，並一直儲存於用戶端上的網路緩衝區中，直到您使用 **DataReader** 的 **Read** 方法要求它們為止。  使用 **DataReader** 可以提高應用程式的效能，方法是立即擷取可用的資料，及 \(依預設\) 一次只將一個資料列儲存到記憶體中，進而減少系統負荷。  
  
 <xref:System.Data.Common.DataAdapter> 可用於從資料來源擷取資料，並填入 <xref:System.Data.DataSet> 內的資料表。  `DataAdapter` 亦可將對 `DataSet` 所做的變更解析回資料來源。  `DataAdapter` 會使用 .NET Framework 資料提供者的 `Connection` 物件連接到資料來源，並使用 `Command` 物件從資料來源擷取資料，以及將變更解析回資料來源。  
  
 內含在 .NET Framework 中的每個 .NET Framework 資料提供者都有 <xref:System.Data.Common.DbDataReader> 和 <xref:System.Data.Common.DbDataAdapter> 物件：.NET Framework Data Provider for OLE DB 包含 <xref:System.Data.OleDb.OleDbDataReader> 和 <xref:System.Data.OleDb.OleDbDataAdapter> 物件、.NET Framework Data Provider for SQL Server 包含 <xref:System.Data.SqlClient.SqlDataReader> 和 <xref:System.Data.SqlClient.SqlDataAdapter> 物件、.NET Framework Data Provider for ODBC 包含 <xref:System.Data.Odbc.OdbcDataReader> 和 <xref:System.Data.Odbc.OdbcDataAdapter> 物件，而且 .NET Framework Data Provider for Oracle 包含 <xref:System.Data.OracleClient.OracleDataReader> 和 <xref:System.Data.OracleClient.OracleDataAdapter> 物件。  
  
## 在本節中  
 [使用 DataReader 擷取資料](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md)  
 說明 ADO.NET **DataReader** 物件，以及如何將該物件用於從資料來源傳回結果資料流。  
  
 [從 DataAdapter 填入資料集](../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 說明如何使用 `DataAdapter` 來以資料表、資料行及資料列填入 `DataSet`。  
  
 [DataAdapter 參數](../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 說明如何搭配使用參數與 `DataAdapter` 的命令屬性，包括如何將 `DataSet` 中資料行的內容對應至命令參數。  
  
 [將現有條件約束加入 DataSet](../../../../docs/framework/data/adonet/adding-existing-constraints-to-a-dataset.md)  
 說明如何將現有條件約束加入 `DataSet`。  
  
 [DataAdapter DataTable 和 DataColumn 對應](../../../../docs/framework/data/adonet/dataadapter-datatable-and-datacolumn-mappings.md)  
 說明如何設定 `DataAdapter` 的 `DataTableMappings` 和 `ColumnMappings`。  
  
 [將查詢結果分頁](../../../../docs/framework/data/adonet/paging-through-a-query-result.md)  
 提供以資料分頁形式檢視查詢結果的範例。  
  
 [以 DataAdapter 更新資料來源](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 說明如何使用 `DataAdapter`，將 `DataSet` 中的變更解析回資料庫。  
  
 [處理 DataAdapter 事件](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)  
 說明 `DataAdapter` 事件以及如何使用它們。  
  
 [使用 DataAdapters 執行批次作業](../../../../docs/framework/data/adonet/performing-batch-operations-using-dataadapters.md)  
 說明在套用來自 `DataSet` 的更新時，如何藉由減少與 SQL Server 之間的往返次數，提高應用程式效能。  
  
## 請參閱  
 [連接資料來源](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)   
 [命令和參數](../../../../docs/framework/data/adonet/commands-and-parameters.md)   
 [交易和並行](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)   
 [DataSet、DataTable 及 DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)