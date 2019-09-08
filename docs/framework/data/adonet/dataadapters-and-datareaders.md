---
title: DataAdapter 和 DataReader
ms.date: 03/30/2017
ms.assetid: cc952ca2-ec19-46ab-9189-15174b52cb74
ms.openlocfilehash: 20c6d514e70d2e4db451e0fff02e72688bf7d0ba
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786645"
---
# <a name="dataadapters-and-datareaders"></a>DataAdapter 和 DataReader
您可以使用 ADO.NET **DataReader** ，從資料庫中取出唯讀、順向資料流程的資料。 執行查詢時會傳回結果，並將其儲存在用戶端上的網路緩衝區中，直到您使用**DataReader**的**Read**方法要求它們為止。 使用**DataReader**可提高應用程式效能，方法是在資料可用時立即抓取它，而且（預設）在記憶體中一次只儲存一個資料列，以降低系統負荷。  
  
 <xref:System.Data.Common.DataAdapter> 可用於從資料來源擷取資料，並填入 <xref:System.Data.DataSet> 內的資料表。 `DataAdapter` 亦可將對 `DataSet` 所做的變更解析回資料來源。 `DataAdapter` 會使用 .NET Framework 資料提供者的 `Connection` 物件連接到資料來源，並使用 `Command` 物件從資料來源擷取資料，以及將變更解析回資料來源。  
  
 內含在 .NET Framework 中的每個 .NET Framework 資料提供者都有 <xref:System.Data.Common.DbDataReader> 和 <xref:System.Data.Common.DbDataAdapter> 物件：.NET Framework Data Provider for OLE DB 包含 <xref:System.Data.OleDb.OleDbDataReader> 和 <xref:System.Data.OleDb.OleDbDataAdapter> 物件、.NET Framework Data Provider for SQL Server 包含 <xref:System.Data.SqlClient.SqlDataReader> 和 <xref:System.Data.SqlClient.SqlDataAdapter> 物件、.NET Framework Data Provider for ODBC 包含 <xref:System.Data.Odbc.OdbcDataReader> 和 <xref:System.Data.Odbc.OdbcDataAdapter> 物件，而且 .NET Framework Data Provider for Oracle 包含 <xref:System.Data.OracleClient.OracleDataReader> 和 <xref:System.Data.OracleClient.OracleDataAdapter> 物件。  
  
## <a name="in-this-section"></a>本節內容  
 [使用 DataReader 擷取資料](retrieving-data-using-a-datareader.md)  
 描述 ADO.NET **DataReader**物件，以及如何使用它從資料來源傳回結果的資料流程。  
  
 [從 DataAdapter 填入 DataSet](populating-a-dataset-from-a-dataadapter.md)  
 說明如何使用 `DataSet` 來以資料表、資料行及資料列填入 `DataAdapter`。  
  
 [DataAdapter 參數](dataadapter-parameters.md)  
 說明如何搭配使用參數與 `DataAdapter` 的命令屬性，包括如何將 `DataSet` 中資料行的內容對應至命令參數。  
  
 [將現有條件約束新增至 DataSet](adding-existing-constraints-to-a-dataset.md)  
 說明如何將現有條件約束加入 `DataSet`。  
  
 [DataAdapter DataTable 和 DataColumn 對應](dataadapter-datatable-and-datacolumn-mappings.md)  
 說明如何設定 `DataTableMappings` 的 `ColumnMappings` 和 `DataAdapter`。  
  
 [逐頁查看查詢結果](paging-through-a-query-result.md)  
 提供以資料分頁形式檢視查詢結果的範例。  
  
 [使用 DataAdapter 更新資料來源](updating-data-sources-with-dataadapters.md)  
 說明如何使用 `DataAdapter`，將 `DataSet` 中的變更解析回資料庫。  
  
 [處理 DataAdapter 事件](handling-dataadapter-events.md)  
 說明 `DataAdapter` 事件以及如何使用它們。  
  
 [使用 DataAdapter 執行批次作業](performing-batch-operations-using-dataadapters.md)  
 說明在套用來自 `DataSet` 的更新時，如何藉由減少與 SQL Server 之間的往返次數，提高應用程式效能。  
  
## <a name="see-also"></a>另請參閱

- [連接至資料來源](connecting-to-a-data-source.md)
- [命令和參數](commands-and-parameters.md)
- [異動和並行存取](transactions-and-concurrency.md)
- [DataSet、DataTable 和 DataView](./dataset-datatable-dataview/index.md)
- [ADO.NET 概觀](ado-net-overview.md)
