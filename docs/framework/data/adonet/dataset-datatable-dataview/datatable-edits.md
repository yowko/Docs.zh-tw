---
title: DataTable 編輯
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f08008a9-042e-4de9-94f3-4f0e502b1eb5
ms.openlocfilehash: 1d9321a1db4f68195fb914f271fb98f904d2f963
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43805802"
---
# <a name="datatable-edits"></a>DataTable 編輯
變更 <xref:System.Data.DataRow> 中的資料行值時，這些變更會立即放入資料列的目前狀態中。 <xref:System.Data.DataRowState>會設為**Modified**，以及所做的變更來接受或拒絕使用<xref:System.Data.DataRow.AcceptChanges%2A>或<xref:System.Data.DataRow.RejectChanges%2A>方法**DataRow**。 **DataRow**也會提供三種方法，您可以使用您在編輯時，暫停的資料列狀態。 這些方法是 <xref:System.Data.DataRow.BeginEdit%2A>、<xref:System.Data.DataRow.EndEdit%2A> 和 <xref:System.Data.DataRow.CancelEdit%2A>。  
  
 當您修改資料行中的值**DataRow**直接**DataRow**會管理使用的資料行值**目前**，**預設**，及**原始**資料列版本。 這些資料列版本，除了**BeginEdit**， **EndEdit**，並**CancelEdit**方法會使用第四個資料列版本：**提議**。 如需有關資料列版本的詳細資訊，請參閱[資料列狀態和資料列版本](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)。  
  
 **提議**編輯作業一開始會先呼叫期間的資料列版本存在**BeginEdit** ，且結束利用**EndEdit**或**CancelEdit**或藉由呼叫**AcceptChanges**或是**RejectChanges**。  
  
 編輯作業期間，您可以將驗證邏輯套用至個別資料行藉由評估**ProposedValue**中**ColumnChanged**事件**DataTable**。 **ColumnChanged**事件會保存**DataColumnChangeEventArgs**正在變更的資料行，並保留參考**ProposedValue**。 在您評估建議的值之後，就可以修改該值或取消編輯。 當編輯作業結束後時，資料列會移出**提議**狀態。  
  
 您可以藉由呼叫確認編輯**EndEdit**，或您可以藉由呼叫取消**CancelEdit**。 請注意，雖然**EndEdit**確認您的編輯**資料集**真正接受變更，直到**AcceptChanges**呼叫。 也請注意，如果您呼叫**AcceptChanges**已經結束編輯之前**EndEdit**或是**CancelEdit**，編輯作業會結束和**提議**同時接受的資料列值**目前**並**原始**資料列版本。 同樣地，在呼叫**RejectChanges**結束編輯，並捨棄**目前**並**提議**資料列版本。 呼叫**EndEdit**或是**CancelEdit**之後呼叫**AcceptChanges**或是**RejectChanges**沒有任何作用，因為編輯作業已完成已結束。  
  
 下列範例示範如何使用**BeginEdit**具有**EndEdit**並**CancelEdit**。 此範例也會檢查**ProposedValue**中**ColumnChanged**事件，並決定是否要取消編輯。  
  
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
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataRowVersion>  
 [在 DataTable 中操作資料](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [處理 DataTable 事件](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
