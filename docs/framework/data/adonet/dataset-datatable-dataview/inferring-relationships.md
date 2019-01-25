---
title: 推斷關聯性
ms.date: 03/30/2017
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
ms.openlocfilehash: 2d25160b8dae8b8dc883abb589551782925ca325
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54536278"
---
# <a name="inferring-relationships"></a><span data-ttu-id="e4aee-102">推斷關聯性</span><span class="sxs-lookup"><span data-stu-id="e4aee-102">Inferring Relationships</span></span>
<span data-ttu-id="e4aee-103">若被推斷為資料表的項目具有子項目，且子項目也被推斷為資料表，則兩個資料表間會建立 <xref:System.Data.DataRelation>。</span><span class="sxs-lookup"><span data-stu-id="e4aee-103">If an element that is inferred as a table has a child element that is also inferred as a table, a <xref:System.Data.DataRelation> will be created between the two tables.</span></span> <span data-ttu-id="e4aee-104">新的資料行名稱取代**ParentTableName_Id**會新增至父元素中，建立的資料表和子元素所建立的資料表。</span><span class="sxs-lookup"><span data-stu-id="e4aee-104">A new column with a name of **ParentTableName_Id** will be added to both the table created for the parent element, and the table created for the child element.</span></span> <span data-ttu-id="e4aee-105">**ColumnMapping**此識別欄位的屬性會設定為**MappingType.Hidden**。</span><span class="sxs-lookup"><span data-stu-id="e4aee-105">The **ColumnMapping** property of this identity column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="e4aee-106">將會自動遞增主索引鍵的父資料表，資料行，並將用於**DataRelation**兩個資料表之間。</span><span class="sxs-lookup"><span data-stu-id="e4aee-106">The column will be an auto-incrementing primary key for the parent table, and will be used for the **DataRelation** between the two tables.</span></span> <span data-ttu-id="e4aee-107">新增的身分識別資料行的資料型別會**System.Int32**，其他所有推斷的資料行的資料型別，即**System.String**。</span><span class="sxs-lookup"><span data-stu-id="e4aee-107">The data type of the added identity column will be **System.Int32**, unlike the data type of all other inferred columns, which is **System.String**.</span></span> <span data-ttu-id="e4aee-108">A<xref:System.Data.ForeignKeyConstraint>具有**DeleteRule** = **Cascade**也會建立在父和子資料表中使用新的資料行。</span><span class="sxs-lookup"><span data-stu-id="e4aee-108">A <xref:System.Data.ForeignKeyConstraint> with **DeleteRule** = **Cascade** will also be created using the new column in both the parent and child tables.</span></span>  
  
 <span data-ttu-id="e4aee-109">例如，請考量下列 XML：</span><span class="sxs-lookup"><span data-stu-id="e4aee-109">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="e4aee-110">推斷處理序會產生兩個資料表：**Element1**並**ChildElement1**。</span><span class="sxs-lookup"><span data-stu-id="e4aee-110">The inference process will produce two tables: **Element1** and **ChildElement1**.</span></span>  
  
 <span data-ttu-id="e4aee-111">**Element1**資料表會有兩個資料行：**Element1_Id**並**ChildElement2**。</span><span class="sxs-lookup"><span data-stu-id="e4aee-111">The **Element1** table will have two columns: **Element1_Id** and **ChildElement2**.</span></span> <span data-ttu-id="e4aee-112">**ColumnMapping**屬性**Element1_Id**資料行都會設定為**MappingType.Hidden**。</span><span class="sxs-lookup"><span data-stu-id="e4aee-112">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="e4aee-113">**ColumnMapping**屬性**ChildElement2**資料行都會設定為**MappingType.Element**。</span><span class="sxs-lookup"><span data-stu-id="e4aee-113">The **ColumnMapping** property of the **ChildElement2** column will be set to **MappingType.Element**.</span></span> <span data-ttu-id="e4aee-114">**Element1_Id**資料行都會設定為的主索引鍵**Element1**資料表。</span><span class="sxs-lookup"><span data-stu-id="e4aee-114">The **Element1_Id** column will be set as the primary key of the **Element1** table.</span></span>  
  
 <span data-ttu-id="e4aee-115">**ChildElement1**資料表會有三個資料行： **attr1**， **attr2**並**Element1_Id**。</span><span class="sxs-lookup"><span data-stu-id="e4aee-115">The **ChildElement1** table will have three columns: **attr1**, **attr2** and **Element1_Id**.</span></span> <span data-ttu-id="e4aee-116">**ColumnMapping**屬性**attr1**並**attr2**資料行都會設定為**MappingType.Attribute**。</span><span class="sxs-lookup"><span data-stu-id="e4aee-116">The **ColumnMapping** property for the **attr1** and **attr2** columns will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="e4aee-117">**ColumnMapping**屬性**Element1_Id**資料行都會設定為**MappingType.Hidden**。</span><span class="sxs-lookup"><span data-stu-id="e4aee-117">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span>  
  
 <span data-ttu-id="e4aee-118">A **DataRelation**並**ForeignKeyConstraint**將會使用建立**Element1_Id**兩個資料表的資料行。</span><span class="sxs-lookup"><span data-stu-id="e4aee-118">A **DataRelation** and **ForeignKeyConstraint** will be created using the **Element1_Id** columns from both tables.</span></span>  
  
 <span data-ttu-id="e4aee-119">**資料集：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="e4aee-119">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="e4aee-120">**資料表：** Element1</span><span class="sxs-lookup"><span data-stu-id="e4aee-120">**Table:** Element1</span></span>  
  
|<span data-ttu-id="e4aee-121">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="e4aee-121">Element1_Id</span></span>|<span data-ttu-id="e4aee-122">ChildElement2</span><span class="sxs-lookup"><span data-stu-id="e4aee-122">ChildElement2</span></span>|  
|------------------|-------------------|  
|<span data-ttu-id="e4aee-123">0</span><span class="sxs-lookup"><span data-stu-id="e4aee-123">0</span></span>|<span data-ttu-id="e4aee-124">Text2</span><span class="sxs-lookup"><span data-stu-id="e4aee-124">Text2</span></span>|  
  
 <span data-ttu-id="e4aee-125">**資料表：** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="e4aee-125">**Table:** ChildElement1</span></span>  
  
|<span data-ttu-id="e4aee-126">attr1</span><span class="sxs-lookup"><span data-stu-id="e4aee-126">attr1</span></span>|<span data-ttu-id="e4aee-127">attr2</span><span class="sxs-lookup"><span data-stu-id="e4aee-127">attr2</span></span>|<span data-ttu-id="e4aee-128">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="e4aee-128">Element1_Id</span></span>|  
|-----------|-----------|------------------|  
|<span data-ttu-id="e4aee-129">value1</span><span class="sxs-lookup"><span data-stu-id="e4aee-129">value1</span></span>|<span data-ttu-id="e4aee-130">value2</span><span class="sxs-lookup"><span data-stu-id="e4aee-130">value2</span></span>|<span data-ttu-id="e4aee-131">0</span><span class="sxs-lookup"><span data-stu-id="e4aee-131">0</span></span>|  
  
 <span data-ttu-id="e4aee-132">**DataRelation:** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="e4aee-132">**DataRelation:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="e4aee-133">**ParentTable:** Element1</span><span class="sxs-lookup"><span data-stu-id="e4aee-133">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="e4aee-134">**ParentColumn:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="e4aee-134">**ParentColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="e4aee-135">**ChildTable:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="e4aee-135">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="e4aee-136">**ChildColumn:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="e4aee-136">**ChildColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="e4aee-137">**巢狀：** True</span><span class="sxs-lookup"><span data-stu-id="e4aee-137">**Nested:** True</span></span>  
  
 <span data-ttu-id="e4aee-138">**ForeignKeyConstraint:** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="e4aee-138">**ForeignKeyConstraint:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="e4aee-139">**資料行：** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="e4aee-139">**Column:** Element1_Id</span></span>  
  
 <span data-ttu-id="e4aee-140">**ParentTable:** Element1</span><span class="sxs-lookup"><span data-stu-id="e4aee-140">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="e4aee-141">**ChildTable:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="e4aee-141">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="e4aee-142">**DeleteRule:** Cascade</span><span class="sxs-lookup"><span data-stu-id="e4aee-142">**DeleteRule:** Cascade</span></span>  
  
 <span data-ttu-id="e4aee-143">**AcceptRejectRule:** 無</span><span class="sxs-lookup"><span data-stu-id="e4aee-143">**AcceptRejectRule:** None</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4aee-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4aee-144">See also</span></span>
- [<span data-ttu-id="e4aee-145">從 XML 推斷資料集關聯式結構</span><span class="sxs-lookup"><span data-stu-id="e4aee-145">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="e4aee-146">從 XML 載入資料集</span><span class="sxs-lookup"><span data-stu-id="e4aee-146">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [<span data-ttu-id="e4aee-147">從 XML 載入資料集結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="e4aee-147">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="e4aee-148">巢狀 DataRelation</span><span class="sxs-lookup"><span data-stu-id="e4aee-148">Nesting DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)
- [<span data-ttu-id="e4aee-149">在 DataSet 中使用 XML</span><span class="sxs-lookup"><span data-stu-id="e4aee-149">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [<span data-ttu-id="e4aee-150">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="e4aee-150">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="e4aee-151">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="e4aee-151">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
