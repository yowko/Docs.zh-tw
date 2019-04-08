---
title: DataAdapter 和 DataReader
ms.date: 03/30/2017
ms.assetid: cc952ca2-ec19-46ab-9189-15174b52cb74
ms.openlocfilehash: af1d44b1e320557ab7906ce65dbeb5415b5c09dd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59189678"
---
# <a name="dataadapters-and-datareaders"></a><span data-ttu-id="880f2-102">DataAdapter 和 DataReader</span><span class="sxs-lookup"><span data-stu-id="880f2-102">DataAdapters and DataReaders</span></span>
<span data-ttu-id="880f2-103">您可以使用 ADO.NET **DataReader**從資料庫擷取資料的唯讀、 順向資料流。</span><span class="sxs-lookup"><span data-stu-id="880f2-103">You can use the ADO.NET **DataReader** to retrieve a read-only, forward-only stream of data from a database.</span></span> <span data-ttu-id="880f2-104">結果會傳回查詢執行，並會儲存在用戶端上的網路緩衝區中，直到您提出要求時使用**讀取**方法**DataReader**。</span><span class="sxs-lookup"><span data-stu-id="880f2-104">Results are returned as the query executes, and are stored in the network buffer on the client until you request them using the **Read** method of the **DataReader**.</span></span> <span data-ttu-id="880f2-105">使用**DataReader**可以提高應用程式的效能，會透過形式擷取資料及 （依預設） 只有一個資料列一次將儲存在記憶體中，進而減少系統負擔。</span><span class="sxs-lookup"><span data-stu-id="880f2-105">Using the **DataReader** can increase application performance both by retrieving data as soon as it is available, and (by default) storing only one row at a time in memory, reducing system overhead.</span></span>  
  
 <span data-ttu-id="880f2-106"><xref:System.Data.Common.DataAdapter> 可用於從資料來源擷取資料，並填入 <xref:System.Data.DataSet> 內的資料表。</span><span class="sxs-lookup"><span data-stu-id="880f2-106">A <xref:System.Data.Common.DataAdapter> is used to retrieve data from a data source and populate tables within a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="880f2-107">`DataAdapter` 亦可將對 `DataSet` 所做的變更解析回資料來源。</span><span class="sxs-lookup"><span data-stu-id="880f2-107">The `DataAdapter` also resolves changes made to the `DataSet` back to the data source.</span></span> <span data-ttu-id="880f2-108">`DataAdapter` 會使用 .NET Framework 資料提供者的 `Connection` 物件連接到資料來源，並使用 `Command` 物件從資料來源擷取資料，以及將變更解析回資料來源。</span><span class="sxs-lookup"><span data-stu-id="880f2-108">The `DataAdapter` uses the `Connection` object of the .NET Framework data provider to connect to a data source, and it uses `Command` objects to retrieve data from and resolve changes to the data source.</span></span>  
  
 <span data-ttu-id="880f2-109">內含在 .NET Framework 中的每個 .NET Framework 資料提供者都有 <xref:System.Data.Common.DbDataReader> 和 <xref:System.Data.Common.DbDataAdapter> 物件：.NET Framework Data Provider for OLE DB 包含 <xref:System.Data.OleDb.OleDbDataReader> 和 <xref:System.Data.OleDb.OleDbDataAdapter> 物件、.NET Framework Data Provider for SQL Server 包含 <xref:System.Data.SqlClient.SqlDataReader> 和 <xref:System.Data.SqlClient.SqlDataAdapter> 物件、.NET Framework Data Provider for ODBC 包含 <xref:System.Data.Odbc.OdbcDataReader> 和 <xref:System.Data.Odbc.OdbcDataAdapter> 物件，而且 .NET Framework Data Provider for Oracle 包含 <xref:System.Data.OracleClient.OracleDataReader> 和 <xref:System.Data.OracleClient.OracleDataAdapter> 物件。</span><span class="sxs-lookup"><span data-stu-id="880f2-109">Each .NET Framework data provider included with the .NET Framework has a <xref:System.Data.Common.DbDataReader> and a <xref:System.Data.Common.DbDataAdapter> object: the .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbDataReader> and an <xref:System.Data.OleDb.OleDbDataAdapter> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlDataReader> and a <xref:System.Data.SqlClient.SqlDataAdapter> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcDataReader> and an <xref:System.Data.Odbc.OdbcDataAdapter> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleDataReader> and an <xref:System.Data.OracleClient.OracleDataAdapter> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="880f2-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="880f2-110">In This Section</span></span>  
 [<span data-ttu-id="880f2-111">使用 DataReader 擷取資料</span><span class="sxs-lookup"><span data-stu-id="880f2-111">Retrieving Data Using a DataReader</span></span>](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md)  
 <span data-ttu-id="880f2-112">說明 ADO.NET **DataReader**物件，以及如何使用它來從資料來源傳回結果資料流。</span><span class="sxs-lookup"><span data-stu-id="880f2-112">Describes the ADO.NET **DataReader** object and how to use it to return a stream of results from a data source.</span></span>  
  
 [<span data-ttu-id="880f2-113">從 DataAdapter 填入資料集</span><span class="sxs-lookup"><span data-stu-id="880f2-113">Populating a DataSet from a DataAdapter</span></span>](../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 <span data-ttu-id="880f2-114">說明如何使用 `DataSet` 來以資料表、資料行及資料列填入 `DataAdapter`。</span><span class="sxs-lookup"><span data-stu-id="880f2-114">Describes how to fill a `DataSet` with tables, columns, and rows by using a `DataAdapter`.</span></span>  
  
 [<span data-ttu-id="880f2-115">DataAdapter 的參數</span><span class="sxs-lookup"><span data-stu-id="880f2-115">DataAdapter Parameters</span></span>](../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 <span data-ttu-id="880f2-116">說明如何搭配使用參數與 `DataAdapter` 的命令屬性，包括如何將 `DataSet` 中資料行的內容對應至命令參數。</span><span class="sxs-lookup"><span data-stu-id="880f2-116">Describes how to use parameters with the command properties of a `DataAdapter` including how to map the contents of a column in a `DataSet` to a command parameter.</span></span>  
  
 [<span data-ttu-id="880f2-117">將現有條件約束加入至資料集</span><span class="sxs-lookup"><span data-stu-id="880f2-117">Adding Existing Constraints to a DataSet</span></span>](../../../../docs/framework/data/adonet/adding-existing-constraints-to-a-dataset.md)  
 <span data-ttu-id="880f2-118">說明如何將現有條件約束加入 `DataSet`。</span><span class="sxs-lookup"><span data-stu-id="880f2-118">Describes how to add existing constraints to a `DataSet`.</span></span>  
  
 [<span data-ttu-id="880f2-119">DataAdapter DataTable 和 DataColumn 對應</span><span class="sxs-lookup"><span data-stu-id="880f2-119">DataAdapter DataTable and DataColumn Mappings</span></span>](../../../../docs/framework/data/adonet/dataadapter-datatable-and-datacolumn-mappings.md)  
 <span data-ttu-id="880f2-120">說明如何設定 `DataTableMappings` 的 `ColumnMappings` 和 `DataAdapter`。</span><span class="sxs-lookup"><span data-stu-id="880f2-120">Describes how to set up `DataTableMappings` and `ColumnMappings` for a `DataAdapter`.</span></span>  
  
 [<span data-ttu-id="880f2-121">逐頁查看查詢結果</span><span class="sxs-lookup"><span data-stu-id="880f2-121">Paging Through a Query Result</span></span>](../../../../docs/framework/data/adonet/paging-through-a-query-result.md)  
 <span data-ttu-id="880f2-122">提供以資料分頁形式檢視查詢結果的範例。</span><span class="sxs-lookup"><span data-stu-id="880f2-122">Provides an example of viewing the results of a query as pages of data.</span></span>  
  
 [<span data-ttu-id="880f2-123">使用 DataAdapter 更新資料來源</span><span class="sxs-lookup"><span data-stu-id="880f2-123">Updating Data Sources with DataAdapters</span></span>](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 <span data-ttu-id="880f2-124">說明如何使用 `DataAdapter`，將 `DataSet` 中的變更解析回資料庫。</span><span class="sxs-lookup"><span data-stu-id="880f2-124">Describes how to use a `DataAdapter` to resolve changes in a `DataSet` back to the database.</span></span>  
  
 [<span data-ttu-id="880f2-125">處理 DataAdapter 的事件</span><span class="sxs-lookup"><span data-stu-id="880f2-125">Handling DataAdapter Events</span></span>](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)  
 <span data-ttu-id="880f2-126">說明 `DataAdapter` 事件以及如何使用它們。</span><span class="sxs-lookup"><span data-stu-id="880f2-126">Describes `DataAdapter` events and how to use them.</span></span>  
  
 [<span data-ttu-id="880f2-127">使用 DataAdapter 執行批次作業</span><span class="sxs-lookup"><span data-stu-id="880f2-127">Performing Batch Operations Using DataAdapters</span></span>](../../../../docs/framework/data/adonet/performing-batch-operations-using-dataadapters.md)  
 <span data-ttu-id="880f2-128">說明在套用來自 `DataSet` 的更新時，如何藉由減少與 SQL Server 之間的往返次數，提高應用程式效能。</span><span class="sxs-lookup"><span data-stu-id="880f2-128">Describes enhancing application performance by reducing the number of round trips to SQL Server when applying updates from the `DataSet`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="880f2-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="880f2-129">See also</span></span>

- [<span data-ttu-id="880f2-130">連接資料來源</span><span class="sxs-lookup"><span data-stu-id="880f2-130">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [<span data-ttu-id="880f2-131">命令和參數</span><span class="sxs-lookup"><span data-stu-id="880f2-131">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [<span data-ttu-id="880f2-132">異動和並行存取</span><span class="sxs-lookup"><span data-stu-id="880f2-132">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)
- [<span data-ttu-id="880f2-133">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="880f2-133">DataSets, DataTables, and DataViews</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="880f2-134">ADO.NET Managed 提供者和DataSet開發人員中心</span><span class="sxs-lookup"><span data-stu-id="880f2-134">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
