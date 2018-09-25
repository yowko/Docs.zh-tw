---
title: 使用 DataAdapter 執行批次作業
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e72ed5af-b24f-486c-8429-c8fd2208f844
ms.openlocfilehash: cfc77ff3b030ffebf52feab0190f81fc4e581cf9
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47114966"
---
# <a name="performing-batch-operations-using-dataadapters"></a><span data-ttu-id="df6be-102">使用 DataAdapter 執行批次作業</span><span class="sxs-lookup"><span data-stu-id="df6be-102">Performing Batch Operations Using DataAdapters</span></span>
<span data-ttu-id="df6be-103">ADO.NET 中的批次支援可讓 <xref:System.Data.Common.DataAdapter> 針對從 <xref:System.Data.DataSet> 或 <xref:System.Data.DataTable> 至伺服器的 INSERT、UPDATE 與 DELETE 作業進行分組，而非一次傳送一個作業。</span><span class="sxs-lookup"><span data-stu-id="df6be-103">Batch support in ADO.NET allows a <xref:System.Data.Common.DataAdapter> to group INSERT, UPDATE, and DELETE operations from a <xref:System.Data.DataSet> or <xref:System.Data.DataTable> to the server, instead of sending one operation at a time.</span></span> <span data-ttu-id="df6be-104">如此可降低往返於伺服器的次數，因此一般都能夠大幅提升作業效能。</span><span class="sxs-lookup"><span data-stu-id="df6be-104">The reduction in the number of round trips to the server typically results in significant performance gains.</span></span> <span data-ttu-id="df6be-105">SQL Server (<xref:System.Data.SqlClient>) 和 Oracle (<xref:System.Data.OracleClient>) 的 .NET 資料提供者都支援批次更新。</span><span class="sxs-lookup"><span data-stu-id="df6be-105">Batch updates are supported for the .NET data providers for SQL Server (<xref:System.Data.SqlClient>) and Oracle (<xref:System.Data.OracleClient>).</span></span>  
  
 <span data-ttu-id="df6be-106">在舊版 ADO.NET 中，以 <xref:System.Data.DataSet> 的變更更新資料庫時，`Update` 的 `DataAdapter` 方法會一次變更資料庫的一個資料列。</span><span class="sxs-lookup"><span data-stu-id="df6be-106">When updating a database with changes from a <xref:System.Data.DataSet> in previous versions of ADO.NET, the `Update` method of a `DataAdapter` performed updates to the database one row at a time.</span></span> <span data-ttu-id="df6be-107">當它逐一查看指定之 <xref:System.Data.DataTable> 的資料列時，它會檢查每一個 <xref:System.Data.DataRow>，以查看是否已修改該資料列。</span><span class="sxs-lookup"><span data-stu-id="df6be-107">As it iterated through the rows in the specified <xref:System.Data.DataTable>, it examined each <xref:System.Data.DataRow> to see if it had been modified.</span></span> <span data-ttu-id="df6be-108">如果已修改資料列，則會根據該資料列的 `UpdateCommand` 屬性值，呼叫適當的 `InsertCommand`、`DeleteCommand` 或 <xref:System.Data.DataRow.RowState%2A>。</span><span class="sxs-lookup"><span data-stu-id="df6be-108">If the row had been modified, it called the appropriate `UpdateCommand`, `InsertCommand`, or `DeleteCommand`, depending on the value of the <xref:System.Data.DataRow.RowState%2A> property for that row.</span></span> <span data-ttu-id="df6be-109">更新每個資料列時，都必須透過網路與資料庫往來通訊。</span><span class="sxs-lookup"><span data-stu-id="df6be-109">Every row update involved a network round-trip to the database.</span></span>  
  
 <span data-ttu-id="df6be-110">從 ADO.NET 2.0 開始，<xref:System.Data.Common.DbDataAdapter> 就會公開 (Expose) <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="df6be-110">Starting with ADO.NET 2.0, the <xref:System.Data.Common.DbDataAdapter> exposes an <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A> property.</span></span> <span data-ttu-id="df6be-111">將 `UpdateBatchSize` 設為正整數值，可將資料庫更新當成所指定大小的批次傳送。</span><span class="sxs-lookup"><span data-stu-id="df6be-111">Setting the `UpdateBatchSize` to a positive integer value causes updates to the database to be sent as batches of the specified size.</span></span> <span data-ttu-id="df6be-112">例如，將 `UpdateBatchSize` 設為 10，會分組 10 個不同的陳述式，並將它們當做單一批次送出。</span><span class="sxs-lookup"><span data-stu-id="df6be-112">For example, setting the `UpdateBatchSize` to 10 will group 10 separate statements and submit them as single batch.</span></span> <span data-ttu-id="df6be-113">將 `UpdateBatchSize` 設為 0，可讓 <xref:System.Data.Common.DataAdapter> 使用伺服器可處理的最大批次大小。</span><span class="sxs-lookup"><span data-stu-id="df6be-113">Setting the `UpdateBatchSize` to 0 will cause the <xref:System.Data.Common.DataAdapter> to use the largest batch size that the server can handle.</span></span> <span data-ttu-id="df6be-114">將其設定為 1 則可停用批次更新，此時一次只能傳送一個資料列。</span><span class="sxs-lookup"><span data-stu-id="df6be-114">Setting it to 1 disables batch updates, as rows are sent one at a time.</span></span>  
  
 <span data-ttu-id="df6be-115">執行極大的批次可能會降低效能。</span><span class="sxs-lookup"><span data-stu-id="df6be-115">Executing an extremely large batch could decrease performance.</span></span> <span data-ttu-id="df6be-116">因此，您應該先測試理想的批次大小設定，再實作應用程式。</span><span class="sxs-lookup"><span data-stu-id="df6be-116">Therefore, you should test for the optimum batch size setting before implementing your application.</span></span>  
  
## <a name="using-the-updatebatchsize-property"></a><span data-ttu-id="df6be-117">使用 UpdateBatchSize 屬性</span><span class="sxs-lookup"><span data-stu-id="df6be-117">Using the UpdateBatchSize Property</span></span>  
 <span data-ttu-id="df6be-118">啟用批次更新時，應該將 DataAdapter 的 <xref:System.Data.IDbCommand.UpdatedRowSource%2A>、`UpdateCommand` 和 `InsertCommand` 的 `DeleteCommand` 屬性值設為 <xref:System.Data.UpdateRowSource.None> 或 <xref:System.Data.UpdateRowSource.OutputParameters>。</span><span class="sxs-lookup"><span data-stu-id="df6be-118">When batch updates are enabled, the <xref:System.Data.IDbCommand.UpdatedRowSource%2A> property value of the DataAdapter's `UpdateCommand`, `InsertCommand`, and `DeleteCommand` should be set to <xref:System.Data.UpdateRowSource.None> or <xref:System.Data.UpdateRowSource.OutputParameters>.</span></span> <span data-ttu-id="df6be-119">執行批次更新時，命令之 <xref:System.Data.IDbCommand.UpdatedRowSource%2A> 或 <xref:System.Data.UpdateRowSource.FirstReturnedRecord> 的 <xref:System.Data.UpdateRowSource.Both> 屬性值無效。</span><span class="sxs-lookup"><span data-stu-id="df6be-119">When performing a batch update, the command's <xref:System.Data.IDbCommand.UpdatedRowSource%2A> property value of <xref:System.Data.UpdateRowSource.FirstReturnedRecord> or <xref:System.Data.UpdateRowSource.Both> is invalid.</span></span>  
  
 <span data-ttu-id="df6be-120">下列程序示範 `UpdateBatchSize` 屬性的用法。</span><span class="sxs-lookup"><span data-stu-id="df6be-120">The following procedure demonstrates the use of the `UpdateBatchSize` property.</span></span> <span data-ttu-id="df6be-121">此程序會採用兩個引數，<xref:System.Data.DataSet>物件，其代表的資料行**ProductCategoryID**並**名稱**中的欄位**Production.ProductCategory**資料表和整數，表示批次大小 （批次中的資料列數目）。</span><span class="sxs-lookup"><span data-stu-id="df6be-121">The procedure takes two arguments, a <xref:System.Data.DataSet> object that has columns representing the **ProductCategoryID** and **Name** fields in the **Production.ProductCategory** table, and an integer representing the batch size (the number of rows in the batch).</span></span> <span data-ttu-id="df6be-122">程式碼會建立新的 <xref:System.Data.SqlClient.SqlDataAdapter> 物件，並設定其 <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>、<xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> 和 <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="df6be-122">The code creates a new <xref:System.Data.SqlClient.SqlDataAdapter> object, setting its <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, and <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> properties.</span></span> <span data-ttu-id="df6be-123">程式碼假設 <xref:System.Data.DataSet> 物件具有已修改過的資料列。</span><span class="sxs-lookup"><span data-stu-id="df6be-123">The code assumes that the <xref:System.Data.DataSet> object has modified rows.</span></span> <span data-ttu-id="df6be-124">它會設定 `UpdateBatchSize` 屬性並執行更新。</span><span class="sxs-lookup"><span data-stu-id="df6be-124">It sets the `UpdateBatchSize` property and executes the update.</span></span>  
  
```vb  
Public Sub BatchUpdate( _  
  ByVal dataTable As DataTable, ByVal batchSize As Int32)  
    ' Assumes GetConnectionString() returns a valid connection string.  
    Dim connectionString As String = GetConnectionString()  
  
    ' Connect to the AdventureWorks database.  
    Using connection As New SqlConnection(connectionString)  
        ' Create a SqlDataAdapter.  
        Dim adapter As New SqlDataAdapter()  
  
        'Set the UPDATE command and parameters.  
        adapter.UpdateCommand = New SqlCommand( _  
          "UPDATE Production.ProductCategory SET " _  
          & "Name=@Name WHERE ProductCategoryID=@ProdCatID;", _  
          connection)  
        adapter.UpdateCommand.Parameters.Add("@Name", _  
          SqlDbType.NVarChar, 50, "Name")  
        adapter.UpdateCommand.Parameters.Add("@ProdCatID",  _  
          SqlDbType.Int, 4, " ProductCategoryID ")  
        adapter.UpdateCommand.UpdatedRowSource = _  
          UpdateRowSource.None  
  
        'Set the INSERT command and parameter.  
        adapter.InsertCommand = New SqlCommand( _  
          "INSERT INTO Production.ProductCategory (Name) VALUES (@Name);", _  
  connection)  
        adapter.InsertCommand.Parameters.Add("@Name", _  
          SqlDbType.NVarChar, 50, "Name")  
        adapter.InsertCommand.UpdatedRowSource = _  
          UpdateRowSource.None  
  
        'Set the DELETE command and parameter.  
        adapter.DeleteCommand = New SqlCommand( _  
          "DELETE FROM Production.ProductCategory " _  
          & "WHERE ProductCategoryID=@ProdCatID;", connection)  
        adapter.DeleteCommand.Parameters.Add("@ProdCatID", _  
           SqlDbType.Int, 4, " ProductCategoryID ")  
        adapter.DeleteCommand.UpdatedRowSource = UpdateRowSource.None  
  
        ' Set the batch size.  
        adapter.UpdateBatchSize = batchSize  
  
        ' Execute the update.  
        adapter.Update(dataTable)  
    End Using  
End Sub  
```  
  
```csharp  
public static void BatchUpdate(DataTable dataTable,Int32 batchSize)  
{  
    // Assumes GetConnectionString() returns a valid connection string.  
    string connectionString = GetConnectionString();  
  
    // Connect to the AdventureWorks database.  
    using (SqlConnection connection = new   
      SqlConnection(connectionString))  
    {  
  
        // Create a SqlDataAdapter.  
        SqlDataAdapter adapter = new SqlDataAdapter();  
  
        // Set the UPDATE command and parameters.  
        adapter.UpdateCommand = new SqlCommand(  
            "UPDATE Production.ProductCategory SET "  
            + "Name=@Name WHERE ProductCategoryID=@ProdCatID;",   
            connection);  
        adapter.UpdateCommand.Parameters.Add("@Name",   
           SqlDbType.NVarChar, 50, "Name");  
        adapter.UpdateCommand.Parameters.Add("@ProdCatID",   
           SqlDbType.Int, 4, "ProductCategoryID");  
         adapter.UpdateCommand.UpdatedRowSource = UpdateRowSource.None;  
  
        // Set the INSERT command and parameter.  
        adapter.InsertCommand = new SqlCommand(  
            "INSERT INTO Production.ProductCategory (Name) VALUES (@Name);",   
            connection);  
        adapter.InsertCommand.Parameters.Add("@Name",   
          SqlDbType.NVarChar, 50, "Name");  
        adapter.InsertCommand.UpdatedRowSource = UpdateRowSource.None;  
  
        // Set the DELETE command and parameter.  
        adapter.DeleteCommand = new SqlCommand(  
            "DELETE FROM Production.ProductCategory "  
            + "WHERE ProductCategoryID=@ProdCatID;", connection);  
        adapter.DeleteCommand.Parameters.Add("@ProdCatID",   
          SqlDbType.Int, 4, "ProductCategoryID");  
        adapter.DeleteCommand.UpdatedRowSource = UpdateRowSource.None;  
  
        // Set the batch size.  
        adapter.UpdateBatchSize = batchSize;  
  
        // Execute the update.  
        adapter.Update(dataTable);  
    }  
}  
```  
  
## <a name="handling-batch-update-related-events-and-errors"></a><span data-ttu-id="df6be-125">處理批次更新的相關事件和錯誤</span><span class="sxs-lookup"><span data-stu-id="df6be-125">Handling Batch Update-Related Events and Errors</span></span>  
 <span data-ttu-id="df6be-126">**DataAdapter**有兩個與更新相關的事件： **RowUpdating**並**RowUpdated**。</span><span class="sxs-lookup"><span data-stu-id="df6be-126">The **DataAdapter** has two update-related events: **RowUpdating** and **RowUpdated**.</span></span> <span data-ttu-id="df6be-127">停用舊版 ADO.NET 的批次處理時，會針對已處理的每個資料列產生其中一個事件。</span><span class="sxs-lookup"><span data-stu-id="df6be-127">In previous versions of ADO.NET, when batch processing is disabled, each of these events is generated once for each row processed.</span></span> <span data-ttu-id="df6be-128">**RowUpdating**在更新之前，會產生並**RowUpdated**資料庫更新完成之後產生。</span><span class="sxs-lookup"><span data-stu-id="df6be-128">**RowUpdating** is generated before the update occurs, and **RowUpdated** is generated after the database update has been completed.</span></span>  
  
### <a name="event-behavior-changes-with-batch-updates"></a><span data-ttu-id="df6be-129">批次更新時所變更的事件行為</span><span class="sxs-lookup"><span data-stu-id="df6be-129">Event Behavior Changes with Batch Updates</span></span>  
 <span data-ttu-id="df6be-130">啟用批次處理時，會在單一資料庫作業中更新多個資料列。</span><span class="sxs-lookup"><span data-stu-id="df6be-130">When batch processing is enabled, multiple rows are updated in a single database operation.</span></span> <span data-ttu-id="df6be-131">因此，每個批次作業只會發生一個 `RowUpdated` 事件，而每個已處理的資料列則會發生 `RowUpdating` 事件。</span><span class="sxs-lookup"><span data-stu-id="df6be-131">Therefore, only one `RowUpdated` event occurs for each batch, whereas the `RowUpdating` event occurs for each row processed.</span></span> <span data-ttu-id="df6be-132">停用批次處理時，會以一對一交錯的方式引發這兩個事件，即針對一個資料列引發一個 `RowUpdating` 事件和一個 `RowUpdated` 事件，再針對下一個資料列引發一個 `RowUpdating` 事件和一個 `RowUpdated` 事件，直到處理完所有資料列為止。</span><span class="sxs-lookup"><span data-stu-id="df6be-132">When batch processing is disabled, the two events are fired with one-to-one interleaving, where one `RowUpdating` event and one `RowUpdated` event fire for a row, and then one `RowUpdating` and one `RowUpdated` event fire for the next row, until all of the rows are processed.</span></span>  
  
### <a name="accessing-updated-rows"></a><span data-ttu-id="df6be-133">存取更新的資料列</span><span class="sxs-lookup"><span data-stu-id="df6be-133">Accessing Updated Rows</span></span>  
 <span data-ttu-id="df6be-134">停用批次處理後，就可以使用 <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> 類別的 <xref:System.Data.Common.RowUpdatedEventArgs> 屬性存取正在更新的資料列。</span><span class="sxs-lookup"><span data-stu-id="df6be-134">When batch processing is disabled, the row being updated can be accessed using the <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> property of the <xref:System.Data.Common.RowUpdatedEventArgs> class.</span></span>  
  
 <span data-ttu-id="df6be-135">啟用批次處理時，會針對多個資料列產生單一 `RowUpdated` 事件。</span><span class="sxs-lookup"><span data-stu-id="df6be-135">When batch processing is enabled, a single `RowUpdated` event is generated for multiple rows.</span></span> <span data-ttu-id="df6be-136">因此，每個資料列的 `Row` 屬性值都是 null。</span><span class="sxs-lookup"><span data-stu-id="df6be-136">Therefore, the value of the `Row` property for each row is null.</span></span> <span data-ttu-id="df6be-137">但仍會針對每個資料列產生 `RowUpdating` 事件。</span><span class="sxs-lookup"><span data-stu-id="df6be-137">`RowUpdating` events are still generated for each row.</span></span> <span data-ttu-id="df6be-138">您可以使用 <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> 類別的 <xref:System.Data.Common.RowUpdatedEventArgs> 方法，將處理的資料列參考複製至陣列，以存取這些資料列。</span><span class="sxs-lookup"><span data-stu-id="df6be-138">The <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> method of the <xref:System.Data.Common.RowUpdatedEventArgs> class allows you to access the processed rows by copying references to the rows into an array.</span></span> <span data-ttu-id="df6be-139">如果目前未處理任何資料列，則 `CopyToRows` 會擲回 <xref:System.ArgumentNullException>。</span><span class="sxs-lookup"><span data-stu-id="df6be-139">If no rows are being processed, `CopyToRows` throws an <xref:System.ArgumentNullException>.</span></span> <span data-ttu-id="df6be-140">呼叫 <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> 方法前，請使用 <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> 屬性傳回已處理的資料列數。</span><span class="sxs-lookup"><span data-stu-id="df6be-140">Use the <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> property to return the number of rows processed before calling the <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> method.</span></span>  
  
### <a name="handling-data-errors"></a><span data-ttu-id="df6be-141">處理資料錯誤 </span><span class="sxs-lookup"><span data-stu-id="df6be-141">Handling Data Errors</span></span>  
 <span data-ttu-id="df6be-142">批次執行與執行每個獨立陳述式具有相同的效果。</span><span class="sxs-lookup"><span data-stu-id="df6be-142">Batch execution has the same effect as the execution of each individual statement.</span></span> <span data-ttu-id="df6be-143">系統會以陳述式加入至批次的順序執行它們。</span><span class="sxs-lookup"><span data-stu-id="df6be-143">Statements are executed in the order that the statements were added to the batch.</span></span> <span data-ttu-id="df6be-144">批次模式下所發生的錯誤，與停用批次模式所發生的錯誤，擁有相同的處理方式。</span><span class="sxs-lookup"><span data-stu-id="df6be-144">Errors are handled the same way in batch mode as they are when batch mode is disabled.</span></span> <span data-ttu-id="df6be-145">每個資料列是分開處理的。</span><span class="sxs-lookup"><span data-stu-id="df6be-145">Each row is processed separately.</span></span> <span data-ttu-id="df6be-146">在 <xref:System.Data.DataRow> 內的對應 <xref:System.Data.DataTable> 中，只會更新資料庫中已成功處理的資料列。</span><span class="sxs-lookup"><span data-stu-id="df6be-146">Only rows that have been successfully processed in the database will be updated in the corresponding <xref:System.Data.DataRow> within the <xref:System.Data.DataTable>.</span></span>  
  
 <span data-ttu-id="df6be-147">資料提供者和後端資料庫伺服器決定批次執行能使用哪些 SQL 建構。</span><span class="sxs-lookup"><span data-stu-id="df6be-147">The data provider and the back-end database server determine which SQL constructs are supported for batch execution.</span></span> <span data-ttu-id="df6be-148">如果要求執行不受支援的陳述式，則可能擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="df6be-148">An exception may be thrown if a non-supported statement is submitted for execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df6be-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df6be-149">See Also</span></span>  
 [<span data-ttu-id="df6be-150">DataAdapter 和 DataReader</span><span class="sxs-lookup"><span data-stu-id="df6be-150">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="df6be-151">使用 DataAdapter 更新資料來源</span><span class="sxs-lookup"><span data-stu-id="df6be-151">Updating Data Sources with DataAdapters</span></span>](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [<span data-ttu-id="df6be-152">處理 DataAdapter 事件</span><span class="sxs-lookup"><span data-stu-id="df6be-152">Handling DataAdapter Events</span></span>](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)  
 [<span data-ttu-id="df6be-153">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="df6be-153">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
