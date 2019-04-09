---
title: 刪除 DataRow
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34f531d-4b9b-4071-b2d7-342c402aa586
ms.openlocfilehash: 57f51ada00bf24617ca3e295a010aae64f0aa849
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59196134"
---
# <a name="datarow-deletion"></a><span data-ttu-id="0b86e-102">刪除 DataRow</span><span class="sxs-lookup"><span data-stu-id="0b86e-102">DataRow Deletion</span></span>
<span data-ttu-id="0b86e-103">有兩種方法可用來刪除<xref:System.Data.DataRow>物件從<xref:System.Data.DataTable>物件：**移除**方法<xref:System.Data.DataRowCollection>物件，而<xref:System.Data.DataRow.Delete%2A>方法**DataRow**物件。</span><span class="sxs-lookup"><span data-stu-id="0b86e-103">There are two methods you can use to delete a <xref:System.Data.DataRow> object from a <xref:System.Data.DataTable> object: the **Remove** method of the <xref:System.Data.DataRowCollection> object, and the <xref:System.Data.DataRow.Delete%2A> method of the **DataRow** object.</span></span> <span data-ttu-id="0b86e-104">然而<xref:System.Data.DataRowCollection.Remove%2A>方法會刪除**DataRow**從**DataRowCollection**，則<xref:System.Data.DataRow.Delete%2A>方法只能標記要刪除的資料列。</span><span class="sxs-lookup"><span data-stu-id="0b86e-104">Whereas the <xref:System.Data.DataRowCollection.Remove%2A> method deletes a **DataRow** from the **DataRowCollection**, the <xref:System.Data.DataRow.Delete%2A> method only marks the row for deletion.</span></span> <span data-ttu-id="0b86e-105">當應用程式呼叫時，就會發生真正的移除作業**AcceptChanges**方法。</span><span class="sxs-lookup"><span data-stu-id="0b86e-105">The actual removal occurs when the application calls the **AcceptChanges** method.</span></span> <span data-ttu-id="0b86e-106">您可以使用 <xref:System.Data.DataRow.Delete%2A>，以程式設計方式檢查有哪些資料列標示為要刪除，然後再將其實際移除。</span><span class="sxs-lookup"><span data-stu-id="0b86e-106">By using <xref:System.Data.DataRow.Delete%2A>, you can programmatically check which rows are marked for deletion before actually removing them.</span></span> <span data-ttu-id="0b86e-107">將資料列標記為要刪除時，會將其 <xref:System.Data.DataRow.RowState%2A> 屬性設為 <xref:System.Data.DataRow.Delete%2A>。</span><span class="sxs-lookup"><span data-stu-id="0b86e-107">When a row is marked for deletion, its <xref:System.Data.DataRow.RowState%2A> property is set to <xref:System.Data.DataRow.Delete%2A>.</span></span>  
  
 <span data-ttu-id="0b86e-108">在 foreach 迴圈中不應呼叫 <xref:System.Data.DataRow.Delete%2A> 和 <xref:System.Data.DataRowCollection.Remove%2A>，而應逐一查看 <xref:System.Data.DataRowCollection> 物件。</span><span class="sxs-lookup"><span data-stu-id="0b86e-108">Neither <xref:System.Data.DataRow.Delete%2A> nor <xref:System.Data.DataRowCollection.Remove%2A> should be called in a foreach loop while iterating through a <xref:System.Data.DataRowCollection> object.</span></span> <xref:System.Data.DataRow.Delete%2A> <span data-ttu-id="0b86e-109">也不<xref:System.Data.DataRowCollection.Remove%2A>修改集合的狀態。</span><span class="sxs-lookup"><span data-stu-id="0b86e-109">nor <xref:System.Data.DataRowCollection.Remove%2A> modify the state of the collection.</span></span>  
  
 <span data-ttu-id="0b86e-110">使用時<xref:System.Data.DataSet>或是**DataTable**搭配**DataAdapter**和關聯式資料來源，使用**刪除**方法**DataRow**若要移除的資料列。</span><span class="sxs-lookup"><span data-stu-id="0b86e-110">When using a <xref:System.Data.DataSet> or **DataTable** in conjunction with a **DataAdapter** and a relational data source, use the **Delete** method of the **DataRow** to remove the row.</span></span> <span data-ttu-id="0b86e-111">**刪除**方法會將資料列做為標記**Deleted**中**資料集**或**DataTable**但不會移除它。</span><span class="sxs-lookup"><span data-stu-id="0b86e-111">The **Delete** method marks the row as **Deleted** in the **DataSet** or **DataTable** but does not remove it.</span></span> <span data-ttu-id="0b86e-112">相反地，當**DataAdapter**遇到標記為一個資料列**已刪除**，它會執行其**DeleteCommand**方法來刪除資料來源的資料列。</span><span class="sxs-lookup"><span data-stu-id="0b86e-112">Instead, when the **DataAdapter** encounters a row marked as **Deleted**, it executes its **DeleteCommand** method to delete the row at the data source.</span></span> <span data-ttu-id="0b86e-113">資料列可以再永久移除使用**AcceptChanges**方法。</span><span class="sxs-lookup"><span data-stu-id="0b86e-113">The row can then be permanently removed using the **AcceptChanges** method.</span></span> <span data-ttu-id="0b86e-114">如果您使用**移除**若要刪除的資料列，資料列完全移除資料表，但**DataAdapter**將不會刪除在資料來源的資料列。</span><span class="sxs-lookup"><span data-stu-id="0b86e-114">If you use **Remove** to delete the row, the row is removed entirely from the table, but the **DataAdapter** will not delete the row at the data source.</span></span>  
  
 <span data-ttu-id="0b86e-115">**移除**方法**DataRowCollection**採用**DataRow**做為引數並將它移除，從集合中，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="0b86e-115">The **Remove** method of the **DataRowCollection** takes a **DataRow** as an argument and removes it from the collection, as shown in the following example.</span></span>  
  
```vb  
workTable.Rows.Remove(workRow)  
```  
  
```csharp  
workTable.Rows.Remove(workRow);  
```  
  
 <span data-ttu-id="0b86e-116">相反地，下列範例示範如何呼叫**刪除**方法**DataRow**若要變更其**RowState**至**Deleted**.</span><span class="sxs-lookup"><span data-stu-id="0b86e-116">In contrast, the following example demonstrates how to call the **Delete** method on a **DataRow** to change its **RowState** to **Deleted**.</span></span>  
  
```vb  
workRow.Delete  
```  
  
```csharp  
workRow.Delete();  
```  
  
 <span data-ttu-id="0b86e-117">如果資料列被標示為刪除，而且您呼叫**AcceptChanges**方法**DataTable**物件，會移除資料列，從**DataTable**。</span><span class="sxs-lookup"><span data-stu-id="0b86e-117">If a row is marked for deletion and you call the **AcceptChanges** method of the **DataTable** object, the row is removed from the **DataTable**.</span></span> <span data-ttu-id="0b86e-118">相反地，如果您呼叫**RejectChanges**，則**RowState**的資料列會還原為之前被標示為**Deleted**。</span><span class="sxs-lookup"><span data-stu-id="0b86e-118">In contrast, if you call **RejectChanges**, the **RowState** of the row reverts to what it was before being marked as **Deleted**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0b86e-119">如果**RowState**的**DataRow**會**Added**，亦即它剛新增至資料表，則會標記為**Deleted**，它是從資料表中移除。</span><span class="sxs-lookup"><span data-stu-id="0b86e-119">If the **RowState** of a **DataRow** is **Added**, meaning it has just been added to the table, and it is then marked as **Deleted**, it is removed from the table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b86e-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b86e-120">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="0b86e-121">在 DataTable 中操作資料</span><span class="sxs-lookup"><span data-stu-id="0b86e-121">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="0b86e-122">ADO.NET Managed 提供者和DataSet開發人員中心</span><span class="sxs-lookup"><span data-stu-id="0b86e-122">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
