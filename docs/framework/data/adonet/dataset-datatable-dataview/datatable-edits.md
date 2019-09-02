---
title: DataTable 編輯
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f08008a9-042e-4de9-94f3-4f0e502b1eb5
ms.openlocfilehash: a970ebda76f5bb6bdea704dabef2ee305436c613
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205010"
---
# <a name="datatable-edits"></a><span data-ttu-id="83bb7-102">DataTable 編輯</span><span class="sxs-lookup"><span data-stu-id="83bb7-102">DataTable Edits</span></span>
<span data-ttu-id="83bb7-103">變更 <xref:System.Data.DataRow> 中的資料行值時，這些變更會立即放入資料列的目前狀態中。</span><span class="sxs-lookup"><span data-stu-id="83bb7-103">When you make changes to column values in a <xref:System.Data.DataRow>, the changes are immediately placed in the current state of the row.</span></span> <span data-ttu-id="83bb7-104"><xref:System.Data.DataRow.AcceptChanges%2A> <xref:System.Data.DataRow.RejectChanges%2A>接著會將設定為 Modified, 並使用 DataRow 的或方法來接受或拒絕變更。 <xref:System.Data.DataRowState></span><span class="sxs-lookup"><span data-stu-id="83bb7-104">The <xref:System.Data.DataRowState> is then set to **Modified**, and the changes are accepted or rejected using the <xref:System.Data.DataRow.AcceptChanges%2A> or <xref:System.Data.DataRow.RejectChanges%2A> methods of the **DataRow**.</span></span> <span data-ttu-id="83bb7-105">**DataRow**也提供三種方法, 可讓您在編輯資料列時, 用來暫停該資料列的狀態。</span><span class="sxs-lookup"><span data-stu-id="83bb7-105">The **DataRow** also provides three methods that you can use to suspend the state of the row while you are editing it.</span></span> <span data-ttu-id="83bb7-106">這些方法是 <xref:System.Data.DataRow.BeginEdit%2A>、<xref:System.Data.DataRow.EndEdit%2A> 和 <xref:System.Data.DataRow.CancelEdit%2A>。</span><span class="sxs-lookup"><span data-stu-id="83bb7-106">These methods are <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>, and <xref:System.Data.DataRow.CancelEdit%2A>.</span></span>  
  
 <span data-ttu-id="83bb7-107">當您直接修改**datarow**中的資料行值時, **Datarow**會使用**目前**的、**預設值**和**原始**資料列版本來管理資料行值。</span><span class="sxs-lookup"><span data-stu-id="83bb7-107">When you modify column values in a **DataRow** directly, the **DataRow** manages the column values using the **Current**, **Default**, and **Original** row versions.</span></span> <span data-ttu-id="83bb7-108">除了這些資料列版本以外, **BeginEdit**、 **EndEdit**和**CancelEdit**方法還使用第四個數據列版本:**提議**。</span><span class="sxs-lookup"><span data-stu-id="83bb7-108">In addition to these row versions, the **BeginEdit**, **EndEdit**, and **CancelEdit** methods use a fourth row version: **Proposed**.</span></span> <span data-ttu-id="83bb7-109">如需資料列版本的詳細資訊, 請參閱資料[列狀態和資料列版本](row-states-and-row-versions.md)。</span><span class="sxs-lookup"><span data-stu-id="83bb7-109">For more information about row versions, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="83bb7-110">**建議**的資料列版本存在於編輯作業期間, 此作業一開始會呼叫**BeginEdit** , 並使用**EndEdit**或**CancelEdit,** 或藉由呼叫**AcceptChanges**或**RejectChanges**來結束。</span><span class="sxs-lookup"><span data-stu-id="83bb7-110">The **Proposed** row version exists during an edit operation that begins by calling **BeginEdit** and that ends either by using **EndEdit** or **CancelEdit,** or by calling **AcceptChanges** or **RejectChanges**.</span></span>  
  
 <span data-ttu-id="83bb7-111">在編輯作業期間, 您可以藉由評估**DataTable** **ColumnChanged**事件中的**ProposedValue** , 將驗證邏輯套用至個別資料行。</span><span class="sxs-lookup"><span data-stu-id="83bb7-111">During the edit operation, you can apply validation logic to individual columns by evaluating the **ProposedValue** in the **ColumnChanged** event of the **DataTable**.</span></span> <span data-ttu-id="83bb7-112">**ColumnChanged**事件會保存**DataColumnChangeEventArgs** , 以保留對變更的資料行及其對**ProposedValue**的參考。</span><span class="sxs-lookup"><span data-stu-id="83bb7-112">The **ColumnChanged** event holds **DataColumnChangeEventArgs** that keep a reference to the column that is changing and to the **ProposedValue**.</span></span> <span data-ttu-id="83bb7-113">在您評估建議的值之後，就可以修改該值或取消編輯。</span><span class="sxs-lookup"><span data-stu-id="83bb7-113">After you evaluate the proposed value, you can either modify it or cancel the edit.</span></span> <span data-ttu-id="83bb7-114">當編輯結束時, 資料列就會移出所**提議**的狀態。</span><span class="sxs-lookup"><span data-stu-id="83bb7-114">When the edit is ended, the row moves out of the **Proposed** state.</span></span>  
  
 <span data-ttu-id="83bb7-115">您可以藉由呼叫**EndEdit**來確認編輯, 或者可以藉由呼叫**CancelEdit**來取消。</span><span class="sxs-lookup"><span data-stu-id="83bb7-115">You can confirm edits by calling **EndEdit**, or you can cancel them by calling **CancelEdit**.</span></span> <span data-ttu-id="83bb7-116">請注意, 雖然**EndEdit**會確認您的編輯, 但在呼叫**AcceptChanges**之前,**資料集**實際上並不接受變更。</span><span class="sxs-lookup"><span data-stu-id="83bb7-116">Note that while **EndEdit** does confirm your edits, the **DataSet** does not actually accept the changes until **AcceptChanges** is called.</span></span> <span data-ttu-id="83bb7-117">另請注意, 如果您在結束 edit with **EndEdit**或**CancelEdit**之前呼叫**AcceptChanges** , 就會結束編輯, 而且**目前**和**原始**資料列版本都會接受**建議**的資料列值。</span><span class="sxs-lookup"><span data-stu-id="83bb7-117">Note also that if you call **AcceptChanges** before you have ended the edit with **EndEdit** or **CancelEdit**, the edit is ended and the **Proposed** row values are accepted for both the **Current** and **Original** row versions.</span></span> <span data-ttu-id="83bb7-118">以同樣的方式, 呼叫**RejectChanges**會結束編輯, 並捨棄**目前**和**建議**的資料列版本。</span><span class="sxs-lookup"><span data-stu-id="83bb7-118">In the same manner, calling **RejectChanges** ends the edit and discards the **Current** and **Proposed** row versions.</span></span> <span data-ttu-id="83bb7-119">呼叫**AcceptChanges**或**RejectChanges**之後呼叫**EndEdit**或**CancelEdit**沒有作用, 因為編輯已經結束。</span><span class="sxs-lookup"><span data-stu-id="83bb7-119">Calling **EndEdit** or **CancelEdit** after calling **AcceptChanges** or **RejectChanges** has no effect because the edit has already ended.</span></span>  
  
 <span data-ttu-id="83bb7-120">下列範例示範如何使用**BeginEdit**搭配**EndEdit**和**CancelEdit**。</span><span class="sxs-lookup"><span data-stu-id="83bb7-120">The following example demonstrates how to use **BeginEdit** with **EndEdit** and **CancelEdit**.</span></span> <span data-ttu-id="83bb7-121">此範例也會檢查**ColumnChanged**事件中的**ProposedValue** , 並決定是否要取消編輯。</span><span class="sxs-lookup"><span data-stu-id="83bb7-121">The example also checks the **ProposedValue** in the **ColumnChanged** event and decides whether to cancel the edit.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="83bb7-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83bb7-122">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataRowVersion>
- [<span data-ttu-id="83bb7-123">在 DataTable 中操作資料</span><span class="sxs-lookup"><span data-stu-id="83bb7-123">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="83bb7-124">處理 DataTable 事件</span><span class="sxs-lookup"><span data-stu-id="83bb7-124">Handling DataTable Events</span></span>](handling-datatable-events.md)
- [<span data-ttu-id="83bb7-125">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="83bb7-125">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
