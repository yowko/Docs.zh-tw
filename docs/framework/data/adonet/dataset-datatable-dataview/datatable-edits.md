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
ms.openlocfilehash: d33bd8900c48222142a46ed2c5bd64412d2eaab5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="datatable-edits"></a><span data-ttu-id="f1713-102">DataTable 編輯</span><span class="sxs-lookup"><span data-stu-id="f1713-102">DataTable Edits</span></span>
<span data-ttu-id="f1713-103">變更 <xref:System.Data.DataRow> 中的資料行值時，這些變更會立即放入資料列的目前狀態中。</span><span class="sxs-lookup"><span data-stu-id="f1713-103">When you make changes to column values in a <xref:System.Data.DataRow>, the changes are immediately placed in the current state of the row.</span></span> <span data-ttu-id="f1713-104"><xref:System.Data.DataRowState>會接著設為**Modified**，以及所做的變更會接受或拒絕使用<xref:System.Data.DataRow.AcceptChanges%2A>或<xref:System.Data.DataRow.RejectChanges%2A>方法**DataRow**。</span><span class="sxs-lookup"><span data-stu-id="f1713-104">The <xref:System.Data.DataRowState> is then set to **Modified**, and the changes are accepted or rejected using the <xref:System.Data.DataRow.AcceptChanges%2A> or <xref:System.Data.DataRow.RejectChanges%2A> methods of the **DataRow**.</span></span> <span data-ttu-id="f1713-105">**DataRow**也會提供三種方法可讓您在編輯時，暫止的資料列狀態。</span><span class="sxs-lookup"><span data-stu-id="f1713-105">The **DataRow** also provides three methods that you can use to suspend the state of the row while you are editing it.</span></span> <span data-ttu-id="f1713-106">這些方法是 <xref:System.Data.DataRow.BeginEdit%2A>、<xref:System.Data.DataRow.EndEdit%2A> 和 <xref:System.Data.DataRow.CancelEdit%2A>。</span><span class="sxs-lookup"><span data-stu-id="f1713-106">These methods are <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>, and <xref:System.Data.DataRow.CancelEdit%2A>.</span></span>  
  
 <span data-ttu-id="f1713-107">當您修改的資料行值**DataRow**直接**DataRow**管理使用的資料行值**目前**，**預設**，和**原始**資料列版本。</span><span class="sxs-lookup"><span data-stu-id="f1713-107">When you modify column values in a **DataRow** directly, the **DataRow** manages the column values using the **Current**, **Default**, and **Original** row versions.</span></span> <span data-ttu-id="f1713-108">這些資料列版本，除了**BeginEdit**， **EndEdit**，和**CancelEdit**方法會使用第四個資料列版本： **Proposed**。</span><span class="sxs-lookup"><span data-stu-id="f1713-108">In addition to these row versions, the **BeginEdit**, **EndEdit**, and **CancelEdit** methods use a fourth row version: **Proposed**.</span></span> <span data-ttu-id="f1713-109">如需詳細資料列版本的詳細資訊，請參閱[資料列狀態和資料列版本](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)。</span><span class="sxs-lookup"><span data-stu-id="f1713-109">For more information about row versions, see [Row States and Row Versions](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="f1713-110">**Proposed**開始所呼叫的編輯作業期間的資料列版本存在**BeginEdit**及結束使用**EndEdit**或**CancelEdit**或藉由呼叫**AcceptChanges**或**RejectChanges**。</span><span class="sxs-lookup"><span data-stu-id="f1713-110">The **Proposed** row version exists during an edit operation that begins by calling **BeginEdit** and that ends either by using **EndEdit** or **CancelEdit,** or by calling **AcceptChanges** or **RejectChanges**.</span></span>  
  
 <span data-ttu-id="f1713-111">編輯作業期間，您可以將驗證邏輯套用至個別資料行藉由評估**Datatable**中**ColumnChanged**事件**DataTable**。</span><span class="sxs-lookup"><span data-stu-id="f1713-111">During the edit operation, you can apply validation logic to individual columns by evaluating the **ProposedValue** in the **ColumnChanged** event of the **DataTable**.</span></span> <span data-ttu-id="f1713-112">**ColumnChanged**事件含有**DataColumnChangeEventArgs**所保留的參考，正在變更的資料行以及**Datatable**。</span><span class="sxs-lookup"><span data-stu-id="f1713-112">The **ColumnChanged** event holds **DataColumnChangeEventArgs** that keep a reference to the column that is changing and to the **ProposedValue**.</span></span> <span data-ttu-id="f1713-113">在您評估建議的值之後，就可以修改該值或取消編輯。</span><span class="sxs-lookup"><span data-stu-id="f1713-113">After you evaluate the proposed value, you can either modify it or cancel the edit.</span></span> <span data-ttu-id="f1713-114">當編輯作業結束後時，資料列移出的**Proposed**狀態。</span><span class="sxs-lookup"><span data-stu-id="f1713-114">When the edit is ended, the row moves out of the **Proposed** state.</span></span>  
  
 <span data-ttu-id="f1713-115">您可以藉由呼叫確認編輯**EndEdit**，或藉由呼叫取消**CancelEdit**。</span><span class="sxs-lookup"><span data-stu-id="f1713-115">You can confirm edits by calling **EndEdit**, or you can cancel them by calling **CancelEdit**.</span></span> <span data-ttu-id="f1713-116">請注意，當**EndEdit**確認您的編輯**資料集**真正接受變更，直到**AcceptChanges**呼叫。</span><span class="sxs-lookup"><span data-stu-id="f1713-116">Note that while **EndEdit** does confirm your edits, the **DataSet** does not actually accept the changes until **AcceptChanges** is called.</span></span> <span data-ttu-id="f1713-117">另請注意，如果您呼叫**AcceptChanges**您已經結束編輯之前**EndEdit**或**CancelEdit**，編輯作業會結束而**Proposed**接受兩個資料列值**目前**和**原始**資料列版本。</span><span class="sxs-lookup"><span data-stu-id="f1713-117">Note also that if you call **AcceptChanges** before you have ended the edit with **EndEdit** or **CancelEdit**, the edit is ended and the **Proposed** row values are accepted for both the **Current** and **Original** row versions.</span></span> <span data-ttu-id="f1713-118">同樣地，在呼叫**RejectChanges**結束編輯並捨棄**目前**和**Proposed**資料列版本。</span><span class="sxs-lookup"><span data-stu-id="f1713-118">In the same manner, calling **RejectChanges** ends the edit and discards the **Current** and **Proposed** row versions.</span></span> <span data-ttu-id="f1713-119">呼叫**EndEdit**或**CancelEdit**之後呼叫**AcceptChanges**或**RejectChanges**沒有任何作用，因為編輯作業已完成結束。</span><span class="sxs-lookup"><span data-stu-id="f1713-119">Calling **EndEdit** or **CancelEdit** after calling **AcceptChanges** or **RejectChanges** has no effect because the edit has already ended.</span></span>  
  
 <span data-ttu-id="f1713-120">下列範例示範如何使用**BeginEdit**與**EndEdit**和**CancelEdit**。</span><span class="sxs-lookup"><span data-stu-id="f1713-120">The following example demonstrates how to use **BeginEdit** with **EndEdit** and **CancelEdit**.</span></span> <span data-ttu-id="f1713-121">此範例也會檢查**Datatable**中**ColumnChanged**事件，並決定是否要取消編輯。</span><span class="sxs-lookup"><span data-stu-id="f1713-121">The example also checks the **ProposedValue** in the **ColumnChanged** event and decides whether to cancel the edit.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f1713-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1713-122">See Also</span></span>  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataRowVersion>  
 [<span data-ttu-id="f1713-123">在 DataTable 中操作資料</span><span class="sxs-lookup"><span data-stu-id="f1713-123">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="f1713-124">處理 DataTable 的事件</span><span class="sxs-lookup"><span data-stu-id="f1713-124">Handling DataTable Events</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 [<span data-ttu-id="f1713-125">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="f1713-125">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
