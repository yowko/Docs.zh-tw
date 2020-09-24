---
title: DataTable 編輯
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f08008a9-042e-4de9-94f3-4f0e502b1eb5
ms.openlocfilehash: 4fdb19e7fa014bf4a7c924b1fbae53fa44de6e3c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153257"
---
# <a name="datatable-edits"></a>DataTable 編輯

變更 <xref:System.Data.DataRow> 中的資料行值時，這些變更會立即放入資料列的目前狀態中。 <xref:System.Data.DataRowState>接著會設定為 [**已修改**]，並使用 DataRow 的或方法來接受或拒絕變更 <xref:System.Data.DataRow.AcceptChanges%2A> <xref:System.Data.DataRow.RejectChanges%2A> 。 **DataRow** **DataRow**也提供三種方法，可讓您在編輯資料列時，用來暫止該資料列的狀態。 這些方法是 <xref:System.Data.DataRow.BeginEdit%2A>、<xref:System.Data.DataRow.EndEdit%2A> 和 <xref:System.Data.DataRow.CancelEdit%2A>。  
  
 當您直接修改 **datarow** 中的資料行值時， **Datarow** 會使用 **目前**、 **預設**和 **原始** 資料列版本來管理資料行的值。 除了這些資料列版本以外， **BeginEdit**、 **EndEdit**和 **CancelEdit** 方法還使用第四個數據列版本： **提議**。 如需資料列版本的詳細資訊，請參閱資料 [列狀態和資料列版本](row-states-and-row-versions.md)。  
  
 **建議**的資料列版本存在於從呼叫**BeginEdit**開始的編輯作業期間，或是藉由使用**EndEdit**或**CancelEdit，** 或藉由呼叫**AcceptChanges**或**RejectChanges**來結束。  
  
 在編輯作業期間，您可以藉由評估**DataTable** **ColumnChanged**事件中的**ProposedValue** ，將驗證邏輯套用至個別資料行。 **ColumnChanged**事件會保存**DataColumnChangeEventArgs** ，以保留變更和**ProposedValue**的資料行參考。 在您評估建議的值之後，就可以修改該值或取消編輯。 當編輯結束時，資料列就會移出 **建議** 的狀態。  
  
 您可以藉由呼叫 **EndEdit**來確認編輯，或是藉由呼叫 **CancelEdit**來取消編輯。 請注意，雖然**EndEdit**確實會確認您的編輯，但在呼叫**AcceptChanges**之前，**資料集**不會實際接受變更。 另外也請注意，如果您在結束 [使用**EndEdit**或**CancelEdit**編輯] 之前呼叫**AcceptChanges** ，就會結束編輯，並且針對**目前**和**原始**資料列版本接受**建議**的資料列值。 以同樣的方式，呼叫 **RejectChanges** 會結束編輯並捨棄 **目前** 和 **建議** 的資料列版本。 呼叫**AcceptChanges**或**RejectChanges**之後呼叫**EndEdit**或**CancelEdit**沒有任何作用，因為編輯已經結束。  
  
 下列範例示範如何搭配使用 **BeginEdit** 與 **EndEdit** 和 **CancelEdit**。 此範例也會檢查**ColumnChanged**事件中的**ProposedValue** ，並決定是否要取消編輯。  
  
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

- <xref:System.Data.DataRow>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataRowVersion>
- [在 DataTable 中操作資料](manipulating-data-in-a-datatable.md)
- [處理 DataTable 的事件](handling-datatable-events.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
