---
title: "處理 DataAdapter 的事件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 11515b25-ee49-4b1d-9294-a142147c1ec5
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 71524de2edbedb24cacc6727654aac5be0a48bb7
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="handling-dataadapter-events"></a><span data-ttu-id="bf84e-102">處理 DataAdapter 的事件</span><span class="sxs-lookup"><span data-stu-id="bf84e-102">Handling DataAdapter Events</span></span>
<span data-ttu-id="bf84e-103">ADO.NET <xref:System.Data.Common.DataAdapter> 公開 (Expose) 的三個事件可讓您用來回應資料來源中的資料變更。</span><span class="sxs-lookup"><span data-stu-id="bf84e-103">The ADO.NET <xref:System.Data.Common.DataAdapter> exposes three events that you can use to respond to changes made to data at the data source.</span></span> <span data-ttu-id="bf84e-104">下表說明 `DataAdapter` 事件。</span><span class="sxs-lookup"><span data-stu-id="bf84e-104">The following table shows the `DataAdapter` events.</span></span>  
  
|<span data-ttu-id="bf84e-105">事件</span><span class="sxs-lookup"><span data-stu-id="bf84e-105">Event</span></span>|<span data-ttu-id="bf84e-106">描述</span><span class="sxs-lookup"><span data-stu-id="bf84e-106">Description</span></span>|  
|-----------|-----------------|  
|`RowUpdating`|<span data-ttu-id="bf84e-107">資料列上的 UPDATE、INSERT 或 DELETE 作業 (呼叫其中一個 `Update` 方法) 即將開始。</span><span class="sxs-lookup"><span data-stu-id="bf84e-107">An UPDATE, INSERT, or DELETE operation on a row (by a call to one of the `Update` methods) is about to begin.</span></span>|  
|`RowUpdated`|<span data-ttu-id="bf84e-108">資料列上的 UPDATE、INSERT 或 DELETE 作業 (呼叫其中一個 `Update` 方法) 已經完成。</span><span class="sxs-lookup"><span data-stu-id="bf84e-108">An UPDATE, INSERT, or DELETE operation on a row (by a call to one of the `Update` methods) is complete.</span></span>|  
|`FillError`|<span data-ttu-id="bf84e-109">`Fill` 作業過程中發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="bf84e-109">An error has occurred during a `Fill` operation.</span></span>|  
  
## <a name="rowupdating-and-rowupdated"></a><span data-ttu-id="bf84e-110">RowUpdating 和 RowUpdated</span><span class="sxs-lookup"><span data-stu-id="bf84e-110">RowUpdating and RowUpdated</span></span>  
 <span data-ttu-id="bf84e-111">在資料來源中處理 `RowUpdating` 之資料列的任何更新之前，會引發 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="bf84e-111">`RowUpdating` is raised before any update to a row from the <xref:System.Data.DataSet> has been processed at the data source.</span></span> <span data-ttu-id="bf84e-112">在資料來源中處理 `RowUpdated` 之資料列的任何更新之後，會引發 `DataSet`。</span><span class="sxs-lookup"><span data-stu-id="bf84e-112">`RowUpdated` is raised after any update to a row from the `DataSet` has been processed at the data source.</span></span> <span data-ttu-id="bf84e-113">所以，您可以使用 `RowUpdating` 在更新發生前修改更新行為，讓您更能控制更新發生的時間、保留對已更新資料列的參考、取消目前更新、將更新排程於稍後進行批次處理等其他功能。</span><span class="sxs-lookup"><span data-stu-id="bf84e-113">As a result, you can use `RowUpdating` to modify update behavior before it happens, to provide additional handling when an update will occur, to retain a reference to an updated row, to cancel the current update and schedule it for a batch process to be processed later, and so on.</span></span> <span data-ttu-id="bf84e-114">`RowUpdated` 對於回應在更新期間發生的錯誤和例外狀況而言很有用。</span><span class="sxs-lookup"><span data-stu-id="bf84e-114">`RowUpdated` is useful for responding to errors and exceptions that occur during the update.</span></span> <span data-ttu-id="bf84e-115">您可以將錯誤資訊加入 `DataSet` 以及重試邏輯等等。</span><span class="sxs-lookup"><span data-stu-id="bf84e-115">You can add error information to the `DataSet`, as well as retry logic, and so on.</span></span>  
  
 <span data-ttu-id="bf84e-116">傳遞至 <xref:System.Data.Common.RowUpdatingEventArgs> 和 <xref:System.Data.Common.RowUpdatedEventArgs> 事件的 `RowUpdating` 和 `RowUpdated` 引數包括下列項目：`Command` 屬性 (參考正用來執行更新的 `Command` 物件)、`Row` 屬性 (參考包含已更新資訊的 `DataRow` 物件)、`StatementType` 屬性 (正在執行該類型的更新)、`TableMapping` (如果適用)；以及作業的 `Status`。</span><span class="sxs-lookup"><span data-stu-id="bf84e-116">The <xref:System.Data.Common.RowUpdatingEventArgs> and <xref:System.Data.Common.RowUpdatedEventArgs> arguments passed to the `RowUpdating` and `RowUpdated` events include the following: a `Command` property that references the `Command` object being used to perform the update; a `Row` property that references the `DataRow` object containing the updated information; a `StatementType` property for what type of update is being performed; the `TableMapping`, if applicable; and the `Status` of the operation.</span></span>  
  
 <span data-ttu-id="bf84e-117">您可以使用 `Status` 屬性來判斷作業期間是否發生錯誤，也可以依您的需要，控制目前和結果資料列的動作。</span><span class="sxs-lookup"><span data-stu-id="bf84e-117">You can use the `Status` property to determine if an error has occurred during the operation and, if desired, to control the actions against the current and resulting rows.</span></span> <span data-ttu-id="bf84e-118">發生事件時，`Status` 屬性即等於 `Continue` 或 `ErrorsOccurred`。</span><span class="sxs-lookup"><span data-stu-id="bf84e-118">When the event occurs, the `Status` property equals either `Continue` or `ErrorsOccurred`.</span></span> <span data-ttu-id="bf84e-119">您可以將 `Status` 屬性設成下列表格所顯示的值，以控制更新期間的後續動作。</span><span class="sxs-lookup"><span data-stu-id="bf84e-119">The following table shows the values to which you can set the `Status` property in order to control later actions during the update.</span></span>  
  
|<span data-ttu-id="bf84e-120">狀態</span><span class="sxs-lookup"><span data-stu-id="bf84e-120">Status</span></span>|<span data-ttu-id="bf84e-121">描述</span><span class="sxs-lookup"><span data-stu-id="bf84e-121">Description</span></span>|  
|------------|-----------------|  
|`Continue`|<span data-ttu-id="bf84e-122">繼續更新作業。</span><span class="sxs-lookup"><span data-stu-id="bf84e-122">Continue the update operation.</span></span>|  
|`ErrorsOccurred`|<span data-ttu-id="bf84e-123">中止更新作業並擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="bf84e-123">Abort the update operation and throw an exception.</span></span>|  
|`SkipCurrentRow`|<span data-ttu-id="bf84e-124">忽略目前資料列並繼續更新作業。</span><span class="sxs-lookup"><span data-stu-id="bf84e-124">Ignore the current row and continue the update operation.</span></span>|  
|`SkipAllRemainingRows`|<span data-ttu-id="bf84e-125">中止更新作業但不擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="bf84e-125">Abort the update operation but do not throw an exception.</span></span>|  
  
 <span data-ttu-id="bf84e-126">若將 `Status` 屬性設為 `ErrorsOccurred`，則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="bf84e-126">Setting the `Status` property to `ErrorsOccurred` causes an exception to be thrown.</span></span> <span data-ttu-id="bf84e-127">您可以將 `Errors` 屬性設定為您希望的例外狀況，以控制擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="bf84e-127">You can control which exception is thrown by setting the `Errors` property to the desired exception.</span></span> <span data-ttu-id="bf84e-128">若將 `Status` 設為其他任一值，則可避免擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="bf84e-128">Using one of the other values for `Status` prevents an exception from being thrown.</span></span>  
  
 <span data-ttu-id="bf84e-129">您也可以使用 `ContinueUpdateOnError` 屬性來處理更新資料列的錯誤。</span><span class="sxs-lookup"><span data-stu-id="bf84e-129">You can also use the `ContinueUpdateOnError` property to handle errors for updated rows.</span></span> <span data-ttu-id="bf84e-130">如果 `DataAdapter.ContinueUpdateOnError` 為 `true`，則當資料列的更新造成擲回例外狀況時，會將例外狀況的文字放入特定資料列的 `RowError` 資訊中，並繼續作業，而不擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="bf84e-130">If `DataAdapter.ContinueUpdateOnError` is `true`, when an update to a row results in an exception being thrown, the text of the exception is placed into the `RowError` information of the particular row, and processing continues without throwing an exception.</span></span> <span data-ttu-id="bf84e-131">這樣一來，您就可以在完成 `Update` 後才回應錯誤，而 `RowUpdated` 事件則是讓您在發生錯誤時立即回應該錯誤。</span><span class="sxs-lookup"><span data-stu-id="bf84e-131">This enables you to respond to errors when the `Update` is complete, in contrast to the `RowUpdated` event, which enables you to respond to errors when the error is encountered.</span></span>  
  
 <span data-ttu-id="bf84e-132">下列程式碼範例顯示如何加入和移除事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="bf84e-132">The following code sample shows how to both add and remove event handlers.</span></span> <span data-ttu-id="bf84e-133">`RowUpdating` 事件處理常式將所有的刪除記錄和時間戳記寫入記錄檔。</span><span class="sxs-lookup"><span data-stu-id="bf84e-133">The `RowUpdating` event handler writes a log of all deleted records with a time stamp.</span></span> <span data-ttu-id="bf84e-134">`RowUpdated`事件處理常式會將錯誤資訊加入`RowError`屬性中的資料列`DataSet`、 隱藏例外狀況，然後繼續處理 (鏡像的行為`ContinueUpdateOnError`  =  `true`)。</span><span class="sxs-lookup"><span data-stu-id="bf84e-134">The `RowUpdated` event handler adds error information to the `RowError` property of the row in the `DataSet`, suppresses the exception, and continues processing (mirroring the behavior of `ContinueUpdateOnError` = `true`).</span></span>  
  
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
  
## <a name="fillerror"></a><span data-ttu-id="bf84e-135">FillError</span><span class="sxs-lookup"><span data-stu-id="bf84e-135">FillError</span></span>  
 <span data-ttu-id="bf84e-136">`DataAdapter` 作業期間發生錯誤時，`FillError` 會發出 `Fill` 事件。</span><span class="sxs-lookup"><span data-stu-id="bf84e-136">The `DataAdapter` issues the `FillError` event when an error occurs during a `Fill` operation.</span></span> <span data-ttu-id="bf84e-137">當加入資料列中的資料必須放棄一些精確度，不然無法轉換為 .NET Framework 型別時，通常就會發生這類型的錯誤。</span><span class="sxs-lookup"><span data-stu-id="bf84e-137">This type of error commonly occurs when the data in the row being added could not be converted to a .NET Framework type without some loss of precision.</span></span>  
  
 <span data-ttu-id="bf84e-138">`Fill` 作業期間如果發生錯誤，則不會將目前的資料列加入 `DataTable`。</span><span class="sxs-lookup"><span data-stu-id="bf84e-138">If an error occurs during a `Fill` operation, the current row is not added to the `DataTable`.</span></span> <span data-ttu-id="bf84e-139">`FillError` 事件可讓您解析錯誤並加入資料列，或忽略排除的資料列，繼續進行 `Fill` 作業。</span><span class="sxs-lookup"><span data-stu-id="bf84e-139">The `FillError` event enables you to resolve the error and add the row, or to ignore the excluded row and continue the `Fill` operation.</span></span>  
  
 <span data-ttu-id="bf84e-140">傳遞給 `FillErrorEventArgs` 事件的 `FillError` 可包含數個屬性，讓您回應並解決錯誤。</span><span class="sxs-lookup"><span data-stu-id="bf84e-140">The `FillErrorEventArgs` passed to the `FillError` event can contain several properties that enable you to respond to and resolve errors.</span></span> <span data-ttu-id="bf84e-141">下列表格顯示 `FillErrorEventArgs` 物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="bf84e-141">The following table shows the properties of the `FillErrorEventArgs` object.</span></span>  
  
|<span data-ttu-id="bf84e-142">屬性</span><span class="sxs-lookup"><span data-stu-id="bf84e-142">Property</span></span>|<span data-ttu-id="bf84e-143">描述</span><span class="sxs-lookup"><span data-stu-id="bf84e-143">Description</span></span>|  
|--------------|-----------------|  
|`Errors`|<span data-ttu-id="bf84e-144">所發生的 `Exception`。</span><span class="sxs-lookup"><span data-stu-id="bf84e-144">The `Exception` that occurred.</span></span>|  
|`DataTable`|<span data-ttu-id="bf84e-145">發生錯誤時，填入的 `DataTable` 物件。</span><span class="sxs-lookup"><span data-stu-id="bf84e-145">The `DataTable` object being filled when the error occurred.</span></span>|  
|`Values`|<span data-ttu-id="bf84e-146">發生錯誤時，包含加入資料列值的物件陣列。</span><span class="sxs-lookup"><span data-stu-id="bf84e-146">An array of objects that contains the values of the row being added when the error occurred.</span></span> <span data-ttu-id="bf84e-147">`Values` 陣列的序數參考對應至加入資料列資料行的序數參考。</span><span class="sxs-lookup"><span data-stu-id="bf84e-147">The ordinal references of the `Values` array correspond to the ordinal references of the columns of the row being added.</span></span> <span data-ttu-id="bf84e-148">例如，`Values[0]` 便是當成資料列第一個資料行而加入的值。</span><span class="sxs-lookup"><span data-stu-id="bf84e-148">For example, `Values[0]` is the value that was being added as the first column of the row.</span></span>|  
|`Continue`|<span data-ttu-id="bf84e-149">可讓您選擇是否要擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="bf84e-149">Allows you to choose whether or not to throw an exception.</span></span> <span data-ttu-id="bf84e-150">將 `Continue` 屬性設為 `false`，即可中斷目前的 `Fill` 作業，並擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="bf84e-150">Setting the `Continue` property to `false` will halt the current `Fill` operation, and an exception will be thrown.</span></span> <span data-ttu-id="bf84e-151">將 `Continue` 設為 `true`，則不管是否發生錯誤，都將繼續進行 `Fill` 作業。</span><span class="sxs-lookup"><span data-stu-id="bf84e-151">Setting `Continue` to `true` continues the `Fill` operation despite the error.</span></span>|  
  
 <span data-ttu-id="bf84e-152">下列程式碼範例針對 `FillError` 的 `DataAdapter` 事件，加入事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="bf84e-152">The following code example adds an event handler for the `FillError` event of the `DataAdapter`.</span></span> <span data-ttu-id="bf84e-153">範例的 `FillError` 事件程式碼會在有機會回應例外狀況時，判斷是否可能會缺少精確度。</span><span class="sxs-lookup"><span data-stu-id="bf84e-153">In the `FillError` event code, the example determines if there is the potential for precision loss, providing the opportunity to respond to the exception.</span></span>  
  
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
    args.RowError = _  
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
    args.RowError =   
       "OverflowException Encountered. Value from data source: " +  
       args.Values[2];  
    args.Continue = true;  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="bf84e-154">請參閱</span><span class="sxs-lookup"><span data-stu-id="bf84e-154">See Also</span></span>  
 [<span data-ttu-id="bf84e-155">DataAdapter 和 DataReader</span><span class="sxs-lookup"><span data-stu-id="bf84e-155">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="bf84e-156">處理 DataSet 的事件</span><span class="sxs-lookup"><span data-stu-id="bf84e-156">Handling DataSet Events</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)  
 [<span data-ttu-id="bf84e-157">處理 DataTable 事件</span><span class="sxs-lookup"><span data-stu-id="bf84e-157">Handling DataTable Events</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 [<span data-ttu-id="bf84e-158">事件</span><span class="sxs-lookup"><span data-stu-id="bf84e-158">Events</span></span>](../../../../docs/standard/events/index.md)  
 [<span data-ttu-id="bf84e-159">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="bf84e-159">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
