---
title: "DataTable 編輯"
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
ms.assetid: f08008a9-042e-4de9-94f3-4f0e502b1eb5
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3d06fc3a82457972db94f82964942f446bb761be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="datatable-edits"></a>DataTable 編輯
變更 <xref:System.Data.DataRow> 中的資料行值時，這些變更會立即放入資料列的目前狀態中。 <xref:System.Data.DataRowState>會接著設為**Modified**，以及所做的變更會接受或拒絕使用<xref:System.Data.DataRow.AcceptChanges%2A>或<xref:System.Data.DataRow.RejectChanges%2A>方法**DataRow**。 **DataRow**也會提供三種方法可讓您在編輯時，暫止的資料列狀態。 這些方法是 <xref:System.Data.DataRow.BeginEdit%2A>、<xref:System.Data.DataRow.EndEdit%2A> 和 <xref:System.Data.DataRow.CancelEdit%2A>。  
  
 當您修改的資料行值**DataRow**直接**DataRow**管理使用的資料行值**目前**，**預設**，和**原始**資料列版本。 這些資料列版本，除了**BeginEdit**， **EndEdit**，和**CancelEdit**方法會使用第四個資料列版本： **Proposed**。 如需詳細資料列版本的詳細資訊，請參閱[資料列狀態和資料列版本](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)。  
  
 **Proposed**開始所呼叫的編輯作業期間的資料列版本存在**BeginEdit**及結束使用**EndEdit**或**CancelEdit**或藉由呼叫**AcceptChanges**或**RejectChanges**。  
  
 編輯作業期間，您可以將驗證邏輯套用至個別資料行藉由評估**Datatable**中**ColumnChanged**事件**DataTable**。 **ColumnChanged**事件含有**DataColumnChangeEventArgs**所保留的參考，正在變更的資料行以及**Datatable**。 在您評估建議的值之後，就可以修改該值或取消編輯。 當編輯作業結束後時，資料列移出的**Proposed**狀態。  
  
 您可以藉由呼叫確認編輯**EndEdit**，或藉由呼叫取消**CancelEdit**。 請注意，當**EndEdit**確認您的編輯**資料集**真正接受變更，直到**AcceptChanges**呼叫。 另請注意，如果您呼叫**AcceptChanges**您已經結束編輯之前**EndEdit**或**CancelEdit**，編輯作業會結束而**Proposed**接受兩個資料列值**目前**和**原始**資料列版本。 同樣地，在呼叫**RejectChanges**結束編輯並捨棄**目前**和**Proposed**資料列版本。 呼叫**EndEdit**或**CancelEdit**之後呼叫**AcceptChanges**或**RejectChanges**沒有任何作用，因為編輯作業已完成結束。  
  
 下列範例示範如何使用**BeginEdit**與**EndEdit**和**CancelEdit**。 此範例也會檢查**Datatable**中**ColumnChanged**事件，並決定是否要取消編輯。  
  
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
  
## <a name="see-also"></a>請參閱  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataRowVersion>  
 [在 DataTable 中操作資料](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [處理 DataTable 事件](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
