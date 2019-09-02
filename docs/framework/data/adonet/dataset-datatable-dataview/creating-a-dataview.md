---
title: 建立 DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
ms.openlocfilehash: 391c071f19149e9690c9121b1094aef5bfa605cd
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203835"
---
# <a name="creating-a-dataview"></a><span data-ttu-id="1306c-102">建立 DataView</span><span class="sxs-lookup"><span data-stu-id="1306c-102">Creating a DataView</span></span>
<span data-ttu-id="1306c-103">建立 <xref:System.Data.DataView> 的方法有兩種。</span><span class="sxs-lookup"><span data-stu-id="1306c-103">There are two ways to create a <xref:System.Data.DataView>.</span></span> <span data-ttu-id="1306c-104">您可以使用**DataView**函式, 也可以建立的<xref:System.Data.DataTable.DefaultView%2A>屬性<xref:System.Data.DataTable>參考。</span><span class="sxs-lookup"><span data-stu-id="1306c-104">You can use the **DataView** constructor, or you can create a reference to the <xref:System.Data.DataTable.DefaultView%2A> property of the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="1306c-105">**DataView**函式可以是空的, 或者可以接受**datatable**做為單一引數, 或將 datatable當做篩選準則、排序準則和資料列狀態篩選。</span><span class="sxs-lookup"><span data-stu-id="1306c-105">The **DataView** constructor can be empty, or it can take either a **DataTable** as a single argument, or a **DataTable** along with filter criteria, sort criteria, and a row state filter.</span></span> <span data-ttu-id="1306c-106">如需可搭配**DataView**使用之其他引數的詳細資訊, 請參閱[排序和篩選資料](sorting-and-filtering-data.md)。</span><span class="sxs-lookup"><span data-stu-id="1306c-106">For more information about the additional arguments available for use with the **DataView**, see [Sorting and Filtering Data](sorting-and-filtering-data.md).</span></span>  
  
 <span data-ttu-id="1306c-107">由於建立**dataview**時, 會同時建立**dataview**的索引, 而且在修改任何**Sort**、 **RowFilter**或**RowStateFilter**屬性時, 您可以藉由提供任何初始的來達到最佳效能。當您建立**DataView**時, 排序次序或篩選準則做為函式引數。</span><span class="sxs-lookup"><span data-stu-id="1306c-107">Because the index for a **DataView** is built both when the **DataView** is created, and when any of the **Sort**, **RowFilter**, or **RowStateFilter** properties are modified, you achieve best performance by supplying any initial sort order or filtering criteria as constructor arguments when you create the **DataView**.</span></span> <span data-ttu-id="1306c-108">建立**dataview**而不指定排序或篩選準則, 然後設定**sort**、 **RowFilter**或**RowStateFilter**屬性之後, 會導致索引至少建立兩次: 一次在**DataView**為會在修改任何排序或篩選屬性時再次建立。</span><span class="sxs-lookup"><span data-stu-id="1306c-108">Creating a **DataView** without specifying sort or filter criteria and then setting the **Sort**, **RowFilter**, or **RowStateFilter** properties later causes the index to be built at least twice: once when the **DataView** is created, and again when any of the sort or filter properties are modified.</span></span>  
  
 <span data-ttu-id="1306c-109">請注意, 如果您使用不接受任何引數的函式來建立**dataview** , 在設定**資料表**屬性之前, 您將無法使用**dataview** 。</span><span class="sxs-lookup"><span data-stu-id="1306c-109">Note that if you create a **DataView** using the constructor that does not take any arguments, you will not be able to use the **DataView** until you have set the **Table** property.</span></span>  
  
 <span data-ttu-id="1306c-110">下列程式碼範例示範如何使用**dataview**函式建立**dataview** 。</span><span class="sxs-lookup"><span data-stu-id="1306c-110">The following code example demonstrates how to create a **DataView** using the **DataView** constructor.</span></span> <span data-ttu-id="1306c-111">**RowFilter**、 **Sort**資料行和**DataViewRowState**會連同**DataTable**一起提供。</span><span class="sxs-lookup"><span data-stu-id="1306c-111">A **RowFilter**, **Sort** column, and **DataViewRowState** are supplied along with the **DataTable**.</span></span>  
  
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
  
 <span data-ttu-id="1306c-112">下列程式碼範例示範如何使用資料表的**DefaultView**屬性, 取得**DataTable**之預設**DataView**的參考。</span><span class="sxs-lookup"><span data-stu-id="1306c-112">The following code example demonstrates how to obtain a reference to the default **DataView** of a **DataTable** using the **DefaultView** property of the table.</span></span>  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a><span data-ttu-id="1306c-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1306c-113">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [<span data-ttu-id="1306c-114">DataView</span><span class="sxs-lookup"><span data-stu-id="1306c-114">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="1306c-115">排序和篩選資料</span><span class="sxs-lookup"><span data-stu-id="1306c-115">Sorting and Filtering Data</span></span>](sorting-and-filtering-data.md)
- [<span data-ttu-id="1306c-116">DataTable</span><span class="sxs-lookup"><span data-stu-id="1306c-116">DataTables</span></span>](datatables.md)
- [<span data-ttu-id="1306c-117">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="1306c-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
