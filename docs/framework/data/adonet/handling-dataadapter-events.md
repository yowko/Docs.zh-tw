---
title: 處理 DataAdapter 的事件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 11515b25-ee49-4b1d-9294-a142147c1ec5
ms.openlocfilehash: adda1bd1f16a43087d43382f9b7476856f4bc5c9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54692700"
---
# <a name="handling-dataadapter-events"></a>處理 DataAdapter 的事件
ADO.NET <xref:System.Data.Common.DataAdapter> 公開 (Expose) 的三個事件可讓您用來回應資料來源中的資料變更。 下表說明 `DataAdapter` 事件。  
  
|事件|描述|  
|-----------|-----------------|  
|`RowUpdating`|資料列上的 UPDATE、INSERT 或 DELETE 作業 (呼叫其中一個 `Update` 方法) 即將開始。|  
|`RowUpdated`|資料列上的 UPDATE、INSERT 或 DELETE 作業 (呼叫其中一個 `Update` 方法) 已經完成。|  
|`FillError`|`Fill` 作業過程中發生錯誤。|  
  
## <a name="rowupdating-and-rowupdated"></a>RowUpdating 和 RowUpdated  
 在資料來源中處理 `RowUpdating` 之資料列的任何更新之前，會引發 <xref:System.Data.DataSet>。 在資料來源中處理 `RowUpdated` 之資料列的任何更新之後，會引發 `DataSet`。 所以，您可以使用 `RowUpdating` 在更新發生前修改更新行為，讓您更能控制更新發生的時間、保留對已更新資料列的參考、取消目前更新、將更新排程於稍後進行批次處理等其他功能。 `RowUpdated` 對於回應在更新期間發生的錯誤和例外狀況而言很有用。 您可以將錯誤資訊加入 `DataSet` 以及重試邏輯等等。  
  
 傳遞至 <xref:System.Data.Common.RowUpdatingEventArgs> 和 <xref:System.Data.Common.RowUpdatedEventArgs> 事件的 `RowUpdating` 和 `RowUpdated` 引數包括下列項目：`Command` 屬性 (參考正用來執行更新的 `Command` 物件)、`Row` 屬性 (參考包含已更新資訊的 `DataRow` 物件)、`StatementType` 屬性 (正在執行該類型的更新)、`TableMapping` (如果適用)；以及作業的 `Status`。  
  
 您可以使用 `Status` 屬性來判斷作業期間是否發生錯誤，也可以依您的需要，控制目前和結果資料列的動作。 發生事件時，`Status` 屬性即等於 `Continue` 或 `ErrorsOccurred`。 您可以將 `Status` 屬性設成下列表格所顯示的值，以控制更新期間的後續動作。  
  
|狀態|描述|  
|------------|-----------------|  
|`Continue`|繼續更新作業。|  
|`ErrorsOccurred`|中止更新作業並擲回例外狀況。|  
|`SkipCurrentRow`|忽略目前資料列並繼續更新作業。|  
|`SkipAllRemainingRows`|中止更新作業但不擲回例外狀況。|  
  
 若將 `Status` 屬性設為 `ErrorsOccurred`，則會擲回例外狀況。 您可以將 `Errors` 屬性設定為您希望的例外狀況，以控制擲回的例外狀況。 若將 `Status` 設為其他任一值，則可避免擲回例外狀況。  
  
 您也可以使用 `ContinueUpdateOnError` 屬性來處理更新資料列的錯誤。 如果 `DataAdapter.ContinueUpdateOnError` 為 `true`，則當資料列的更新造成擲回例外狀況時，會將例外狀況的文字放入特定資料列的 `RowError` 資訊中，並繼續作業，而不擲回例外狀況。 這樣一來，您就可以在完成 `Update` 後才回應錯誤，而 `RowUpdated` 事件則是讓您在發生錯誤時立即回應該錯誤。  
  
 下列程式碼範例顯示如何加入和移除事件處理常式。 `RowUpdating` 事件處理常式將所有的刪除記錄和時間戳記寫入記錄檔。 `RowUpdated`事件處理常式會將錯誤資訊`RowError`屬性中的資料列`DataSet`中，會隱藏例外狀況，然後繼續處理 (鏡像的行為`ContinueUpdateOnError`  =  `true`)。  
  
```vb  
' Assumes that connection is a valid SqlConnection object.  
Dim custAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers", connection)  
  
' Add handlers.  
AddHandler custAdapter.RowUpdating, New SqlRowUpdatingEventHandler( _  
  AddressOf OnRowUpdating)  
AddHandler custAdapter.RowUpdated, New SqlRowUpdatedEventHandler(  
  AddressOf OnRowUpdated)  
  
' Set DataAdapter command properties, fill DataSet, and modify DataSet.  
  
custAdapter.Update(custDS, "Customers")  
  
' Remove handlers.  
RemoveHandler custAdapter.RowUpdating, _  
  New SqlRowUpdatingEventHandler(AddressOf OnRowUpdating)  
RemoveHandler custAdapter.RowUpdated, _  
  New SqlRowUpdatedEventHandler(AddressOf OnRowUpdated)  
  
Private Shared Sub OnRowUpdating(sender As Object, _  
  args As SqlRowUpdatingEventArgs)  
  If args.StatementType = StatementType.Delete Then  
    Dim tw As System.IO.TextWriter = _  
  System.IO.File.AppendText("Deletes.log")  
    tw.WriteLine( _  
      "{0}: Customer {1} Deleted.", DateTime.Now, args.Row(_  
      "CustomerID", DataRowVersion.Original))  
    tw.Close()  
  End If  
End Sub  
  
Private Shared Sub OnRowUpdated( _  
  sender As Object, args As SqlRowUpdatedEventArgs)  
  If args.Status = UpdateStatus.ErrorsOccurred  
    args.Status = UpdateStatus.SkipCurrentRow  
    args.Row.RowError = args.Errors.Message  
  End If  
End Sub  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection object.  
SqlDataAdapter custAdapter = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers", connection);  
  
// Add handlers.  
custAdapter.RowUpdating += new SqlRowUpdatingEventHandler(OnRowUpdating);  
custAdapter.RowUpdated += new SqlRowUpdatedEventHandler(OnRowUpdated);  
  
// Set DataAdapter command properties, fill DataSet, modify DataSet.  
  
custAdapter.Update(custDS, "Customers");  
  
// Remove handlers.  
custAdapter.RowUpdating -= new SqlRowUpdatingEventHandler(OnRowUpdating);  
custAdapter.RowUpdated -= new SqlRowUpdatedEventHandler(OnRowUpdated);  
  
protected static void OnRowUpdating(  
  object sender, SqlRowUpdatingEventArgs args)  
{  
  if (args.StatementType == StatementType.Delete)  
  {  
    System.IO.TextWriter tw = System.IO.File.AppendText("Deletes.log");  
    tw.WriteLine(  
      "{0}: Customer {1} Deleted.", DateTime.Now,   
       args.Row["CustomerID", DataRowVersion.Original]);  
    tw.Close();  
  }  
}  
  
protected static void OnRowUpdated(  
  object sender, SqlRowUpdatedEventArgs args)  
{  
  if (args.Status == UpdateStatus.ErrorsOccurred)  
  {  
    args.Row.RowError = args.Errors.Message;  
    args.Status = UpdateStatus.SkipCurrentRow;  
  }  
}  
```  
  
## <a name="fillerror"></a>FillError  
 `DataAdapter` 作業期間發生錯誤時，`FillError` 會發出 `Fill` 事件。 當加入資料列中的資料必須放棄一些精確度，不然無法轉換為 .NET Framework 型別時，通常就會發生這類型的錯誤。  
  
 `Fill` 作業期間如果發生錯誤，則不會將目前的資料列加入 `DataTable`。 `FillError` 事件可讓您解析錯誤並加入資料列，或忽略排除的資料列，繼續進行 `Fill` 作業。  
  
 傳遞給 `FillErrorEventArgs` 事件的 `FillError` 可包含數個屬性，讓您回應並解決錯誤。 下列表格顯示 `FillErrorEventArgs` 物件的屬性。  
  
|屬性|描述|  
|--------------|-----------------|  
|`Errors`|所發生的 `Exception`。|  
|`DataTable`|發生錯誤時，填入的 `DataTable` 物件。|  
|`Values`|發生錯誤時，包含加入資料列值的物件陣列。 `Values` 陣列的序數參考對應至加入資料列資料行的序數參考。 例如，`Values[0]` 便是當成資料列第一個資料行而加入的值。|  
|`Continue`|可讓您選擇是否要擲回例外狀況。 將 `Continue` 屬性設為 `false`，即可中斷目前的 `Fill` 作業，並擲回例外狀況。 將 `Continue` 設為 `true`，則不管是否發生錯誤，都將繼續進行 `Fill` 作業。|  
  
 下列程式碼範例針對 `FillError` 的 `DataAdapter` 事件，加入事件處理常式。 範例的 `FillError` 事件程式碼會在有機會回應例外狀況時，判斷是否可能會缺少精確度。  
  
```vb  
AddHandler adapter.FillError, New FillErrorEventHandler( _  
  AddressOf FillError)  
  
Dim dataSet As DataSet = New DataSet  
adapter.Fill(dataSet, "ThisTable")  
  
Private Shared Sub FillError(sender As Object, _  
  args As FillErrorEventArgs)  
  If args.Errors.GetType() Is Type.GetType("System.OverflowException") Then  
    ' Code to handle precision loss.  
    ' Add a row to table using the values from the first two columns.  
    DataRow myRow = args.DataTable.Rows.Add(New Object() _  
      {args.Values(0), args.Values(1), DBNull.Value})  
    ' Set the RowError containing the value for the third column.  
    myRow.RowError = _  
      "OverflowException encountered. Value from data source: " & _  
      args.Values(2)  
    args.Continue = True  
  End If  
End Sub  
```  
  
```csharp  
adapter.FillError += new FillErrorEventHandler(FillError);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, "ThisTable");  
  
protected static void FillError(object sender, FillErrorEventArgs args)  
{  
  if (args.Errors.GetType() == typeof(System.OverflowException))  
  {  
    // Code to handle precision loss.  
    //Add a row to table using the values from the first two columns.  
    DataRow myRow = args.DataTable.Rows.Add(new object[]  
       {args.Values[0], args.Values[1], DBNull.Value});  
    //Set the RowError containing the value for the third column.  
    myRow.RowError =   
       "OverflowException Encountered. Value from data source: " +  
       args.Values[2];  
    args.Continue = true;  
  }  
}  
```  
  
## <a name="see-also"></a>另請參閱
- [DataAdapter 和 DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [處理 DataSet 的事件](../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)
- [處理 DataTable 事件](../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)
- [事件](../../../../docs/standard/events/index.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
