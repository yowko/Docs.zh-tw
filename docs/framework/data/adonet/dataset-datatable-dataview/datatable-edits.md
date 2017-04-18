---
title: "DataTable 編輯 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f08008a9-042e-4de9-94f3-4f0e502b1eb5
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# DataTable 編輯
變更 <xref:System.Data.DataRow> 中的資料行值時，這些變更會立即放入資料列的目前狀態中。  接著，會將 <xref:System.Data.DataRowState> 設為 **Modified**，並使用 **DataRow** 的 <xref:System.Data.DataRow.AcceptChanges%2A> 或 <xref:System.Data.DataRow.RejectChanges%2A> 方法來接受或拒絕變更。  **DataRow** 同時提供三種方法，可供您在編輯資料列時用來暫停資料列的狀態。  這些方法是 <xref:System.Data.DataRow.BeginEdit%2A>、<xref:System.Data.DataRow.EndEdit%2A> 和 <xref:System.Data.DataRow.CancelEdit%2A>。  
  
 當您直接修改 **DataRow** 中的資料行值時，**DataRow** 會使用 **Current**、**Default** 與 **Original** 資料列版本來管理資料行的值。  除了這些資料列版本以外，**BeginEdit**、**EndEdit** 與 **CancelEdit** 方法還使用第四個資料列版本：**Proposed**。  如需資料列版本的詳細資訊，請參閱 [資料列狀態和資料列版本](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)。  
  
 **Proposed** 資料列版本會於編輯作業期間存在，而編輯作業會於呼叫 **BeginEdit** 開始，並且在使用 **EndEdit** 或 **CancelEdit** 或呼叫 **AcceptChanges** 或 **RejectChanges** 時結束。  
  
 在編輯作業期間，您可以透過評估 **DataTable** 之 **ColumnChanged** 事件的 **ProposedValue**，將驗證邏輯套用到個別的資料行上。  **ColumnChanged** 事件含有 **DataColumnChangeEventArgs**，其中保存了對變更中資料行的參考和對 **ProposedValue** 的參考。  在您評估建議的值之後，就可以修改該值或取消編輯。  當編輯作業結束後，資料列將從 **Proposed** 狀態中移除。  
  
 您可以呼叫 **EndEdit** 來確認編輯，或者呼叫 **CancelEdit** 來取消編輯。  請注意，當 **EndEdit** 確認您的編輯後，除非呼叫 **AcceptChanges**，否則 **DataSet** 並不會真正接受變更。  也請注意，如果您在使用 **EndEdit** 或 **CancelEdit** 結束編輯作業之前便呼叫 **AcceptChanges**，編輯作業會結束，而且 **Current** 和 **Original** 這兩個資料列版本都會接受 **Proposed** 資料列的值。  同樣的，呼叫 **RejectChanges** 將會結束編輯作業，並放棄 **Current** 和 **Proposed** 資料列版本。  如果您在呼叫 **AcceptChanges** 或 **RejectChanges** 之後才呼叫 **EndEdit** 或 **CancelEdit**，則會因為編輯作業已結束，所以這兩項作業將不會生效。  
  
 下列範例展示如何搭配使用 **BeginEdit** 與 **EndEdit** 和 **CancelEdit**。  此範例也會檢查 **ColumnChanged** 事件的 **ProposedValue**，並決定是否取消編輯作業。  
  
```vb  
Dim workTable As DataTable = New DataTable  
workTable.Columns.Add("LastName", Type.GetType("System.String"))  
  
AddHandler workTable.ColumnChanged, _  
  New DataColumnChangeEventHandler(AddressOf OnColumnChanged)  
  
Dim workRow As DataRow = workTable.NewRow()  
workRow(0) = "Smith"  
workTable.Rows.Add(workRow)  
  
workRow.BeginEdit()  
' Causes the ColumnChanged event to write a message and cancel the edit.  
workRow(0) = ""       
workRow.EndEdit()  
  
' Displays "Smith, New".  
Console.WriteLine("{0}, {1}", workRow(0), workRow.RowState)  
  
Private Shared Sub OnColumnChanged( _  
  sender As Object, args As DataColumnChangeEventArgs)  
  If args.Column.ColumnName = "LastName" Then  
    If args.ProposedValue.ToString() = "" Then  
      Console.WriteLine("Last Name cannot be blank.  Edit canceled.")  
      args.Row.CancelEdit()  
    End If  
  End If  
End Sub  
  
```  
  
```csharp  
DataTable workTable  = new DataTable();  
workTable.Columns.Add("LastName", typeof(String));  
  
workTable.ColumnChanged +=   
  new DataColumnChangeEventHandler(OnColumnChanged);  
  
DataRow workRow = workTable.NewRow();  
workRow[0] = "Smith";  
workTable.Rows.Add(workRow);  
  
workRow.BeginEdit();  
// Causes the ColumnChanged event to write a message and cancel the edit.  
workRow[0] = "";       
workRow.EndEdit();  
  
// Displays "Smith, New".  
Console.WriteLine("{0}, {1}", workRow[0], workRow.RowState);    
  
protected static void OnColumnChanged(  
  Object sender, DataColumnChangeEventArgs args)  
{  
  if (args.Column.ColumnName == "LastName")  
    if (args.ProposedValue.ToString() == "")  
    {  
      Console.WriteLine("Last Name cannot be blank. Edit canceled.");  
      args.Row.CancelEdit();  
    }  
}  
```  
  
## 請參閱  
 <xref:System.Data.DataRow>   
 <xref:System.Data.DataTable>   
 <xref:System.Data.DataRowVersion>   
 [管理 DataTable 中的資料](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)   
 [處理 DataTable 事件](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)