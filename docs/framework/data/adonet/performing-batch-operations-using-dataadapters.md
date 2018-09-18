---
title: 使用 DataAdapter 執行批次作業
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e72ed5af-b24f-486c-8429-c8fd2208f844
ms.openlocfilehash: cfc77ff3b030ffebf52feab0190f81fc4e581cf9
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "45989572"
---
# <a name="performing-batch-operations-using-dataadapters"></a>使用 DataAdapter 執行批次作業
ADO.NET 中的批次支援可讓 <xref:System.Data.Common.DataAdapter> 針對從 <xref:System.Data.DataSet> 或 <xref:System.Data.DataTable> 至伺服器的 INSERT、UPDATE 與 DELETE 作業進行分組，而非一次傳送一個作業。 如此可降低往返於伺服器的次數，因此一般都能夠大幅提升作業效能。 SQL Server (<xref:System.Data.SqlClient>) 和 Oracle (<xref:System.Data.OracleClient>) 的 .NET 資料提供者都支援批次更新。  
  
 在舊版 ADO.NET 中，以 <xref:System.Data.DataSet> 的變更更新資料庫時，`Update` 的 `DataAdapter` 方法會一次變更資料庫的一個資料列。 當它逐一查看指定之 <xref:System.Data.DataTable> 的資料列時，它會檢查每一個 <xref:System.Data.DataRow>，以查看是否已修改該資料列。 如果已修改資料列，則會根據該資料列的 `UpdateCommand` 屬性值，呼叫適當的 `InsertCommand`、`DeleteCommand` 或 <xref:System.Data.DataRow.RowState%2A>。 更新每個資料列時，都必須透過網路與資料庫往來通訊。  
  
 從 ADO.NET 2.0 開始，<xref:System.Data.Common.DbDataAdapter> 就會公開 (Expose) <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A> 屬性。 將 `UpdateBatchSize` 設為正整數值，可將資料庫更新當成所指定大小的批次傳送。 例如，將 `UpdateBatchSize` 設為 10，會分組 10 個不同的陳述式，並將它們當做單一批次送出。 將 `UpdateBatchSize` 設為 0，可讓 <xref:System.Data.Common.DataAdapter> 使用伺服器可處理的最大批次大小。 將其設定為 1 則可停用批次更新，此時一次只能傳送一個資料列。  
  
 執行極大的批次可能會降低效能。 因此，您應該先測試理想的批次大小設定，再實作應用程式。  
  
## <a name="using-the-updatebatchsize-property"></a>使用 UpdateBatchSize 屬性  
 啟用批次更新時，應該將 DataAdapter 的 <xref:System.Data.IDbCommand.UpdatedRowSource%2A>、`UpdateCommand` 和 `InsertCommand` 的 `DeleteCommand` 屬性值設為 <xref:System.Data.UpdateRowSource.None> 或 <xref:System.Data.UpdateRowSource.OutputParameters>。 執行批次更新時，命令之 <xref:System.Data.IDbCommand.UpdatedRowSource%2A> 或 <xref:System.Data.UpdateRowSource.FirstReturnedRecord> 的 <xref:System.Data.UpdateRowSource.Both> 屬性值無效。  
  
 下列程序示範 `UpdateBatchSize` 屬性的用法。 此程序會採用兩個引數，<xref:System.Data.DataSet>物件，其代表的資料行**ProductCategoryID**並**名稱**中的欄位**Production.ProductCategory**資料表和整數，表示批次大小 （批次中的資料列數目）。 程式碼會建立新的 <xref:System.Data.SqlClient.SqlDataAdapter> 物件，並設定其 <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>、<xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> 和 <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> 屬性。 程式碼假設 <xref:System.Data.DataSet> 物件具有已修改過的資料列。 它會設定 `UpdateBatchSize` 屬性並執行更新。  
  
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
  
## <a name="handling-batch-update-related-events-and-errors"></a>處理批次更新的相關事件和錯誤  
 **DataAdapter**有兩個與更新相關的事件： **RowUpdating**並**RowUpdated**。 停用舊版 ADO.NET 的批次處理時，會針對已處理的每個資料列產生其中一個事件。 **RowUpdating**在更新之前，會產生並**RowUpdated**資料庫更新完成之後產生。  
  
### <a name="event-behavior-changes-with-batch-updates"></a>批次更新時所變更的事件行為  
 啟用批次處理時，會在單一資料庫作業中更新多個資料列。 因此，每個批次作業只會發生一個 `RowUpdated` 事件，而每個已處理的資料列則會發生 `RowUpdating` 事件。 停用批次處理時，會以一對一交錯的方式引發這兩個事件，即針對一個資料列引發一個 `RowUpdating` 事件和一個 `RowUpdated` 事件，再針對下一個資料列引發一個 `RowUpdating` 事件和一個 `RowUpdated` 事件，直到處理完所有資料列為止。  
  
### <a name="accessing-updated-rows"></a>存取更新的資料列  
 停用批次處理後，就可以使用 <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> 類別的 <xref:System.Data.Common.RowUpdatedEventArgs> 屬性存取正在更新的資料列。  
  
 啟用批次處理時，會針對多個資料列產生單一 `RowUpdated` 事件。 因此，每個資料列的 `Row` 屬性值都是 null。 但仍會針對每個資料列產生 `RowUpdating` 事件。 您可以使用 <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> 類別的 <xref:System.Data.Common.RowUpdatedEventArgs> 方法，將處理的資料列參考複製至陣列，以存取這些資料列。 如果目前未處理任何資料列，則 `CopyToRows` 會擲回 <xref:System.ArgumentNullException>。 呼叫 <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> 方法前，請使用 <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> 屬性傳回已處理的資料列數。  
  
### <a name="handling-data-errors"></a>處理資料錯誤   
 批次執行與執行每個獨立陳述式具有相同的效果。 系統會以陳述式加入至批次的順序執行它們。 批次模式下所發生的錯誤，與停用批次模式所發生的錯誤，擁有相同的處理方式。 每個資料列是分開處理的。 在 <xref:System.Data.DataRow> 內的對應 <xref:System.Data.DataTable> 中，只會更新資料庫中已成功處理的資料列。  
  
 資料提供者和後端資料庫伺服器決定批次執行能使用哪些 SQL 建構。 如果要求執行不受支援的陳述式，則可能擲回例外狀況。  
  
## <a name="see-also"></a>另請參閱  
 [DataAdapter 和 DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [使用 DataAdapter 更新資料來源](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [處理 DataAdapter 事件](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
