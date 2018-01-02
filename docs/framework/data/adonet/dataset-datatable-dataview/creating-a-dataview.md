---
title: "建立 DataView"
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
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 53cbfc5097c28c0677a164f817cfe14927814d75
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-dataview"></a><span data-ttu-id="09323-102">建立 DataView</span><span class="sxs-lookup"><span data-stu-id="09323-102">Creating a DataView</span></span>
<span data-ttu-id="09323-103">建立 <xref:System.Data.DataView> 的方法有兩種。</span><span class="sxs-lookup"><span data-stu-id="09323-103">There are two ways to create a <xref:System.Data.DataView>.</span></span> <span data-ttu-id="09323-104">您可以使用**DataView**建構函式，或者您可以建立參考<xref:System.Data.DataTable.DefaultView%2A>屬性<xref:System.Data.DataTable>。</span><span class="sxs-lookup"><span data-stu-id="09323-104">You can use the **DataView** constructor, or you can create a reference to the <xref:System.Data.DataTable.DefaultView%2A> property of the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="09323-105">**DataView**建構函式可以是空的或者也可採用任一**DataTable**做為單一引數，或**DataTable**配合篩選準則、 排序準則和資料列狀態篩選器。</span><span class="sxs-lookup"><span data-stu-id="09323-105">The **DataView** constructor can be empty, or it can take either a **DataTable** as a single argument, or a **DataTable** along with filter criteria, sort criteria, and a row state filter.</span></span> <span data-ttu-id="09323-106">如需有關其他引數可用於**DataView**，請參閱[排序及篩選資料](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)。</span><span class="sxs-lookup"><span data-stu-id="09323-106">For more information about the additional arguments available for use with the **DataView**, see [Sorting and Filtering Data](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).</span></span>  
  
 <span data-ttu-id="09323-107">因為索引**DataView**會**DataView**建立時，以及當任一**排序**， **RowFilter**，或**RowStateFilter**修改屬性、 您達到最佳效能提供任何初始排序順序或篩選準則做為建構函式引數，當您建立**DataView**。</span><span class="sxs-lookup"><span data-stu-id="09323-107">Because the index for a **DataView** is built both when the **DataView** is created, and when any of the **Sort**, **RowFilter**, or **RowStateFilter** properties are modified, you achieve best performance by supplying any initial sort order or filtering criteria as constructor arguments when you create the **DataView**.</span></span> <span data-ttu-id="09323-108">建立**DataView**而不指定排序或篩選準則，然後設定**排序**， **RowFilter**，或**RowStateFilter**屬性稍後會導致索引建立至少兩次： 一旦時**DataView**建立時，以及重新排序或篩選屬性的任何會修改。</span><span class="sxs-lookup"><span data-stu-id="09323-108">Creating a **DataView** without specifying sort or filter criteria and then setting the **Sort**, **RowFilter**, or **RowStateFilter** properties later causes the index to be built at least twice: once when the **DataView** is created, and again when any of the sort or filter properties are modified.</span></span>  
  
 <span data-ttu-id="09323-109">請注意，如果您建立**DataView**使用不接受任何引數的建構函式，您將無法使用**DataView**除非您已設定**資料表**屬性.</span><span class="sxs-lookup"><span data-stu-id="09323-109">Note that if you create a **DataView** using the constructor that does not take any arguments, you will not be able to use the **DataView** until you have set the **Table** property.</span></span>  
  
 <span data-ttu-id="09323-110">下列程式碼範例示範如何建立**DataView**使用**DataView**建構函式。</span><span class="sxs-lookup"><span data-stu-id="09323-110">The following code example demonstrates how to create a **DataView** using the **DataView** constructor.</span></span> <span data-ttu-id="09323-111">A **RowFilter**，**排序**資料行，和**DataViewRowState**一併提供**DataTable**。</span><span class="sxs-lookup"><span data-stu-id="09323-111">A **RowFilter**, **Sort** column, and **DataViewRowState** are supplied along with the **DataTable**.</span></span>  
  
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
  
 <span data-ttu-id="09323-112">下列程式碼範例示範如何取得預設的參考**DataView**的**DataTable**使用**DefaultView**資料表屬性。</span><span class="sxs-lookup"><span data-stu-id="09323-112">The following code example demonstrates how to obtain a reference to the default **DataView** of a **DataTable** using the **DefaultView** property of the table.</span></span>  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a><span data-ttu-id="09323-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="09323-113">See Also</span></span>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [<span data-ttu-id="09323-114">DataView</span><span class="sxs-lookup"><span data-stu-id="09323-114">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [<span data-ttu-id="09323-115">排序和篩選資料</span><span class="sxs-lookup"><span data-stu-id="09323-115">Sorting and Filtering Data</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)  
 [<span data-ttu-id="09323-116">DataTable</span><span class="sxs-lookup"><span data-stu-id="09323-116">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="09323-117">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="09323-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
