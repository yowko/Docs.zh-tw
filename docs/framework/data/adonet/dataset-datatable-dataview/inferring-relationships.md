---
title: 推斷關聯性
ms.date: 03/30/2017
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
ms.openlocfilehash: 92a4953dc7f5119ffbf171ff2a7bf5b58e896638
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204766"
---
# <a name="inferring-relationships"></a><span data-ttu-id="ff74b-102">推斷關聯性</span><span class="sxs-lookup"><span data-stu-id="ff74b-102">Inferring Relationships</span></span>
<span data-ttu-id="ff74b-103">若被推斷為資料表的項目具有子項目，且子項目也被推斷為資料表，則兩個資料表間會建立 <xref:System.Data.DataRelation>。</span><span class="sxs-lookup"><span data-stu-id="ff74b-103">If an element that is inferred as a table has a child element that is also inferred as a table, a <xref:System.Data.DataRelation> will be created between the two tables.</span></span> <span data-ttu-id="ff74b-104">系統會將名稱為**ParentTableName_Id**的新資料行加入至針對父元素所建立的資料表, 以及為子項目建立的資料表。</span><span class="sxs-lookup"><span data-stu-id="ff74b-104">A new column with a name of **ParentTableName_Id** will be added to both the table created for the parent element, and the table created for the child element.</span></span> <span data-ttu-id="ff74b-105">此識別欄位的**ColumnMapping**屬性將會設定為**MappingType。**</span><span class="sxs-lookup"><span data-stu-id="ff74b-105">The **ColumnMapping** property of this identity column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="ff74b-106">此資料行將會是父資料表的自動遞增主鍵, 並會用於這兩個數據表之間的**DataRelation** 。</span><span class="sxs-lookup"><span data-stu-id="ff74b-106">The column will be an auto-incrementing primary key for the parent table, and will be used for the **DataRelation** between the two tables.</span></span> <span data-ttu-id="ff74b-107">加入之識別欄位的資料類型會是 system.string, 而不像所有其他推斷資料行的資料類型, 也就是**system.string**。</span><span class="sxs-lookup"><span data-stu-id="ff74b-107">The data type of the added identity column will be **System.Int32**, unlike the data type of all other inferred columns, which is **System.String**.</span></span> <span data-ttu-id="ff74b-108">具有 DeleteRule**Cascade 的**會同時使用父資料表和子資料工作表中的新資料行建立。 <xref:System.Data.ForeignKeyConstraint>  = </span><span class="sxs-lookup"><span data-stu-id="ff74b-108">A <xref:System.Data.ForeignKeyConstraint> with **DeleteRule** = **Cascade** will also be created using the new column in both the parent and child tables.</span></span>  
  
 <span data-ttu-id="ff74b-109">例如，請考量下列 XML：</span><span class="sxs-lookup"><span data-stu-id="ff74b-109">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="ff74b-110">推斷處理序會產生兩個資料表：**Element1**和**ChildElement1**。</span><span class="sxs-lookup"><span data-stu-id="ff74b-110">The inference process will produce two tables: **Element1** and **ChildElement1**.</span></span>  
  
 <span data-ttu-id="ff74b-111">**Element1**資料表會有兩個數據行:**Element1_Id**和**ChildElement2**。</span><span class="sxs-lookup"><span data-stu-id="ff74b-111">The **Element1** table will have two columns: **Element1_Id** and **ChildElement2**.</span></span> <span data-ttu-id="ff74b-112">**Element1_Id**資料行的**ColumnMapping**屬性會設定為**MappingType。 Hidden**。</span><span class="sxs-lookup"><span data-stu-id="ff74b-112">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="ff74b-113">**ChildElement2**資料行的**ColumnMapping**屬性會設定為**MappingType。**</span><span class="sxs-lookup"><span data-stu-id="ff74b-113">The **ColumnMapping** property of the **ChildElement2** column will be set to **MappingType.Element**.</span></span> <span data-ttu-id="ff74b-114">**Element1_Id**資料行會設定為**Element1**資料表的主要索引鍵。</span><span class="sxs-lookup"><span data-stu-id="ff74b-114">The **Element1_Id** column will be set as the primary key of the **Element1** table.</span></span>  
  
 <span data-ttu-id="ff74b-115">**ChildElement1**資料表會有三個數據行: **attr1**、 **attr2**和**Element1_Id**。</span><span class="sxs-lookup"><span data-stu-id="ff74b-115">The **ChildElement1** table will have three columns: **attr1**, **attr2** and **Element1_Id**.</span></span> <span data-ttu-id="ff74b-116">**Attr1**和**attr2**資料行的**ColumnMapping**屬性將會設定為**MappingType. Attribute**。</span><span class="sxs-lookup"><span data-stu-id="ff74b-116">The **ColumnMapping** property for the **attr1** and **attr2** columns will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="ff74b-117">**Element1_Id**資料行的**ColumnMapping**屬性會設定為**MappingType。 Hidden**。</span><span class="sxs-lookup"><span data-stu-id="ff74b-117">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span>  
  
 <span data-ttu-id="ff74b-118">會使用兩個數據表中的**Element1_Id**資料行來建立**DataRelation**和**ForeignKeyConstraint** 。</span><span class="sxs-lookup"><span data-stu-id="ff74b-118">A **DataRelation** and **ForeignKeyConstraint** will be created using the **Element1_Id** columns from both tables.</span></span>  
  
 <span data-ttu-id="ff74b-119">**集中**DocumentElement</span><span class="sxs-lookup"><span data-stu-id="ff74b-119">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="ff74b-120">**目錄**Element1</span><span class="sxs-lookup"><span data-stu-id="ff74b-120">**Table:** Element1</span></span>  
  
|<span data-ttu-id="ff74b-121">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="ff74b-121">Element1_Id</span></span>|<span data-ttu-id="ff74b-122">ChildElement2</span><span class="sxs-lookup"><span data-stu-id="ff74b-122">ChildElement2</span></span>|  
|------------------|-------------------|  
|<span data-ttu-id="ff74b-123">0</span><span class="sxs-lookup"><span data-stu-id="ff74b-123">0</span></span>|<span data-ttu-id="ff74b-124">Text2</span><span class="sxs-lookup"><span data-stu-id="ff74b-124">Text2</span></span>|  
  
 <span data-ttu-id="ff74b-125">**目錄**ChildElement1</span><span class="sxs-lookup"><span data-stu-id="ff74b-125">**Table:** ChildElement1</span></span>  
  
|<span data-ttu-id="ff74b-126">attr1</span><span class="sxs-lookup"><span data-stu-id="ff74b-126">attr1</span></span>|<span data-ttu-id="ff74b-127">attr2</span><span class="sxs-lookup"><span data-stu-id="ff74b-127">attr2</span></span>|<span data-ttu-id="ff74b-128">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="ff74b-128">Element1_Id</span></span>|  
|-----------|-----------|------------------|  
|<span data-ttu-id="ff74b-129">value1</span><span class="sxs-lookup"><span data-stu-id="ff74b-129">value1</span></span>|<span data-ttu-id="ff74b-130">value2</span><span class="sxs-lookup"><span data-stu-id="ff74b-130">value2</span></span>|<span data-ttu-id="ff74b-131">0</span><span class="sxs-lookup"><span data-stu-id="ff74b-131">0</span></span>|  
  
 <span data-ttu-id="ff74b-132">**DataRelation**Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="ff74b-132">**DataRelation:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="ff74b-133">**ParentTable**Element1</span><span class="sxs-lookup"><span data-stu-id="ff74b-133">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="ff74b-134">**ParentColumn**Element1_Id</span><span class="sxs-lookup"><span data-stu-id="ff74b-134">**ParentColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="ff74b-135">**ChildTable**ChildElement1</span><span class="sxs-lookup"><span data-stu-id="ff74b-135">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="ff74b-136">**ChildColumn**Element1_Id</span><span class="sxs-lookup"><span data-stu-id="ff74b-136">**ChildColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="ff74b-137">**嵌套**True</span><span class="sxs-lookup"><span data-stu-id="ff74b-137">**Nested:** True</span></span>  
  
 <span data-ttu-id="ff74b-138">**ForeignKeyConstraint**Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="ff74b-138">**ForeignKeyConstraint:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="ff74b-139">**排**Element1_Id</span><span class="sxs-lookup"><span data-stu-id="ff74b-139">**Column:** Element1_Id</span></span>  
  
 <span data-ttu-id="ff74b-140">**ParentTable**Element1</span><span class="sxs-lookup"><span data-stu-id="ff74b-140">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="ff74b-141">**ChildTable**ChildElement1</span><span class="sxs-lookup"><span data-stu-id="ff74b-141">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="ff74b-142">**DeleteRule**Cascade</span><span class="sxs-lookup"><span data-stu-id="ff74b-142">**DeleteRule:** Cascade</span></span>  
  
 <span data-ttu-id="ff74b-143">**AcceptRejectRule**無</span><span class="sxs-lookup"><span data-stu-id="ff74b-143">**AcceptRejectRule:** None</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff74b-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff74b-144">See also</span></span>

- [<span data-ttu-id="ff74b-145">從 XML 推斷資料集關聯式結構</span><span class="sxs-lookup"><span data-stu-id="ff74b-145">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="ff74b-146">從 XML 載入資料集</span><span class="sxs-lookup"><span data-stu-id="ff74b-146">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="ff74b-147">從 XML 載入資料集結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="ff74b-147">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="ff74b-148">巢狀 DataRelation</span><span class="sxs-lookup"><span data-stu-id="ff74b-148">Nesting DataRelations</span></span>](nesting-datarelations.md)
- [<span data-ttu-id="ff74b-149">在 DataSet 中使用 XML</span><span class="sxs-lookup"><span data-stu-id="ff74b-149">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="ff74b-150">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="ff74b-150">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="ff74b-151">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="ff74b-151">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
