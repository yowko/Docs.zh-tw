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
# <a name="datatable-edits"></a><span data-ttu-id="bb8d4-102">DataTable 編輯</span><span class="sxs-lookup"><span data-stu-id="bb8d4-102">DataTable Edits</span></span>
<span data-ttu-id="bb8d4-103">變更 <xref:System.Data.DataRow> 中的資料行值時，這些變更會立即放入資料列的目前狀態中。</span><span class="sxs-lookup"><span data-stu-id="bb8d4-103">When you make changes to column values in a <xref:System.Data.DataRow>, the changes are immediately placed in the current state of the row.</span></span> <span data-ttu-id="bb8d4-104">然後<xref:System.Data.DataRowState>設置為 **"已修改 "，** 並使用<xref:System.Data.DataRow.AcceptChanges%2A>**DataRow**的 或<xref:System.Data.DataRow.RejectChanges%2A>方法接受或拒絕更改。</span><span class="sxs-lookup"><span data-stu-id="bb8d4-104">The <xref:System.Data.DataRowState> is then set to **Modified**, and the changes are accepted or rejected using the <xref:System.Data.DataRow.AcceptChanges%2A> or <xref:System.Data.DataRow.RejectChanges%2A> methods of the **DataRow**.</span></span> <span data-ttu-id="bb8d4-105">**DataRow**還提供三種方法，可用於在編輯行時掛起行的狀態。</span><span class="sxs-lookup"><span data-stu-id="bb8d4-105">The **DataRow** also provides three methods that you can use to suspend the state of the row while you are editing it.</span></span> <span data-ttu-id="bb8d4-106">這些方法是 <xref:System.Data.DataRow.BeginEdit%2A>、<xref:System.Data.DataRow.EndEdit%2A> 和 <xref:System.Data.DataRow.CancelEdit%2A>。</span><span class="sxs-lookup"><span data-stu-id="bb8d4-106">These methods are <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>, and <xref:System.Data.DataRow.CancelEdit%2A>.</span></span>  
  
 <span data-ttu-id="bb8d4-107">直接修改**DataRow**中的列值時 **，DataRow**將使用 **"當前**"、"**預設**"和 **"原始**行"版本管理列值。</span><span class="sxs-lookup"><span data-stu-id="bb8d4-107">When you modify column values in a **DataRow** directly, the **DataRow** manages the column values using the **Current**, **Default**, and **Original** row versions.</span></span> <span data-ttu-id="bb8d4-108">除了這些行版本外，"**開始編輯**"、"**結束編輯\*\*\*\*"和"取消編輯"** 方法使用第四行版本：**建議**。</span><span class="sxs-lookup"><span data-stu-id="bb8d4-108">In addition to these row versions, the **BeginEdit**, **EndEdit**, and **CancelEdit** methods use a fourth row version: **Proposed**.</span></span> <span data-ttu-id="bb8d4-109">有關行版本的詳細資訊，請參閱[行狀態和行版本](row-states-and-row-versions.md)。</span><span class="sxs-lookup"><span data-stu-id="bb8d4-109">For more information about row versions, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="bb8d4-110">**建議的**行版本存在於編輯操作中，該操作以調用**BeginEdit**開始，最後使用 **"結束編輯"** 或 **"取消編輯"，** 或調用 **"接受更改**"或 **"拒絕更改**"。</span><span class="sxs-lookup"><span data-stu-id="bb8d4-110">The **Proposed** row version exists during an edit operation that begins by calling **BeginEdit** and that ends either by using **EndEdit** or **CancelEdit,** or by calling **AcceptChanges** or **RejectChanges**.</span></span>  
  
 <span data-ttu-id="bb8d4-111">在編輯操作期間，您可以通過在**DataTable**的**列更改**事件中評估 **"建議值**"來將驗證邏輯應用於各個列。</span><span class="sxs-lookup"><span data-stu-id="bb8d4-111">During the edit operation, you can apply validation logic to individual columns by evaluating the **ProposedValue** in the **ColumnChanged** event of the **DataTable**.</span></span> <span data-ttu-id="bb8d4-112">**"列更改"** 事件保存**DataColumnChangeEventArgs，該事件**保留對正在更改的列和**建議值**的引用。</span><span class="sxs-lookup"><span data-stu-id="bb8d4-112">The **ColumnChanged** event holds **DataColumnChangeEventArgs** that keep a reference to the column that is changing and to the **ProposedValue**.</span></span> <span data-ttu-id="bb8d4-113">在您評估建議的值之後，就可以修改該值或取消編輯。</span><span class="sxs-lookup"><span data-stu-id="bb8d4-113">After you evaluate the proposed value, you can either modify it or cancel the edit.</span></span> <span data-ttu-id="bb8d4-114">編輯結束時，行將移出 **"建議"** 狀態。</span><span class="sxs-lookup"><span data-stu-id="bb8d4-114">When the edit is ended, the row moves out of the **Proposed** state.</span></span>  
  
 <span data-ttu-id="bb8d4-115">您可以通過調用**EndEdit**來確認編輯，也可以通過調用**CancelEdit**來取消編輯。</span><span class="sxs-lookup"><span data-stu-id="bb8d4-115">You can confirm edits by calling **EndEdit**, or you can cancel them by calling **CancelEdit**.</span></span> <span data-ttu-id="bb8d4-116">請注意，雖然**EndEdit**確實確認您的編輯，但**DataSet**在調用 **"接受更改**"之前實際上不會接受更改。</span><span class="sxs-lookup"><span data-stu-id="bb8d4-116">Note that while **EndEdit** does confirm your edits, the **DataSet** does not actually accept the changes until **AcceptChanges** is called.</span></span> <span data-ttu-id="bb8d4-117">另請注意，如果在結束編輯或**取消編輯**之前調用 **"接受更改**"，則編輯將結束，**並且"當前**"行版本和**原始**行版本均接受 **"建議**行"值。 **EndEdit**</span><span class="sxs-lookup"><span data-stu-id="bb8d4-117">Note also that if you call **AcceptChanges** before you have ended the edit with **EndEdit** or **CancelEdit**, the edit is ended and the **Proposed** row values are accepted for both the **Current** and **Original** row versions.</span></span> <span data-ttu-id="bb8d4-118">以同樣的方式，調用**拒絕更改**結束編輯並丟棄**當前**和**建議的**行版本。</span><span class="sxs-lookup"><span data-stu-id="bb8d4-118">In the same manner, calling **RejectChanges** ends the edit and discards the **Current** and **Proposed** row versions.</span></span> <span data-ttu-id="bb8d4-119">調用"**接受更改**"或 **"拒絕更改**"後調用 **"結束編輯**"或 **"取消編輯"** 不起作用，因為編輯已結束。</span><span class="sxs-lookup"><span data-stu-id="bb8d4-119">Calling **EndEdit** or **CancelEdit** after calling **AcceptChanges** or **RejectChanges** has no effect because the edit has already ended.</span></span>  
  
 <span data-ttu-id="bb8d4-120">下面的示例演示如何使用 **"開始編輯**"與**結束編輯**和**取消編輯**。</span><span class="sxs-lookup"><span data-stu-id="bb8d4-120">The following example demonstrates how to use **BeginEdit** with **EndEdit** and **CancelEdit**.</span></span> <span data-ttu-id="bb8d4-121">該示例還檢查 **"列更改"** 事件中**的"建議值**"，並決定是否取消編輯。</span><span class="sxs-lookup"><span data-stu-id="bb8d4-121">The example also checks the **ProposedValue** in the **ColumnChanged** event and decides whether to cancel the edit.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bb8d4-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb8d4-122">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataRowVersion>
- [<span data-ttu-id="bb8d4-123">在 DataTable 中操作資料</span><span class="sxs-lookup"><span data-stu-id="bb8d4-123">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="bb8d4-124">處理 DataTable 事件</span><span class="sxs-lookup"><span data-stu-id="bb8d4-124">Handling DataTable Events</span></span>](handling-datatable-events.md)
- <span data-ttu-id="bb8d4-125">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="bb8d4-125">[ADO.NET Overview](../ado-net-overview.md)</span></span>
