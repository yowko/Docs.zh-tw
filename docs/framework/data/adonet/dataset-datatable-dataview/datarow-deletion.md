---
title: 刪除 DataRow
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34f531d-4b9b-4071-b2d7-342c402aa586
ms.openlocfilehash: 7c80294c4bc879e6a1df4c9d1170eef14b8b83de
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915817"
---
# <a name="datarow-deletion"></a><span data-ttu-id="bb9b8-102">刪除 DataRow</span><span class="sxs-lookup"><span data-stu-id="bb9b8-102">DataRow Deletion</span></span>
<span data-ttu-id="bb9b8-103">有兩種方法可用來刪除<xref:System.Data.DataRow> <xref:System.Data.DataTable>物件中的物件: <xref:System.Data.DataRowCollection>物件的**Remove** <xref:System.Data.DataRow.Delete%2A>方法, 以及**DataRow**物件的方法。</span><span class="sxs-lookup"><span data-stu-id="bb9b8-103">There are two methods you can use to delete a <xref:System.Data.DataRow> object from a <xref:System.Data.DataTable> object: the **Remove** method of the <xref:System.Data.DataRowCollection> object, and the <xref:System.Data.DataRow.Delete%2A> method of the **DataRow** object.</span></span> <span data-ttu-id="bb9b8-104">方法會從**DataRowCollection** <xref:System.Data.DataRow.Delete%2A>刪除**DataRow** , 而方法只會標示要刪除的資料列。 <xref:System.Data.DataRowCollection.Remove%2A></span><span class="sxs-lookup"><span data-stu-id="bb9b8-104">Whereas the <xref:System.Data.DataRowCollection.Remove%2A> method deletes a **DataRow** from the **DataRowCollection**, the <xref:System.Data.DataRow.Delete%2A> method only marks the row for deletion.</span></span> <span data-ttu-id="bb9b8-105">當應用程式呼叫**AcceptChanges**方法時, 就會發生實際的移除。</span><span class="sxs-lookup"><span data-stu-id="bb9b8-105">The actual removal occurs when the application calls the **AcceptChanges** method.</span></span> <span data-ttu-id="bb9b8-106">您可以使用 <xref:System.Data.DataRow.Delete%2A>，以程式設計方式檢查有哪些資料列標示為要刪除，然後再將其實際移除。</span><span class="sxs-lookup"><span data-stu-id="bb9b8-106">By using <xref:System.Data.DataRow.Delete%2A>, you can programmatically check which rows are marked for deletion before actually removing them.</span></span> <span data-ttu-id="bb9b8-107">將資料列標記為要刪除時，會將其 <xref:System.Data.DataRow.RowState%2A> 屬性設為 <xref:System.Data.DataRow.Delete%2A>。</span><span class="sxs-lookup"><span data-stu-id="bb9b8-107">When a row is marked for deletion, its <xref:System.Data.DataRow.RowState%2A> property is set to <xref:System.Data.DataRow.Delete%2A>.</span></span>  
  
 <span data-ttu-id="bb9b8-108">在 foreach 迴圈中不應呼叫 <xref:System.Data.DataRow.Delete%2A> 和 <xref:System.Data.DataRowCollection.Remove%2A>，而應逐一查看 <xref:System.Data.DataRowCollection> 物件。</span><span class="sxs-lookup"><span data-stu-id="bb9b8-108">Neither <xref:System.Data.DataRow.Delete%2A> nor <xref:System.Data.DataRowCollection.Remove%2A> should be called in a foreach loop while iterating through a <xref:System.Data.DataRowCollection> object.</span></span> <span data-ttu-id="bb9b8-109"><xref:System.Data.DataRow.Delete%2A> 和 <xref:System.Data.DataRowCollection.Remove%2A> 都不會修改集合的狀態。</span><span class="sxs-lookup"><span data-stu-id="bb9b8-109"><xref:System.Data.DataRow.Delete%2A> nor <xref:System.Data.DataRowCollection.Remove%2A> modify the state of the collection.</span></span>  
  
 <span data-ttu-id="bb9b8-110"><xref:System.Data.DataSet>當使用或**DataTable**搭配**DataAdapter**和關聯式資料來源時, 請使用**DataRow**的**Delete**方法來移除資料列。</span><span class="sxs-lookup"><span data-stu-id="bb9b8-110">When using a <xref:System.Data.DataSet> or **DataTable** in conjunction with a **DataAdapter** and a relational data source, use the **Delete** method of the **DataRow** to remove the row.</span></span> <span data-ttu-id="bb9b8-111">**Delete**方法會將資料列標示為已在**DataSet**或**DataTable**中**刪除**, 但不會將它移除。</span><span class="sxs-lookup"><span data-stu-id="bb9b8-111">The **Delete** method marks the row as **Deleted** in the **DataSet** or **DataTable** but does not remove it.</span></span> <span data-ttu-id="bb9b8-112">相反地, 當**DataAdapter**遇到標記為**已刪除**的資料列時, 它會執行其**DeleteCommand**方法, 以刪除資料來源中的資料列。</span><span class="sxs-lookup"><span data-stu-id="bb9b8-112">Instead, when the **DataAdapter** encounters a row marked as **Deleted**, it executes its **DeleteCommand** method to delete the row at the data source.</span></span> <span data-ttu-id="bb9b8-113">然後, 您可以使用**AcceptChanges**方法來永久移除該資料列。</span><span class="sxs-lookup"><span data-stu-id="bb9b8-113">The row can then be permanently removed using the **AcceptChanges** method.</span></span> <span data-ttu-id="bb9b8-114">如果您使用 [**移除**] 來刪除資料列, 就會從資料表中移除該資料列, 但**DataAdapter**不會刪除資料來源中的資料列。</span><span class="sxs-lookup"><span data-stu-id="bb9b8-114">If you use **Remove** to delete the row, the row is removed entirely from the table, but the **DataAdapter** will not delete the row at the data source.</span></span>  
  
 <span data-ttu-id="bb9b8-115">**DataRowCollection**的**Remove**方法會採用**DataRow**做為引數, 並將它從集合中移除, 如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="bb9b8-115">The **Remove** method of the **DataRowCollection** takes a **DataRow** as an argument and removes it from the collection, as shown in the following example.</span></span>  
  
```vb  
workTable.Rows.Remove(workRow)  
```  
  
```csharp  
workTable.Rows.Remove(workRow);  
```  
  
 <span data-ttu-id="bb9b8-116">相反地, 下列範例將示範如何在**DataRow**上呼叫**Delete**方法, 以將其**RowState**變更為**Deleted**。</span><span class="sxs-lookup"><span data-stu-id="bb9b8-116">In contrast, the following example demonstrates how to call the **Delete** method on a **DataRow** to change its **RowState** to **Deleted**.</span></span>  
  
```vb  
workRow.Delete  
```  
  
```csharp  
workRow.Delete();  
```  
  
 <span data-ttu-id="bb9b8-117">如果將資料列標示為要刪除, 而且您呼叫**datatable**物件的**AcceptChanges**方法, 則會從**datatable**移除該資料列。</span><span class="sxs-lookup"><span data-stu-id="bb9b8-117">If a row is marked for deletion and you call the **AcceptChanges** method of the **DataTable** object, the row is removed from the **DataTable**.</span></span> <span data-ttu-id="bb9b8-118">相反地, 如果您呼叫**RejectChanges**, 則資料列的**RowState**會還原為標示為**已刪除**之前的內容。</span><span class="sxs-lookup"><span data-stu-id="bb9b8-118">In contrast, if you call **RejectChanges**, the **RowState** of the row reverts to what it was before being marked as **Deleted**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bb9b8-119">如果**加入**了**DataRow**的**RowState** , 表示它剛加入至資料表, 然後將它標示為**已刪除**, 則會從資料表中移除它。</span><span class="sxs-lookup"><span data-stu-id="bb9b8-119">If the **RowState** of a **DataRow** is **Added**, meaning it has just been added to the table, and it is then marked as **Deleted**, it is removed from the table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb9b8-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb9b8-120">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="bb9b8-121">在 DataTable 中操作資料</span><span class="sxs-lookup"><span data-stu-id="bb9b8-121">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="bb9b8-122">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="bb9b8-122">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
