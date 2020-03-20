---
title: 建立 DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
ms.openlocfilehash: 9d21b17068ff3ce5b0bd3990144383d7f9ded2f9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151334"
---
# <a name="creating-a-dataview"></a><span data-ttu-id="c6c77-102">建立 DataView</span><span class="sxs-lookup"><span data-stu-id="c6c77-102">Creating a DataView</span></span>
<span data-ttu-id="c6c77-103">建立 <xref:System.Data.DataView> 的方法有兩種。</span><span class="sxs-lookup"><span data-stu-id="c6c77-103">There are two ways to create a <xref:System.Data.DataView>.</span></span> <span data-ttu-id="c6c77-104">您可以使用**DataView**建構函式，也可以創建對<xref:System.Data.DataTable.DefaultView%2A>屬性<xref:System.Data.DataTable>的引用。</span><span class="sxs-lookup"><span data-stu-id="c6c77-104">You can use the **DataView** constructor, or you can create a reference to the <xref:System.Data.DataTable.DefaultView%2A> property of the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="c6c77-105">**DataView**建構函式可以是空的，也可以將**DataTable**作為單個參數，也可以將 DataTable 以及篩選器條件、排序條件和行狀態篩選器視為 **"DataTable"。**</span><span class="sxs-lookup"><span data-stu-id="c6c77-105">The **DataView** constructor can be empty, or it can take either a **DataTable** as a single argument, or a **DataTable** along with filter criteria, sort criteria, and a row state filter.</span></span> <span data-ttu-id="c6c77-106">有關可用於**DataView**的其他參數的詳細資訊，請參閱[排序和篩選資料](sorting-and-filtering-data.md)。</span><span class="sxs-lookup"><span data-stu-id="c6c77-106">For more information about the additional arguments available for use with the **DataView**, see [Sorting and Filtering Data](sorting-and-filtering-data.md).</span></span>  
  
 <span data-ttu-id="c6c77-107">由於**DataView**的索引是在創建**DataView**時構建的，並且當修改任何**排序**、**行篩選器**或**RowStateFilter**屬性時，在創建**DataView**時，通過提供任何初始排序次序或篩選準則作為建構函式參數來實現最佳性能。</span><span class="sxs-lookup"><span data-stu-id="c6c77-107">Because the index for a **DataView** is built both when the **DataView** is created, and when any of the **Sort**, **RowFilter**, or **RowStateFilter** properties are modified, you achieve best performance by supplying any initial sort order or filtering criteria as constructor arguments when you create the **DataView**.</span></span> <span data-ttu-id="c6c77-108">創建**DataView**而不指定排序或篩選準則，然後設置**排序**、**行篩選器**或**RowStateFilter**屬性，以後會導致索引至少生成兩次：創建**DataView**時生成一次，在修改任何排序或篩選器屬性時再次生成索引。</span><span class="sxs-lookup"><span data-stu-id="c6c77-108">Creating a **DataView** without specifying sort or filter criteria and then setting the **Sort**, **RowFilter**, or **RowStateFilter** properties later causes the index to be built at least twice: once when the **DataView** is created, and again when any of the sort or filter properties are modified.</span></span>  
  
 <span data-ttu-id="c6c77-109">請注意，如果使用不採用任何參數的建構函式創建**DataView，** 則在設置**表**屬性之前，您將無法使用**DataView。**</span><span class="sxs-lookup"><span data-stu-id="c6c77-109">Note that if you create a **DataView** using the constructor that does not take any arguments, you will not be able to use the **DataView** until you have set the **Table** property.</span></span>  
  
 <span data-ttu-id="c6c77-110">以下代碼示例演示如何使用**DataView**建構函式創建**DataView。**</span><span class="sxs-lookup"><span data-stu-id="c6c77-110">The following code example demonstrates how to create a **DataView** using the **DataView** constructor.</span></span> <span data-ttu-id="c6c77-111">隨**資料表**一起提供**行篩選器**、**排序**列和**DataViewRowState。**</span><span class="sxs-lookup"><span data-stu-id="c6c77-111">A **RowFilter**, **Sort** column, and **DataViewRowState** are supplied along with the **DataTable**.</span></span>  
  
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
  
 <span data-ttu-id="c6c77-112">以下代碼示例演示如何使用表的**DefaultView**屬性獲取對**DataTable**的預設**DataView**的引用。</span><span class="sxs-lookup"><span data-stu-id="c6c77-112">The following code example demonstrates how to obtain a reference to the default **DataView** of a **DataTable** using the **DefaultView** property of the table.</span></span>  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a><span data-ttu-id="c6c77-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6c77-113">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [<span data-ttu-id="c6c77-114">DataView</span><span class="sxs-lookup"><span data-stu-id="c6c77-114">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="c6c77-115">排序和篩選資料</span><span class="sxs-lookup"><span data-stu-id="c6c77-115">Sorting and Filtering Data</span></span>](sorting-and-filtering-data.md)
- [<span data-ttu-id="c6c77-116">DataTable</span><span class="sxs-lookup"><span data-stu-id="c6c77-116">DataTables</span></span>](datatables.md)
- <span data-ttu-id="c6c77-117">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="c6c77-117">[ADO.NET Overview](../ado-net-overview.md)</span></span>
