---
title: 加入 DataRelation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a4a564fb-c1c4-4135-b6c2-b030e51195e4
ms.openlocfilehash: fde1e2ace09e31234d199876ae7f063e01e7a7e4
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203976"
---
# <a name="adding-datarelations"></a><span data-ttu-id="111a3-102">加入 DataRelation</span><span class="sxs-lookup"><span data-stu-id="111a3-102">Adding DataRelations</span></span>
<span data-ttu-id="111a3-103">在包含多個 <xref:System.Data.DataSet> 物件的 <xref:System.Data.DataTable> 中，可以使用 <xref:System.Data.DataRelation> 物件建立資料表間的關聯性、巡覽資料表，並從相關資料表傳回子資料列或父資料列。</span><span class="sxs-lookup"><span data-stu-id="111a3-103">In a <xref:System.Data.DataSet> with multiple <xref:System.Data.DataTable> objects, you can use <xref:System.Data.DataRelation> objects to relate one table to another, to navigate through the tables, and to return child or parent rows from a related table.</span></span>  
  
 <span data-ttu-id="111a3-104">建立**datarelation**所需的引數是所建立之**datarelation**的名稱, 以及一個或多個<xref:System.Data.DataColumn>參考的陣列, 這些資料行是做為關聯性中的父系和子資料行。</span><span class="sxs-lookup"><span data-stu-id="111a3-104">The arguments required to create a **DataRelation** are a name for the **DataRelation** being created, and an array of one or more <xref:System.Data.DataColumn> references to the columns that serve as the parent and child columns in the relationship.</span></span> <span data-ttu-id="111a3-105">建立**DataRelation**之後, 您可以使用它在資料表之間流覽, 並取得值。</span><span class="sxs-lookup"><span data-stu-id="111a3-105">After you have created a **DataRelation**, you can use it to navigate between tables and to retrieve values.</span></span>  
  
 <span data-ttu-id="111a3-106">根據預設 , <xref:System.Data.DataSet> <xref:System.Data.ForeignKeyConstraint>將 DataRelation 加入至父資料表, 並將加入至子資料工作表。 <xref:System.Data.UniqueConstraint></span><span class="sxs-lookup"><span data-stu-id="111a3-106">Adding a **DataRelation** to a <xref:System.Data.DataSet> adds, by default, a <xref:System.Data.UniqueConstraint> to the parent table and a <xref:System.Data.ForeignKeyConstraint> to the child table.</span></span> <span data-ttu-id="111a3-107">如需這些預設條件約束的詳細資訊, 請參閱[DataTable 條件約束](datatable-constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="111a3-107">For more information about these default constraints, see [DataTable Constraints](datatable-constraints.md).</span></span>  
  
 <span data-ttu-id="111a3-108">下列程式碼範例會在中<xref:System.Data.DataSet>使用兩<xref:System.Data.DataTable>個物件來建立**DataRelation** 。</span><span class="sxs-lookup"><span data-stu-id="111a3-108">The following code example creates a **DataRelation** using two <xref:System.Data.DataTable> objects in a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="111a3-109">每<xref:System.Data.DataTable>個都包含一個名為**CustID**的資料行, 其可做<xref:System.Data.DataTable>為兩個物件之間的連結。</span><span class="sxs-lookup"><span data-stu-id="111a3-109">Each <xref:System.Data.DataTable> contains a column named **CustID**, which serves as a link between the two <xref:System.Data.DataTable> objects.</span></span> <span data-ttu-id="111a3-110">這個範例會將單一**DataRelation**加入的關聯性<xref:System.Data.DataSet>集合。</span><span class="sxs-lookup"><span data-stu-id="111a3-110">The example adds a single **DataRelation** to the **Relations** collection of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="111a3-111">範例中的第一個引數會指定所建立之**DataRelation**的名稱。</span><span class="sxs-lookup"><span data-stu-id="111a3-111">The first argument in the example specifies the name of the **DataRelation** being created.</span></span> <span data-ttu-id="111a3-112">第二個引數會設定父系**datacolumn** , 而第三個引數會設定子**datacolumn**。</span><span class="sxs-lookup"><span data-stu-id="111a3-112">The second argument sets the parent **DataColumn** and the third argument sets the child **DataColumn**.</span></span>  
  
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
  
 <span data-ttu-id="111a3-113">**DataRelation**也有一個**Nested**屬性, 當設定為**true**時, 會導致子資料工作表的資料列在使用<xref:System.Data.DataSet.WriteXml%2A>當做 XML 專案寫入時, 從父資料表的相關資料列中加以嵌套。</span><span class="sxs-lookup"><span data-stu-id="111a3-113">A **DataRelation** also has a **Nested** property which, when set to **true**, causes the rows from the child table to be nested within the associated row from the parent table when written as XML elements using <xref:System.Data.DataSet.WriteXml%2A> .</span></span> <span data-ttu-id="111a3-114">如需詳細資訊，請參閱[在 DataSet 中使用 XML](using-xml-in-a-dataset.md)。</span><span class="sxs-lookup"><span data-stu-id="111a3-114">For more information, see [Using XML in a DataSet](using-xml-in-a-dataset.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="111a3-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="111a3-115">See also</span></span>

- [<span data-ttu-id="111a3-116">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="111a3-116">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="111a3-117">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="111a3-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
