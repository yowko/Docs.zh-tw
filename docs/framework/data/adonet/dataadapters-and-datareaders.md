---
title: "DataAdapter 和 DataReader"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc952ca2-ec19-46ab-9189-15174b52cb74
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3e7a0af0b5fabdfacfcc825258242868b0fbb513
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="dataadapters-and-datareaders"></a>DataAdapter 和 DataReader
您可以使用 ADO.NET **DataReader**從資料庫擷取資料的唯讀、 順向資料流。 時會傳回結果的查詢會執行，而且會儲存在用戶端上的網路緩衝區中，直到您提出要求時使用**讀取**方法**DataReader**。 使用**DataReader**可以提高應用程式效能，並使用，以擷取資料及 （依預設） 只有一個資料列一次將儲存在記憶體中，可降低系統額外負荷。  
  
 <xref:System.Data.Common.DataAdapter> 可用於從資料來源擷取資料，並填入 <xref:System.Data.DataSet> 內的資料表。 `DataAdapter` 亦可將對 `DataSet` 所做的變更解析回資料來源。 `DataAdapter` 會使用 .NET Framework 資料提供者的 `Connection` 物件連接到資料來源，並使用 `Command` 物件從資料來源擷取資料，以及將變更解析回資料來源。  
  
 內含在 .NET Framework 中的每個 .NET Framework 資料提供者都有 <xref:System.Data.Common.DbDataReader> 和 <xref:System.Data.Common.DbDataAdapter> 物件：.NET Framework Data Provider for OLE DB 包含 <xref:System.Data.OleDb.OleDbDataReader> 和 <xref:System.Data.OleDb.OleDbDataAdapter> 物件、.NET Framework Data Provider for SQL Server 包含 <xref:System.Data.SqlClient.SqlDataReader> 和 <xref:System.Data.SqlClient.SqlDataAdapter> 物件、.NET Framework Data Provider for ODBC 包含 <xref:System.Data.Odbc.OdbcDataReader> 和 <xref:System.Data.Odbc.OdbcDataAdapter> 物件，而且 .NET Framework Data Provider for Oracle 包含 <xref:System.Data.OracleClient.OracleDataReader> 和 <xref:System.Data.OracleClient.OracleDataAdapter> 物件。  
  
## <a name="in-this-section"></a>本章節內容  
 [使用 DataReader 擷取資料](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md)  
 說明 ADO.NET **DataReader**物件，以及如何使用它來從資料來源傳回的結果資料流。  
  
 [從 DataAdapter 填入 DataSet](../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 說明如何使用 `DataSet` 來以資料表、資料行及資料列填入 `DataAdapter`。  
  
 [DataAdapter 的參數](../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 說明如何搭配使用參數與 `DataAdapter` 的命令屬性，包括如何將 `DataSet` 中資料行的內容對應至命令參數。  
  
 [將現有條件約束新增至 DataSet](../../../../docs/framework/data/adonet/adding-existing-constraints-to-a-dataset.md)  
 說明如何將現有條件約束加入 `DataSet`。  
  
 [DataAdapter DataTable 和 DataColumn 對應](../../../../docs/framework/data/adonet/dataadapter-datatable-and-datacolumn-mappings.md)  
 說明如何設定 `DataTableMappings` 的 `ColumnMappings` 和 `DataAdapter`。  
  
 [查詢結果分頁](../../../../docs/framework/data/adonet/paging-through-a-query-result.md)  
 提供以資料分頁形式檢視查詢結果的範例。  
  
 [使用 DataAdapter 更新資料來源](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 說明如何使用 `DataAdapter`，將 `DataSet` 中的變更解析回資料庫。  
  
 [處理 DataAdapter 事件](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)  
 說明 `DataAdapter` 事件以及如何使用它們。  
  
 [使用 Dataadapter 執行批次作業](../../../../docs/framework/data/adonet/performing-batch-operations-using-dataadapters.md)  
 說明在套用來自 `DataSet` 的更新時，如何藉由減少與 SQL Server 之間的往返次數，提高應用程式效能。  
  
## <a name="see-also"></a>另請參閱  
 [連接至資料來源](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [命令和參數](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [異動和並行存取](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [DataSet、DataTable 和 DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
