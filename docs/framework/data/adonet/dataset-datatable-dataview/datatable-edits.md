---
title: DataTable 編輯
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f08008a9-042e-4de9-94f3-4f0e502b1eb5
ms.openlocfilehash: 9e8c4204b51121b147fc7614066d9b849a687574
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151256"
---
# <a name="datatable-edits"></a>DataTable 編輯
變更 <xref:System.Data.DataRow> 中的資料行值時，這些變更會立即放入資料列的目前狀態中。 然後<xref:System.Data.DataRowState>設置為 **"已修改 "，** 並使用<xref:System.Data.DataRow.AcceptChanges%2A>**DataRow**的 或<xref:System.Data.DataRow.RejectChanges%2A>方法接受或拒絕更改。 **DataRow**還提供三種方法，可用於在編輯行時掛起行的狀態。 這些方法是 <xref:System.Data.DataRow.BeginEdit%2A>、<xref:System.Data.DataRow.EndEdit%2A> 和 <xref:System.Data.DataRow.CancelEdit%2A>。  
  
 直接修改**DataRow**中的列值時 **，DataRow**將使用 **"當前**"、"**預設**"和 **"原始**行"版本管理列值。 除了這些行版本外，"**開始編輯**"、"**結束編輯****"和"取消編輯"** 方法使用第四行版本：**建議**。 有關行版本的詳細資訊，請參閱[行狀態和行版本](row-states-and-row-versions.md)。  
  
 **建議的**行版本存在於編輯操作中，該操作以調用**BeginEdit**開始，最後使用 **"結束編輯"** 或 **"取消編輯"，** 或調用 **"接受更改**"或 **"拒絕更改**"。  
  
 在編輯操作期間，您可以通過在**DataTable**的**列更改**事件中評估 **"建議值**"來將驗證邏輯應用於各個列。 **"列更改"** 事件保存**DataColumnChangeEventArgs，該事件**保留對正在更改的列和**建議值**的引用。 在您評估建議的值之後，就可以修改該值或取消編輯。 編輯結束時，行將移出 **"建議"** 狀態。  
  
 您可以通過調用**EndEdit**來確認編輯，也可以通過調用**CancelEdit**來取消編輯。 請注意，雖然**EndEdit**確實確認您的編輯，但**DataSet**在調用 **"接受更改**"之前實際上不會接受更改。 另請注意，如果在結束編輯或**取消編輯**之前調用 **"接受更改**"，則編輯將結束，**並且"當前**"行版本和**原始**行版本均接受 **"建議**行"值。 **EndEdit** 以同樣的方式，調用**拒絕更改**結束編輯並丟棄**當前**和**建議的**行版本。 調用"**接受更改**"或 **"拒絕更改**"後調用 **"結束編輯**"或 **"取消編輯"** 不起作用，因為編輯已結束。  
  
 下面的示例演示如何使用 **"開始編輯**"與**結束編輯**和**取消編輯**。 該示例還檢查 **"列更改"** 事件中**的"建議值**"，並決定是否取消編輯。  
  
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
- [處理 DataTable 事件](handling-datatable-events.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
