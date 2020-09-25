---
title: DataAdapter 和 DataReader
description: 瞭解 ADO.NET DataReader （可從資料庫取出資料）和 DataAdapter （可從資料來源抓取資料並填入資料集）。
ms.date: 03/30/2017
ms.assetid: cc952ca2-ec19-46ab-9189-15174b52cb74
ms.openlocfilehash: 2584f8b382dd90f2f8b4554663dc545b9ccceb62
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177601"
---
# <a name="dataadapters-and-datareaders"></a>DataAdapter 和 DataReader

您可以使用 ADO.NET **DataReader** ，從資料庫取出唯讀、順向的資料流程。 結果會在執行查詢時傳回，而且會儲存在用戶端的網路緩衝區中，直到您使用**DataReader**的**Read**方法要求它們為止。 使用 **DataReader** 可在資料可供使用時立即取得資料，以提高應用程式效能，並預設 () 在記憶體中一次只儲存一個資料列，以降低系統的額外負荷。  
  
 <xref:System.Data.Common.DataAdapter> 可用於從資料來源擷取資料，並填入 <xref:System.Data.DataSet> 內的資料表。 `DataAdapter` 亦可將對 `DataSet` 所做的變更解析回資料來源。 `DataAdapter` 會使用 .NET Framework 資料提供者的 `Connection` 物件連接到資料來源，並使用 `Command` 物件從資料來源擷取資料，以及將變更解析回資料來源。  
  
 內含在 .NET Framework 中的每個 .NET Framework 資料提供者都有 <xref:System.Data.Common.DbDataReader> 和 <xref:System.Data.Common.DbDataAdapter> 物件：.NET Framework Data Provider for OLE DB 包含 <xref:System.Data.OleDb.OleDbDataReader> 和 <xref:System.Data.OleDb.OleDbDataAdapter> 物件、.NET Framework Data Provider for SQL Server 包含 <xref:System.Data.SqlClient.SqlDataReader> 和 <xref:System.Data.SqlClient.SqlDataAdapter> 物件、.NET Framework Data Provider for ODBC 包含 <xref:System.Data.Odbc.OdbcDataReader> 和 <xref:System.Data.Odbc.OdbcDataAdapter> 物件，而且 .NET Framework Data Provider for Oracle 包含 <xref:System.Data.OracleClient.OracleDataReader> 和 <xref:System.Data.OracleClient.OracleDataAdapter> 物件。  
  
## <a name="in-this-section"></a>本節內容  

 [使用 DataReader 擷取資料](retrieving-data-using-a-datareader.md)  
 描述 ADO.NET **DataReader** 物件，以及如何使用它來從資料來源傳回結果資料流程。  
  
 [從 DataAdapter 填入資料集](populating-a-dataset-from-a-dataadapter.md)  
 說明如何使用 `DataSet` 來以資料表、資料行及資料列填入 `DataAdapter`。  
  
 [DataAdapter 的參數](dataadapter-parameters.md)  
 說明如何搭配使用參數與 `DataAdapter` 的命令屬性，包括如何將 `DataSet` 中資料行的內容對應至命令參數。  
  
 [將現有條件約束加入至資料集](adding-existing-constraints-to-a-dataset.md)  
 說明如何將現有條件約束加入 `DataSet`。  
  
 [DataAdapter DataTable 和 DataColumn 對應](dataadapter-datatable-and-datacolumn-mappings.md)  
 說明如何設定 `DataTableMappings` 的 `ColumnMappings` 和 `DataAdapter`。  
  
 [逐頁查看查詢結果](paging-through-a-query-result.md)  
 提供以資料分頁形式檢視查詢結果的範例。  
  
 [使用 DataAdapter 更新資料來源](updating-data-sources-with-dataadapters.md)  
 說明如何使用 `DataAdapter`，將 `DataSet` 中的變更解析回資料庫。  
  
 [處理 DataAdapter 的事件](handling-dataadapter-events.md)  
 說明 `DataAdapter` 事件以及如何使用它們。  
  
 [使用 DataAdapter 執行批次作業](performing-batch-operations-using-dataadapters.md)  
 說明在套用來自 `DataSet` 的更新時，如何藉由減少與 SQL Server 之間的往返次數，提高應用程式效能。  
  
## <a name="see-also"></a>另請參閱

- [連接到資料來源](connecting-to-a-data-source.md)
- [命令和參數](commands-and-parameters.md)
- [異動和並行存取](transactions-and-concurrency.md)
- [DataSet、DataTable 和 DataView](./dataset-datatable-dataview/index.md)
- [ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)
