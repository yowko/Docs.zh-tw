---
title: DataAdapter 和 DataReader
ms.date: 03/30/2017
ms.assetid: cc952ca2-ec19-46ab-9189-15174b52cb74
ms.openlocfilehash: af1d44b1e320557ab7906ce65dbeb5415b5c09dd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59189678"
---
# <a name="dataadapters-and-datareaders"></a>DataAdapter 和 DataReader
您可以使用 ADO.NET **DataReader**從資料庫擷取資料的唯讀、 順向資料流。 結果會傳回查詢執行，並會儲存在用戶端上的網路緩衝區中，直到您提出要求時使用**讀取**方法**DataReader**。 使用**DataReader**可以提高應用程式的效能，會透過形式擷取資料及 （依預設） 只有一個資料列一次將儲存在記憶體中，進而減少系統負擔。  
  
 <xref:System.Data.Common.DataAdapter> 可用於從資料來源擷取資料，並填入 <xref:System.Data.DataSet> 內的資料表。 `DataAdapter` 亦可將對 `DataSet` 所做的變更解析回資料來源。 `DataAdapter` 會使用 .NET Framework 資料提供者的 `Connection` 物件連接到資料來源，並使用 `Command` 物件從資料來源擷取資料，以及將變更解析回資料來源。  
  
 內含在 .NET Framework 中的每個 .NET Framework 資料提供者都有 <xref:System.Data.Common.DbDataReader> 和 <xref:System.Data.Common.DbDataAdapter> 物件：.NET Framework Data Provider for OLE DB 包含 <xref:System.Data.OleDb.OleDbDataReader> 和 <xref:System.Data.OleDb.OleDbDataAdapter> 物件、.NET Framework Data Provider for SQL Server 包含 <xref:System.Data.SqlClient.SqlDataReader> 和 <xref:System.Data.SqlClient.SqlDataAdapter> 物件、.NET Framework Data Provider for ODBC 包含 <xref:System.Data.Odbc.OdbcDataReader> 和 <xref:System.Data.Odbc.OdbcDataAdapter> 物件，而且 .NET Framework Data Provider for Oracle 包含 <xref:System.Data.OracleClient.OracleDataReader> 和 <xref:System.Data.OracleClient.OracleDataAdapter> 物件。  
  
## <a name="in-this-section"></a>本節內容  
 [使用 DataReader 擷取資料](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md)  
 說明 ADO.NET **DataReader**物件，以及如何使用它來從資料來源傳回結果資料流。  
  
 [從 DataAdapter 填入 DataSet](../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 說明如何使用 `DataSet` 來以資料表、資料行及資料列填入 `DataAdapter`。  
  
 [DataAdapter 參數](../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 說明如何搭配使用參數與 `DataAdapter` 的命令屬性，包括如何將 `DataSet` 中資料行的內容對應至命令參數。  
  
 [將現有條件約束新增至 DataSet](../../../../docs/framework/data/adonet/adding-existing-constraints-to-a-dataset.md)  
 說明如何將現有條件約束加入 `DataSet`。  
  
 [DataAdapter DataTable 和 DataColumn 對應](../../../../docs/framework/data/adonet/dataadapter-datatable-and-datacolumn-mappings.md)  
 說明如何設定 `DataTableMappings` 的 `ColumnMappings` 和 `DataAdapter`。  
  
 [逐頁查看查詢結果](../../../../docs/framework/data/adonet/paging-through-a-query-result.md)  
 提供以資料分頁形式檢視查詢結果的範例。  
  
 [使用 DataAdapter 更新資料來源](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 說明如何使用 `DataAdapter`，將 `DataSet` 中的變更解析回資料庫。  
  
 [處理 DataAdapter 事件](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)  
 說明 `DataAdapter` 事件以及如何使用它們。  
  
 [使用 DataAdapter 執行批次作業](../../../../docs/framework/data/adonet/performing-batch-operations-using-dataadapters.md)  
 說明在套用來自 `DataSet` 的更新時，如何藉由減少與 SQL Server 之間的往返次數，提高應用程式效能。  
  
## <a name="see-also"></a>另請參閱

- [連接至資料來源](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [命令和參數](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [異動和並行存取](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)
- [DataSet、DataTable 和 DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
