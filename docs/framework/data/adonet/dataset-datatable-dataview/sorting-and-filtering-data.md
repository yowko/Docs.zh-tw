---
title: "排序及篩選資料"
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
ms.assetid: fdd9c753-39df-48cd-9822-2781afe76200
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 01c09d94fd3224e8fd875b7f6eea06b2d2c35cca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="sorting-and-filtering-data"></a><span data-ttu-id="844fc-102">排序及篩選資料</span><span class="sxs-lookup"><span data-stu-id="844fc-102">Sorting and Filtering Data</span></span>
<span data-ttu-id="844fc-103"><xref:System.Data.DataView> 提供數種可在 <xref:System.Data.DataTable> 中排序和篩選資料的方法：</span><span class="sxs-lookup"><span data-stu-id="844fc-103">The <xref:System.Data.DataView> provides several ways of sorting and filtering data in a <xref:System.Data.DataTable>:</span></span>  
  
-   <span data-ttu-id="844fc-104">您可以使用 <xref:System.Data.DataView.Sort%2A> 屬性，指定單一或多個資料行的排序順序，並納入 ASC (遞增) 和 DESC (遞減) 參數。</span><span class="sxs-lookup"><span data-stu-id="844fc-104">You can use the <xref:System.Data.DataView.Sort%2A> property to specify single or multiple column sort orders and include ASC (ascending) and DESC (descending) parameters.</span></span>  
  
-   <span data-ttu-id="844fc-105">您可以使用 <xref:System.Data.DataView.ApplyDefaultSort%2A> 屬性，依照主索引鍵資料行或資料表之資料行來自動建立遞增的排序順序。</span><span class="sxs-lookup"><span data-stu-id="844fc-105">You can use the <xref:System.Data.DataView.ApplyDefaultSort%2A> property to automatically create a sort order, in ascending order, based on the primary key column or columns of the table.</span></span> <span data-ttu-id="844fc-106"><xref:System.Data.DataView.ApplyDefaultSort%2A>僅適用於當**排序**屬性為 null 參考或空字串，而當資料表有定義的主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="844fc-106"><xref:System.Data.DataView.ApplyDefaultSort%2A> only applies when the **Sort** property is a null reference or an empty string, and when the table has a primary key defined.</span></span>  
  
-   <span data-ttu-id="844fc-107">您可以使用 <xref:System.Data.DataView.RowFilter%2A> 屬性，依照其資料行的值來指定資料列子集。</span><span class="sxs-lookup"><span data-stu-id="844fc-107">You can use the <xref:System.Data.DataView.RowFilter%2A> property to specify subsets of rows based on their column values.</span></span> <span data-ttu-id="844fc-108">如需有效運算式的詳細資訊**RowFilter**屬性，請參閱的參考資訊<xref:System.Data.DataColumn.Expression%2A>屬性<xref:System.Data.DataColumn>類別。</span><span class="sxs-lookup"><span data-stu-id="844fc-108">For details about valid expressions for the **RowFilter** property, see the reference information for the <xref:System.Data.DataColumn.Expression%2A> property of the <xref:System.Data.DataColumn> class.</span></span>  
  
     <span data-ttu-id="844fc-109">如果您想要傳回的資料，而不是提供資料子集的動態檢視的特定查詢的結果，請使用<xref:System.Data.DataView.Find%2A>或<xref:System.Data.DataView.FindRows%2A>方法**DataView**達到最佳效能而非設定**RowFilter**屬性。</span><span class="sxs-lookup"><span data-stu-id="844fc-109">If you want to return the results of a particular query on the data, as opposed to providing a dynamic view of a subset of the data, use the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods of the **DataView** to achieve best performance rather than setting the **RowFilter** property.</span></span> <span data-ttu-id="844fc-110">設定**RowFilter**屬性會重建索引的資料加入至應用程式的額外負荷並降低效能。</span><span class="sxs-lookup"><span data-stu-id="844fc-110">Setting the **RowFilter** property rebuilds the index for the data, adding overhead to your application and decreasing performance.</span></span> <span data-ttu-id="844fc-111">**RowFilter**屬性最適合用於資料繫結應用程式繫結的控制項顯示篩選的結果的位置。</span><span class="sxs-lookup"><span data-stu-id="844fc-111">The **RowFilter** property is best used in a data-bound application where a bound control displays filtered results.</span></span> <span data-ttu-id="844fc-112">**尋找**和**FindRows**方法會使用目前的索引而不需要重建索引。</span><span class="sxs-lookup"><span data-stu-id="844fc-112">The **Find** and **FindRows** methods leverage the current index without requiring the index to be rebuilt.</span></span> <span data-ttu-id="844fc-113">如需有關**尋找**和**FindRows**方法，請參閱[尋找資料列](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md)。</span><span class="sxs-lookup"><span data-stu-id="844fc-113">For more information about the **Find** and **FindRows** methods, see [Finding Rows](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).</span></span>  
  
-   <span data-ttu-id="844fc-114">您可以使用 <xref:System.Data.DataView.RowStateFilter%2A> 屬性，指定要檢視的資料列版本。</span><span class="sxs-lookup"><span data-stu-id="844fc-114">You can use the <xref:System.Data.DataView.RowStateFilter%2A> property to specify which row versions to view.</span></span> <span data-ttu-id="844fc-115">**DataView**隱含管理要公開 （expose） 而定的資料列版本**RowState**基礎資料列。</span><span class="sxs-lookup"><span data-stu-id="844fc-115">The **DataView** implicitly manages which row version to expose depending upon the **RowState** of the underlying row.</span></span> <span data-ttu-id="844fc-116">例如，如果**RowStateFilter**設為**DataViewRowState.Deleted**、 **DataView**公開**原始**的資料列版本所有**刪除**資料列，所以沒有**目前**資料列版本。</span><span class="sxs-lookup"><span data-stu-id="844fc-116">For example, if the **RowStateFilter** is set to **DataViewRowState.Deleted**, the **DataView** exposes the **Original** row version of all **Deleted** rows because there is no **Current** row version.</span></span> <span data-ttu-id="844fc-117">您可以判斷資料列版本資料列的正在使用公開**RowVersion**屬性**DataRowView**。</span><span class="sxs-lookup"><span data-stu-id="844fc-117">You can determine which row version of a row is being exposed by using the **RowVersion** property of the **DataRowView**.</span></span>  
  
     <span data-ttu-id="844fc-118">下表顯示的選項**DataViewRowState**。</span><span class="sxs-lookup"><span data-stu-id="844fc-118">The following table shows the options for **DataViewRowState**.</span></span>  
  
    |<span data-ttu-id="844fc-119">DataViewRowState 選項</span><span class="sxs-lookup"><span data-stu-id="844fc-119">DataViewRowState options</span></span>|<span data-ttu-id="844fc-120">說明</span><span class="sxs-lookup"><span data-stu-id="844fc-120">Description</span></span>|  
    |------------------------------|-----------------|  
    |<span data-ttu-id="844fc-121">**CurrentRows**</span><span class="sxs-lookup"><span data-stu-id="844fc-121">**CurrentRows**</span></span>|<span data-ttu-id="844fc-122">**目前**的所有資料列版本**Unchanged**， **Added**，和**Modified**資料列。</span><span class="sxs-lookup"><span data-stu-id="844fc-122">The **Current** row version of all **Unchanged**, **Added**, and **Modified** rows.</span></span> <span data-ttu-id="844fc-123">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="844fc-123">This is the default.</span></span>|  
    |<span data-ttu-id="844fc-124">**加入**</span><span class="sxs-lookup"><span data-stu-id="844fc-124">**Added**</span></span>|<span data-ttu-id="844fc-125">**目前**的所有資料列版本**Added**資料列。</span><span class="sxs-lookup"><span data-stu-id="844fc-125">The **Current** row version of all **Added** rows.</span></span>|  
    |<span data-ttu-id="844fc-126">**刪除**</span><span class="sxs-lookup"><span data-stu-id="844fc-126">**Deleted**</span></span>|<span data-ttu-id="844fc-127">**原始**的所有資料列版本**刪除**資料列。</span><span class="sxs-lookup"><span data-stu-id="844fc-127">The **Original** row version of all **Deleted** rows.</span></span>|  
    |<span data-ttu-id="844fc-128">**ModifiedCurrent**</span><span class="sxs-lookup"><span data-stu-id="844fc-128">**ModifiedCurrent**</span></span>|<span data-ttu-id="844fc-129">**目前**的所有資料列版本**Modified**資料列。</span><span class="sxs-lookup"><span data-stu-id="844fc-129">The **Current** row version of all **Modified** rows.</span></span>|  
    |<span data-ttu-id="844fc-130">**ModifiedOriginal**</span><span class="sxs-lookup"><span data-stu-id="844fc-130">**ModifiedOriginal**</span></span>|<span data-ttu-id="844fc-131">**原始**的所有資料列版本**Modified**資料列。</span><span class="sxs-lookup"><span data-stu-id="844fc-131">The **Original** row version of all **Modified** rows.</span></span>|  
    |<span data-ttu-id="844fc-132">**無**</span><span class="sxs-lookup"><span data-stu-id="844fc-132">**None**</span></span>|<span data-ttu-id="844fc-133">無資料列。</span><span class="sxs-lookup"><span data-stu-id="844fc-133">No rows.</span></span>|  
    |<span data-ttu-id="844fc-134">**OriginalRows**</span><span class="sxs-lookup"><span data-stu-id="844fc-134">**OriginalRows**</span></span>|<span data-ttu-id="844fc-135">**原始**的所有資料列版本**Unchanged**， **Modified**，和**刪除**資料列。</span><span class="sxs-lookup"><span data-stu-id="844fc-135">The **Original** row version of all **Unchanged**, **Modified**, and **Deleted** rows.</span></span>|  
    |<span data-ttu-id="844fc-136">**不變**</span><span class="sxs-lookup"><span data-stu-id="844fc-136">**Unchanged**</span></span>|<span data-ttu-id="844fc-137">**目前**的所有資料列版本**Unchanged**資料列。</span><span class="sxs-lookup"><span data-stu-id="844fc-137">The **Current** row version of all **Unchanged** rows.</span></span>|  
  
 <span data-ttu-id="844fc-138">如需有關資料列狀態和資料列版本的詳細資訊，請參閱[資料列狀態和資料列版本](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)。</span><span class="sxs-lookup"><span data-stu-id="844fc-138">For more information about row states and row versions, see [Row States and Row Versions](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="844fc-139">下列程式碼範例所建立的檢視，可顯示庫存中所有單位數量低於或等於重新訂購層級的產品，而其檢視內容是依序由廠商 ID 和產品名稱進行排序。</span><span class="sxs-lookup"><span data-stu-id="844fc-139">The following code example creates a view that shows all the products where the number of units in stock is less than or equal to the reorder level, sorted first by supplier ID and then by product name.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="844fc-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="844fc-140">See Also</span></span>  
 <xref:System.Data.DataViewRowState>  
 <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [<span data-ttu-id="844fc-141">DataView</span><span class="sxs-lookup"><span data-stu-id="844fc-141">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [<span data-ttu-id="844fc-142">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="844fc-142">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
