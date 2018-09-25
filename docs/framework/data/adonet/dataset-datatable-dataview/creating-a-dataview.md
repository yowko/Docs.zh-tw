---
title: 建立 DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
ms.openlocfilehash: b88df66ef2e065d1db8d4033eb1fb0e47ebdd189
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47108711"
---
# <a name="creating-a-dataview"></a><span data-ttu-id="2e51f-102">建立 DataView</span><span class="sxs-lookup"><span data-stu-id="2e51f-102">Creating a DataView</span></span>
<span data-ttu-id="2e51f-103">建立 <xref:System.Data.DataView> 的方法有兩種。</span><span class="sxs-lookup"><span data-stu-id="2e51f-103">There are two ways to create a <xref:System.Data.DataView>.</span></span> <span data-ttu-id="2e51f-104">您可以使用**DataView**建構函式，或者您可以建立參考<xref:System.Data.DataTable.DefaultView%2A>屬性<xref:System.Data.DataTable>。</span><span class="sxs-lookup"><span data-stu-id="2e51f-104">You can use the **DataView** constructor, or you can create a reference to the <xref:System.Data.DataTable.DefaultView%2A> property of the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="2e51f-105">**DataView**建構函式可以是空的或者也可採用任一**DataTable**做為單一引數，或有**DataTable**篩選準則、 排序條件及一個資料列狀態篩選器。</span><span class="sxs-lookup"><span data-stu-id="2e51f-105">The **DataView** constructor can be empty, or it can take either a **DataTable** as a single argument, or a **DataTable** along with filter criteria, sort criteria, and a row state filter.</span></span> <span data-ttu-id="2e51f-106">如需有關其他引數可用以搭配**DataView**，請參閱[排序及篩選資料](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)。</span><span class="sxs-lookup"><span data-stu-id="2e51f-106">For more information about the additional arguments available for use with the **DataView**, see [Sorting and Filtering Data](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).</span></span>  
  
 <span data-ttu-id="2e51f-107">因為索引**DataView**會**DataView**建立時，以及當任一**排序**， **RowFilter**，或**RowStateFilter**屬性會經過修改，即可藉由提供任何初始排序順序或篩選準則做為建構函式引數，當您建立時達到最佳效能**DataView**。</span><span class="sxs-lookup"><span data-stu-id="2e51f-107">Because the index for a **DataView** is built both when the **DataView** is created, and when any of the **Sort**, **RowFilter**, or **RowStateFilter** properties are modified, you achieve best performance by supplying any initial sort order or filtering criteria as constructor arguments when you create the **DataView**.</span></span> <span data-ttu-id="2e51f-108">建立**DataView**而不指定排序或篩選準則，然後設定**排序**， **RowFilter**，或**RowStateFilter**屬性稍後會導致至少兩次建立索引： 一旦時**DataView**建立時，並一次的任何排序或篩選屬性修改時。</span><span class="sxs-lookup"><span data-stu-id="2e51f-108">Creating a **DataView** without specifying sort or filter criteria and then setting the **Sort**, **RowFilter**, or **RowStateFilter** properties later causes the index to be built at least twice: once when the **DataView** is created, and again when any of the sort or filter properties are modified.</span></span>  
  
 <span data-ttu-id="2e51f-109">請注意，如果您建立**DataView**使用未採用任何引數的建構函式，您將無法再使用**DataView**除非您已設定**表格**屬性.</span><span class="sxs-lookup"><span data-stu-id="2e51f-109">Note that if you create a **DataView** using the constructor that does not take any arguments, you will not be able to use the **DataView** until you have set the **Table** property.</span></span>  
  
 <span data-ttu-id="2e51f-110">下列程式碼範例示範如何建立**DataView**使用**DataView**建構函式。</span><span class="sxs-lookup"><span data-stu-id="2e51f-110">The following code example demonstrates how to create a **DataView** using the **DataView** constructor.</span></span> <span data-ttu-id="2e51f-111">A **RowFilter**，**排序**資料行，並**DataViewRowState**提供**DataTable**。</span><span class="sxs-lookup"><span data-stu-id="2e51f-111">A **RowFilter**, **Sort** column, and **DataViewRowState** are supplied along with the **DataTable**.</span></span>  
  
```vb  
Dim custDV As DataView = New DataView(custDS.Tables("Customers"), _  
    "Country = 'USA'", _  
    "ContactName", _  
    DataViewRowState.CurrentRows)  
```  
  
```csharp  
DataView custDV = new DataView(custDS.Tables["Customers"],   
    "Country = 'USA'",   
    "ContactName",   
    DataViewRowState.CurrentRows);  
```  
  
 <span data-ttu-id="2e51f-112">下列程式碼範例示範如何取得預設值的參考**DataView**的**DataTable**使用**DefaultView**資料表屬性。</span><span class="sxs-lookup"><span data-stu-id="2e51f-112">The following code example demonstrates how to obtain a reference to the default **DataView** of a **DataTable** using the **DefaultView** property of the table.</span></span>  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a><span data-ttu-id="2e51f-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e51f-113">See Also</span></span>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [<span data-ttu-id="2e51f-114">DataView</span><span class="sxs-lookup"><span data-stu-id="2e51f-114">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [<span data-ttu-id="2e51f-115">排序和篩選資料</span><span class="sxs-lookup"><span data-stu-id="2e51f-115">Sorting and Filtering Data</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)  
 [<span data-ttu-id="2e51f-116">DataTable</span><span class="sxs-lookup"><span data-stu-id="2e51f-116">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="2e51f-117">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="2e51f-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
