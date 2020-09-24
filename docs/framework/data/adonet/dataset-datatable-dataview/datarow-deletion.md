---
title: 刪除 DataRow
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34f531d-4b9b-4071-b2d7-342c402aa586
ms.openlocfilehash: 2092d7319a398bbdeaef764d677818f78ddf9de9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153348"
---
# <a name="datarow-deletion"></a><span data-ttu-id="ade88-102">刪除 DataRow</span><span class="sxs-lookup"><span data-stu-id="ade88-102">DataRow Deletion</span></span>

<span data-ttu-id="ade88-103">您可以使用兩種方法 <xref:System.Data.DataRow> 從物件刪除物件 <xref:System.Data.DataTable> ：物件的 **Remove** 方法 <xref:System.Data.DataRowCollection> ，以及 <xref:System.Data.DataRow.Delete%2A> **DataRow** 物件的方法。</span><span class="sxs-lookup"><span data-stu-id="ade88-103">There are two methods you can use to delete a <xref:System.Data.DataRow> object from a <xref:System.Data.DataTable> object: the **Remove** method of the <xref:System.Data.DataRowCollection> object, and the <xref:System.Data.DataRow.Delete%2A> method of the **DataRow** object.</span></span> <span data-ttu-id="ade88-104">方法會 <xref:System.Data.DataRowCollection.Remove%2A> 從**DataRowCollection**中刪除**DataRow** ，但是此 <xref:System.Data.DataRow.Delete%2A> 方法只會標示要刪除的資料列。</span><span class="sxs-lookup"><span data-stu-id="ade88-104">Whereas the <xref:System.Data.DataRowCollection.Remove%2A> method deletes a **DataRow** from the **DataRowCollection**, the <xref:System.Data.DataRow.Delete%2A> method only marks the row for deletion.</span></span> <span data-ttu-id="ade88-105">當應用程式呼叫 **AcceptChanges** 方法時，就會發生實際的移除動作。</span><span class="sxs-lookup"><span data-stu-id="ade88-105">The actual removal occurs when the application calls the **AcceptChanges** method.</span></span> <span data-ttu-id="ade88-106">您可以使用 <xref:System.Data.DataRow.Delete%2A>，以程式設計方式檢查有哪些資料列標示為要刪除，然後再將其實際移除。</span><span class="sxs-lookup"><span data-stu-id="ade88-106">By using <xref:System.Data.DataRow.Delete%2A>, you can programmatically check which rows are marked for deletion before actually removing them.</span></span> <span data-ttu-id="ade88-107">將資料列標記為要刪除時，會將其 <xref:System.Data.DataRow.RowState%2A> 屬性設為 <xref:System.Data.DataRow.Delete%2A>。</span><span class="sxs-lookup"><span data-stu-id="ade88-107">When a row is marked for deletion, its <xref:System.Data.DataRow.RowState%2A> property is set to <xref:System.Data.DataRow.Delete%2A>.</span></span>  
  
 <span data-ttu-id="ade88-108">在 foreach 迴圈中不應呼叫 <xref:System.Data.DataRow.Delete%2A> 和 <xref:System.Data.DataRowCollection.Remove%2A>，而應逐一查看 <xref:System.Data.DataRowCollection> 物件。</span><span class="sxs-lookup"><span data-stu-id="ade88-108">Neither <xref:System.Data.DataRow.Delete%2A> nor <xref:System.Data.DataRowCollection.Remove%2A> should be called in a foreach loop while iterating through a <xref:System.Data.DataRowCollection> object.</span></span> <span data-ttu-id="ade88-109"><xref:System.Data.DataRow.Delete%2A> 和 <xref:System.Data.DataRowCollection.Remove%2A> 都不會修改集合的狀態。</span><span class="sxs-lookup"><span data-stu-id="ade88-109"><xref:System.Data.DataRow.Delete%2A> nor <xref:System.Data.DataRowCollection.Remove%2A> modify the state of the collection.</span></span>  
  
 <span data-ttu-id="ade88-110">使用 <xref:System.Data.DataSet> 或**DataTable**搭配**DataAdapter**和關聯式資料來源時，請使用**DataRow**的**Delete**方法來移除資料列。</span><span class="sxs-lookup"><span data-stu-id="ade88-110">When using a <xref:System.Data.DataSet> or **DataTable** in conjunction with a **DataAdapter** and a relational data source, use the **Delete** method of the **DataRow** to remove the row.</span></span> <span data-ttu-id="ade88-111">**Delete**方法會將資料列標示為**已刪除**的**資料集**或**DataTable** ，但不會將它移除。</span><span class="sxs-lookup"><span data-stu-id="ade88-111">The **Delete** method marks the row as **Deleted** in the **DataSet** or **DataTable** but does not remove it.</span></span> <span data-ttu-id="ade88-112">相反地，當 **DataAdapter** 遇到標示為 **Deleted**的資料列時，它會執行其 **DeleteCommand** 方法來刪除資料來源中的資料列。</span><span class="sxs-lookup"><span data-stu-id="ade88-112">Instead, when the **DataAdapter** encounters a row marked as **Deleted**, it executes its **DeleteCommand** method to delete the row at the data source.</span></span> <span data-ttu-id="ade88-113">然後，您可以使用 **AcceptChanges** 方法永久移除該資料列。</span><span class="sxs-lookup"><span data-stu-id="ade88-113">The row can then be permanently removed using the **AcceptChanges** method.</span></span> <span data-ttu-id="ade88-114">如果您使用 [ **移除** ] 來刪除資料列，則會從資料表中移除資料列，但 **DataAdapter** 不會刪除資料來源中的資料列。</span><span class="sxs-lookup"><span data-stu-id="ade88-114">If you use **Remove** to delete the row, the row is removed entirely from the table, but the **DataAdapter** will not delete the row at the data source.</span></span>  
  
 <span data-ttu-id="ade88-115">**DataRowCollection**的**Remove**方法會將**DataRow**視為引數，並將它從集合中移除，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="ade88-115">The **Remove** method of the **DataRowCollection** takes a **DataRow** as an argument and removes it from the collection, as shown in the following example.</span></span>  
  
```vb  
workTable.Rows.Remove(workRow)  
```  
  
```csharp  
workTable.Rows.Remove(workRow);  
```  
  
 <span data-ttu-id="ade88-116">相反地，下列範例示範如何在**DataRow**上呼叫**Delete**方法，以將其**RowState**變更為**Deleted**。</span><span class="sxs-lookup"><span data-stu-id="ade88-116">In contrast, the following example demonstrates how to call the **Delete** method on a **DataRow** to change its **RowState** to **Deleted**.</span></span>  
  
```vb  
workRow.Delete  
```  
  
```csharp  
workRow.Delete();  
```  
  
 <span data-ttu-id="ade88-117">如果資料列標示為刪除，而且您呼叫**datatable**物件的**AcceptChanges**方法，就會從**datatable**中移除該資料列。</span><span class="sxs-lookup"><span data-stu-id="ade88-117">If a row is marked for deletion and you call the **AcceptChanges** method of the **DataTable** object, the row is removed from the **DataTable**.</span></span> <span data-ttu-id="ade88-118">相反地，如果您呼叫 **RejectChanges**，資料列的 **RowState** 會還原為標示為 **已刪除**之前的內容。</span><span class="sxs-lookup"><span data-stu-id="ade88-118">In contrast, if you call **RejectChanges**, the **RowState** of the row reverts to what it was before being marked as **Deleted**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ade88-119">如果**加入** **DataRow**的**RowState** ，表示它剛加入資料表中，然後標示為**已刪除**，則會從資料表中移除它。</span><span class="sxs-lookup"><span data-stu-id="ade88-119">If the **RowState** of a **DataRow** is **Added**, meaning it has just been added to the table, and it is then marked as **Deleted**, it is removed from the table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ade88-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ade88-120">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="ade88-121">在 DataTable 中操作資料</span><span class="sxs-lookup"><span data-stu-id="ade88-121">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- <span data-ttu-id="ade88-122">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="ade88-122">[ADO.NET Overview](../ado-net-overview.md)</span></span>
