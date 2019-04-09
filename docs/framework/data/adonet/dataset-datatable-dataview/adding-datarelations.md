---
title: 加入 DataRelation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a4a564fb-c1c4-4135-b6c2-b030e51195e4
ms.openlocfilehash: 9cefc97e571f315a6a644e0a058d4283168ecb9f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59199358"
---
# <a name="adding-datarelations"></a><span data-ttu-id="dd3bf-102">加入 DataRelation</span><span class="sxs-lookup"><span data-stu-id="dd3bf-102">Adding DataRelations</span></span>
<span data-ttu-id="dd3bf-103">在包含多個 <xref:System.Data.DataSet> 物件的 <xref:System.Data.DataTable> 中，可以使用 <xref:System.Data.DataRelation> 物件建立資料表間的關聯性、巡覽資料表，並從相關資料表傳回子資料列或父資料列。</span><span class="sxs-lookup"><span data-stu-id="dd3bf-103">In a <xref:System.Data.DataSet> with multiple <xref:System.Data.DataTable> objects, you can use <xref:System.Data.DataRelation> objects to relate one table to another, to navigate through the tables, and to return child or parent rows from a related table.</span></span>  
  
 <span data-ttu-id="dd3bf-104">建立所需的引數**DataRelation**是名稱**DataRelation**所建立，以及一或多個陣列<xref:System.Data.DataColumn>做為父和子資料行的參考關聯性中的資料行。</span><span class="sxs-lookup"><span data-stu-id="dd3bf-104">The arguments required to create a **DataRelation** are a name for the **DataRelation** being created, and an array of one or more <xref:System.Data.DataColumn> references to the columns that serve as the parent and child columns in the relationship.</span></span> <span data-ttu-id="dd3bf-105">建立之後**DataRelation**，可以先使用資料表間巡覽並擷取值。</span><span class="sxs-lookup"><span data-stu-id="dd3bf-105">After you have created a **DataRelation**, you can use it to navigate between tables and to retrieve values.</span></span>  
  
 <span data-ttu-id="dd3bf-106">新增**DataRelation**要<xref:System.Data.DataSet>新增，根據預設，<xref:System.Data.UniqueConstraint>父資料表和<xref:System.Data.ForeignKeyConstraint>到子資料表。</span><span class="sxs-lookup"><span data-stu-id="dd3bf-106">Adding a **DataRelation** to a <xref:System.Data.DataSet> adds, by default, a <xref:System.Data.UniqueConstraint> to the parent table and a <xref:System.Data.ForeignKeyConstraint> to the child table.</span></span> <span data-ttu-id="dd3bf-107">如需有關這些預設條件約束的詳細資訊，請參閱 < [DataTable 條件約束](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="dd3bf-107">For more information about these default constraints, see [DataTable Constraints](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span></span>  
  
 <span data-ttu-id="dd3bf-108">下列程式碼範例會建立**DataRelation**使用兩個<xref:System.Data.DataTable>中的物件<xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="dd3bf-108">The following code example creates a **DataRelation** using two <xref:System.Data.DataTable> objects in a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="dd3bf-109">每個<xref:System.Data.DataTable>包含名為的資料行**CustID**，做為兩者之間的連結<xref:System.Data.DataTable>物件。</span><span class="sxs-lookup"><span data-stu-id="dd3bf-109">Each <xref:System.Data.DataTable> contains a column named **CustID**, which serves as a link between the two <xref:System.Data.DataTable> objects.</span></span> <span data-ttu-id="dd3bf-110">範例會新增單一**DataRelation**要**關聯**集合<xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="dd3bf-110">The example adds a single **DataRelation** to the **Relations** collection of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="dd3bf-111">在範例中的第一個引數指定的名稱**DataRelation**所建立。</span><span class="sxs-lookup"><span data-stu-id="dd3bf-111">The first argument in the example specifies the name of the **DataRelation** being created.</span></span> <span data-ttu-id="dd3bf-112">第二個引數設定父**DataColumn**和第三個引數設定子**DataColumn**。</span><span class="sxs-lookup"><span data-stu-id="dd3bf-112">The second argument sets the parent **DataColumn** and the third argument sets the child **DataColumn**.</span></span>  
  
```vb  
customerOrders.Relations.Add("CustOrders", _  
  customerOrders.Tables("Customers").Columns("CustID"), _  
  customerOrders.Tables("Orders").Columns("CustID"))  
```  
  
```csharp  
customerOrders.Relations.Add("CustOrders",  
  customerOrders.Tables["Customers"].Columns["CustID"],  
  customerOrders.Tables["Orders"].Columns["CustID"]);  
```  
  
 <span data-ttu-id="dd3bf-113">A **DataRelation**還有**巢狀**屬性，當設定為**true**，導致從巢狀相關聯的資料列，從父資料表中的子資料表的資料列當撰寫為 XML 項目使用<xref:System.Data.DataSet.WriteXml%2A>。</span><span class="sxs-lookup"><span data-stu-id="dd3bf-113">A **DataRelation** also has a **Nested** property which, when set to **true**, causes the rows from the child table to be nested within the associated row from the parent table when written as XML elements using <xref:System.Data.DataSet.WriteXml%2A> .</span></span> <span data-ttu-id="dd3bf-114">如需詳細資訊，請參閱[在 DataSet 中使用 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)。</span><span class="sxs-lookup"><span data-stu-id="dd3bf-114">For more information, see [Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd3bf-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd3bf-115">See also</span></span>

- [<span data-ttu-id="dd3bf-116">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="dd3bf-116">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="dd3bf-117">ADO.NET Managed 提供者和DataSet開發人員中心</span><span class="sxs-lookup"><span data-stu-id="dd3bf-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
