---
title: "推斷項目文字"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 789799e5-716f-459f-a168-76c5cf22178b
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 239c70ca0e7f8894b988f17d248b2e5b3b98bf6a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="inferring-element-text"></a><span data-ttu-id="e61c2-102">推斷項目文字</span><span class="sxs-lookup"><span data-stu-id="e61c2-102">Inferring Element Text</span></span>
<span data-ttu-id="e61c2-103">如果項目包含文字，而且沒有任何子項目，來推斷為資料表 （具有屬性的項目） 或重複的項目，例如新的資料行名稱**TableName_Text**將加入至項目推斷的資料表。</span><span class="sxs-lookup"><span data-stu-id="e61c2-103">If an element contains text and has no child elements to be inferred as tables (such as elements with attributes or repeated elements), a new column with the name **TableName_Text** will be added to the table that is inferred for the element.</span></span> <span data-ttu-id="e61c2-104">項目中包含的文字會加入資料表中的資料列，並儲存在新資料行內。</span><span class="sxs-lookup"><span data-stu-id="e61c2-104">The text contained in the element will be added to a row in the table and stored in the new column.</span></span> <span data-ttu-id="e61c2-105">**ColumnMapping**新資料行的屬性會設定為**MappingType.SimpleContent**。</span><span class="sxs-lookup"><span data-stu-id="e61c2-105">The **ColumnMapping** property of the new column will be set to **MappingType.SimpleContent**.</span></span>  
  
 <span data-ttu-id="e61c2-106">例如，請考量下列 XML。</span><span class="sxs-lookup"><span data-stu-id="e61c2-106">For example, consider the following XML.</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="e61c2-107">推斷程序將會產生名為的資料表**Element1**與兩個資料行： **attr1**和**Element1_Text**。</span><span class="sxs-lookup"><span data-stu-id="e61c2-107">The inference process will produce a table named **Element1** with two columns: **attr1** and **Element1_Text**.</span></span> <span data-ttu-id="e61c2-108">**ColumnMapping**屬性**attr1**資料行設定**MappingType.Attribute**。</span><span class="sxs-lookup"><span data-stu-id="e61c2-108">The **ColumnMapping** property of the **attr1** column will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="e61c2-109">**ColumnMapping**屬性**Element1_Text**資料行設定**MappingType.SimpleContent**。</span><span class="sxs-lookup"><span data-stu-id="e61c2-109">The **ColumnMapping** property of the **Element1_Text** column will be set to **MappingType.SimpleContent**.</span></span>  
  
 <span data-ttu-id="e61c2-110">**資料集：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="e61c2-110">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="e61c2-111">**Table:** Element1</span><span class="sxs-lookup"><span data-stu-id="e61c2-111">**Table:** Element1</span></span>  
  
|<span data-ttu-id="e61c2-112">attr1</span><span class="sxs-lookup"><span data-stu-id="e61c2-112">attr1</span></span>|<span data-ttu-id="e61c2-113">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="e61c2-113">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="e61c2-114">value1</span><span class="sxs-lookup"><span data-stu-id="e61c2-114">value1</span></span>|<span data-ttu-id="e61c2-115">Text1</span><span class="sxs-lookup"><span data-stu-id="e61c2-115">Text1</span></span>|  
  
 <span data-ttu-id="e61c2-116">如果項目包含文字，但是它的項目子系也包含文字，則不會有資料行加入資料表來儲存項目中包含的文字。</span><span class="sxs-lookup"><span data-stu-id="e61c2-116">If an element contains text, but also has child elements that contain text, a column will not be added to the table to store the text contained in the element.</span></span> <span data-ttu-id="e61c2-117">包含在項目中的文字會被忽略，而項目子系中的文字會被包含在資料表的資料列內。</span><span class="sxs-lookup"><span data-stu-id="e61c2-117">The text contained in the element will be ignored, while the text in the child elements is included in a row in the table.</span></span> <span data-ttu-id="e61c2-118">例如，請考量下列 XML。</span><span class="sxs-lookup"><span data-stu-id="e61c2-118">For example, consider the following XML.</span></span>  
  
```xml  
<Element1>  
  Text1  
  <ChildElement1>Text2</ChildElement1>  
  Text3  
</Element1>  
```  
  
 <span data-ttu-id="e61c2-119">推斷程序將會產生名為的資料表**Element1**包含一個資料行名為**ChildElement1**。</span><span class="sxs-lookup"><span data-stu-id="e61c2-119">The inference process will produce a table named **Element1** with one column named **ChildElement1**.</span></span> <span data-ttu-id="e61c2-120">文字**ChildElement1**項目將會包含在資料表中的資料列。</span><span class="sxs-lookup"><span data-stu-id="e61c2-120">The text for the **ChildElement1** element will be included in a row in the table.</span></span> <span data-ttu-id="e61c2-121">其他文字則被忽略。</span><span class="sxs-lookup"><span data-stu-id="e61c2-121">The other text will be ignored.</span></span> <span data-ttu-id="e61c2-122">**ColumnMapping**屬性**ChildElement1**資料行設定**MappingType.Element**。</span><span class="sxs-lookup"><span data-stu-id="e61c2-122">The **ColumnMapping** property of the **ChildElement1** column will be set to **MappingType.Element**.</span></span>  
  
 <span data-ttu-id="e61c2-123">**資料集：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="e61c2-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="e61c2-124">**Table:** Element1</span><span class="sxs-lookup"><span data-stu-id="e61c2-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="e61c2-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="e61c2-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="e61c2-126">Text2</span><span class="sxs-lookup"><span data-stu-id="e61c2-126">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e61c2-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="e61c2-127">See Also</span></span>  
 [<span data-ttu-id="e61c2-128">從 XML 推斷資料集關聯式結構</span><span class="sxs-lookup"><span data-stu-id="e61c2-128">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="e61c2-129">從 XML 載入資料集</span><span class="sxs-lookup"><span data-stu-id="e61c2-129">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="e61c2-130">從 XML 載入資料集結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="e61c2-130">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="e61c2-131">在 DataSet 中使用 XML</span><span class="sxs-lookup"><span data-stu-id="e61c2-131">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="e61c2-132">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="e61c2-132">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="e61c2-133">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="e61c2-133">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
