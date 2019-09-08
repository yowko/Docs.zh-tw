---
title: 排序及篩選資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fdd9c753-39df-48cd-9822-2781afe76200
ms.openlocfilehash: 09cee2f2b2c3288c835912c9f311bf2511c7b0d0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785922"
---
# <a name="sorting-and-filtering-data"></a><span data-ttu-id="86dc6-102">排序及篩選資料</span><span class="sxs-lookup"><span data-stu-id="86dc6-102">Sorting and Filtering Data</span></span>
<span data-ttu-id="86dc6-103"><xref:System.Data.DataView> 提供數種可在 <xref:System.Data.DataTable> 中排序和篩選資料的方法：</span><span class="sxs-lookup"><span data-stu-id="86dc6-103">The <xref:System.Data.DataView> provides several ways of sorting and filtering data in a <xref:System.Data.DataTable>:</span></span>  
  
- <span data-ttu-id="86dc6-104">您可以使用 <xref:System.Data.DataView.Sort%2A> 屬性，指定單一或多個資料行的排序順序，並納入 ASC (遞增) 和 DESC (遞減) 參數。</span><span class="sxs-lookup"><span data-stu-id="86dc6-104">You can use the <xref:System.Data.DataView.Sort%2A> property to specify single or multiple column sort orders and include ASC (ascending) and DESC (descending) parameters.</span></span>  
  
- <span data-ttu-id="86dc6-105">您可以使用 <xref:System.Data.DataView.ApplyDefaultSort%2A> 屬性，依照主索引鍵資料行或資料表之資料行來自動建立遞增的排序順序。</span><span class="sxs-lookup"><span data-stu-id="86dc6-105">You can use the <xref:System.Data.DataView.ApplyDefaultSort%2A> property to automatically create a sort order, in ascending order, based on the primary key column or columns of the table.</span></span> <span data-ttu-id="86dc6-106"><xref:System.Data.DataView.ApplyDefaultSort%2A>只有在**Sort**屬性為 null 參考或空字串，以及資料表已定義主鍵時，才適用。</span><span class="sxs-lookup"><span data-stu-id="86dc6-106"><xref:System.Data.DataView.ApplyDefaultSort%2A> only applies when the **Sort** property is a null reference or an empty string, and when the table has a primary key defined.</span></span>  
  
- <span data-ttu-id="86dc6-107">您可以使用 <xref:System.Data.DataView.RowFilter%2A> 屬性，依照其資料行的值來指定資料列子集。</span><span class="sxs-lookup"><span data-stu-id="86dc6-107">You can use the <xref:System.Data.DataView.RowFilter%2A> property to specify subsets of rows based on their column values.</span></span> <span data-ttu-id="86dc6-108">如需**RowFilter**屬性之有效運算式的詳細資訊，請參閱<xref:System.Data.DataColumn.Expression%2A> <xref:System.Data.DataColumn>類別之屬性的參考資訊。</span><span class="sxs-lookup"><span data-stu-id="86dc6-108">For details about valid expressions for the **RowFilter** property, see the reference information for the <xref:System.Data.DataColumn.Expression%2A> property of the <xref:System.Data.DataColumn> class.</span></span>  
  
     <span data-ttu-id="86dc6-109">如果您想要傳回資料的特定查詢結果，而不是提供資料子集的動態視圖，請使用<xref:System.Data.DataView.Find%2A> **DataView**的或<xref:System.Data.DataView.FindRows%2A>方法來達到最佳效能，而不是設定**RowFilter**屬性。</span><span class="sxs-lookup"><span data-stu-id="86dc6-109">If you want to return the results of a particular query on the data, as opposed to providing a dynamic view of a subset of the data, use the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods of the **DataView** to achieve best performance rather than setting the **RowFilter** property.</span></span> <span data-ttu-id="86dc6-110">設定**RowFilter**屬性會重建資料的索引，因而增加應用程式的負荷並降低效能。</span><span class="sxs-lookup"><span data-stu-id="86dc6-110">Setting the **RowFilter** property rebuilds the index for the data, adding overhead to your application and decreasing performance.</span></span> <span data-ttu-id="86dc6-111">**RowFilter**屬性最適合用於資料系結應用程式，其中繫結控制項顯示篩選的結果。</span><span class="sxs-lookup"><span data-stu-id="86dc6-111">The **RowFilter** property is best used in a data-bound application where a bound control displays filtered results.</span></span> <span data-ttu-id="86dc6-112">**Find**和**FindRows**方法會利用目前的索引，而不需要重建索引。</span><span class="sxs-lookup"><span data-stu-id="86dc6-112">The **Find** and **FindRows** methods leverage the current index without requiring the index to be rebuilt.</span></span> <span data-ttu-id="86dc6-113">如需**Find**和**FindRows**方法的詳細資訊，請參閱[尋找資料列](finding-rows.md)。</span><span class="sxs-lookup"><span data-stu-id="86dc6-113">For more information about the **Find** and **FindRows** methods, see [Finding Rows](finding-rows.md).</span></span>  
  
- <span data-ttu-id="86dc6-114">您可以使用 <xref:System.Data.DataView.RowStateFilter%2A> 屬性，指定要檢視的資料列版本。</span><span class="sxs-lookup"><span data-stu-id="86dc6-114">You can use the <xref:System.Data.DataView.RowStateFilter%2A> property to specify which row versions to view.</span></span> <span data-ttu-id="86dc6-115">**DataView**會根據基礎資料列的**RowState** ，隱含地管理要公開的資料列版本。</span><span class="sxs-lookup"><span data-stu-id="86dc6-115">The **DataView** implicitly manages which row version to expose depending upon the **RowState** of the underlying row.</span></span> <span data-ttu-id="86dc6-116">例如，如果**RowStateFilter**設定為**DataViewRowState**，則**DataView**會公開所有**已刪除**資料列的**原始**資料列版本，因為沒有**目前**的資料列版本。</span><span class="sxs-lookup"><span data-stu-id="86dc6-116">For example, if the **RowStateFilter** is set to **DataViewRowState.Deleted**, the **DataView** exposes the **Original** row version of all **Deleted** rows because there is no **Current** row version.</span></span> <span data-ttu-id="86dc6-117">您可以使用**DataRowView**的**RowVersion**屬性來判斷要公開的資料列的資料列版本。</span><span class="sxs-lookup"><span data-stu-id="86dc6-117">You can determine which row version of a row is being exposed by using the **RowVersion** property of the **DataRowView**.</span></span>  
  
     <span data-ttu-id="86dc6-118">下表顯示**DataViewRowState**的選項。</span><span class="sxs-lookup"><span data-stu-id="86dc6-118">The following table shows the options for **DataViewRowState**.</span></span>  
  
    |<span data-ttu-id="86dc6-119">DataViewRowState 選項</span><span class="sxs-lookup"><span data-stu-id="86dc6-119">DataViewRowState options</span></span>|<span data-ttu-id="86dc6-120">說明</span><span class="sxs-lookup"><span data-stu-id="86dc6-120">Description</span></span>|  
    |------------------------------|-----------------|  
    |<span data-ttu-id="86dc6-121">**CurrentRows**</span><span class="sxs-lookup"><span data-stu-id="86dc6-121">**CurrentRows**</span></span>|<span data-ttu-id="86dc6-122">所有**未**變更、**已加入**和**已修改**之資料列的**目前**資料列版本。</span><span class="sxs-lookup"><span data-stu-id="86dc6-122">The **Current** row version of all **Unchanged**, **Added**, and **Modified** rows.</span></span> <span data-ttu-id="86dc6-123">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="86dc6-123">This is the default.</span></span>|  
    |<span data-ttu-id="86dc6-124">**加入**</span><span class="sxs-lookup"><span data-stu-id="86dc6-124">**Added**</span></span>|<span data-ttu-id="86dc6-125">所有**已加入**資料列的**目前**資料列版本。</span><span class="sxs-lookup"><span data-stu-id="86dc6-125">The **Current** row version of all **Added** rows.</span></span>|  
    |<span data-ttu-id="86dc6-126">**刪除**</span><span class="sxs-lookup"><span data-stu-id="86dc6-126">**Deleted**</span></span>|<span data-ttu-id="86dc6-127">所有**已刪除**資料列的**原始**資料列版本。</span><span class="sxs-lookup"><span data-stu-id="86dc6-127">The **Original** row version of all **Deleted** rows.</span></span>|  
    |<span data-ttu-id="86dc6-128">**ModifiedCurrent**</span><span class="sxs-lookup"><span data-stu-id="86dc6-128">**ModifiedCurrent**</span></span>|<span data-ttu-id="86dc6-129">所有**已修改**資料列的**目前**資料列版本。</span><span class="sxs-lookup"><span data-stu-id="86dc6-129">The **Current** row version of all **Modified** rows.</span></span>|  
    |<span data-ttu-id="86dc6-130">**ModifiedOriginal**</span><span class="sxs-lookup"><span data-stu-id="86dc6-130">**ModifiedOriginal**</span></span>|<span data-ttu-id="86dc6-131">所有**已修改**資料列的**原始**資料列版本。</span><span class="sxs-lookup"><span data-stu-id="86dc6-131">The **Original** row version of all **Modified** rows.</span></span>|  
    |<span data-ttu-id="86dc6-132">**無**</span><span class="sxs-lookup"><span data-stu-id="86dc6-132">**None**</span></span>|<span data-ttu-id="86dc6-133">無資料列。</span><span class="sxs-lookup"><span data-stu-id="86dc6-133">No rows.</span></span>|  
    |<span data-ttu-id="86dc6-134">**OriginalRows**</span><span class="sxs-lookup"><span data-stu-id="86dc6-134">**OriginalRows**</span></span>|<span data-ttu-id="86dc6-135">所有**未**變更、**已修改**和**已刪除**資料列的**原始**資料列版本。</span><span class="sxs-lookup"><span data-stu-id="86dc6-135">The **Original** row version of all **Unchanged**, **Modified**, and **Deleted** rows.</span></span>|  
    |<span data-ttu-id="86dc6-136">**任何**</span><span class="sxs-lookup"><span data-stu-id="86dc6-136">**Unchanged**</span></span>|<span data-ttu-id="86dc6-137">所有**未**變更資料列的**目前**資料列版本。</span><span class="sxs-lookup"><span data-stu-id="86dc6-137">The **Current** row version of all **Unchanged** rows.</span></span>|  
  
 <span data-ttu-id="86dc6-138">如需資料列狀態和資料列版本的詳細資訊，請參閱資料[列狀態和資料列版本](row-states-and-row-versions.md)。</span><span class="sxs-lookup"><span data-stu-id="86dc6-138">For more information about row states and row versions, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="86dc6-139">下列程式碼範例所建立的檢視，可顯示庫存中所有單位數量低於或等於重新訂購層級的產品，而其檢視內容是依序由廠商 ID 和產品名稱進行排序。</span><span class="sxs-lookup"><span data-stu-id="86dc6-139">The following code example creates a view that shows all the products where the number of units in stock is less than or equal to the reorder level, sorted first by supplier ID and then by product name.</span></span>  
  
```vb  
Dim prodView As DataView = New DataView(prodDS.Tables("Products"), _  
   "UnitsInStock <= ReorderLevel", _  
   "SupplierID, ProductName", _  
   DataViewRowState.CurrentRows)  
```  
  
```csharp  
DataView prodView = new DataView(prodDS.Tables["Products"],  
   "UnitsInStock <= ReorderLevel",  
   "SupplierID, ProductName",  
   DataViewRowState.CurrentRows);  
```  
  
## <a name="see-also"></a><span data-ttu-id="86dc6-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86dc6-140">See also</span></span>

- <xref:System.Data.DataViewRowState>
- <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [<span data-ttu-id="86dc6-141">DataView</span><span class="sxs-lookup"><span data-stu-id="86dc6-141">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="86dc6-142">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="86dc6-142">ADO.NET Overview</span></span>](../ado-net-overview.md)
