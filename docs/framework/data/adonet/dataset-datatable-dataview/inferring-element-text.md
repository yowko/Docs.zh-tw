---
title: 推斷項目文字
ms.date: 03/30/2017
ms.assetid: 789799e5-716f-459f-a168-76c5cf22178b
ms.openlocfilehash: 6ffe8f2fbf01fbe8dfa9d78f3dfb9e39b6e80b16
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59224958"
---
# <a name="inferring-element-text"></a><span data-ttu-id="c8079-102">推斷項目文字</span><span class="sxs-lookup"><span data-stu-id="c8079-102">Inferring Element Text</span></span>
<span data-ttu-id="c8079-103">如果項目包含文字，而且沒有任何子項目，來推斷為資料表 （具有屬性的項目） 或重複的項目，例如新的資料行同名**TableName_Text**會加入項目，推斷的資料表。</span><span class="sxs-lookup"><span data-stu-id="c8079-103">If an element contains text and has no child elements to be inferred as tables (such as elements with attributes or repeated elements), a new column with the name **TableName_Text** will be added to the table that is inferred for the element.</span></span> <span data-ttu-id="c8079-104">項目中包含的文字會加入資料表中的資料列，並儲存在新資料行內。</span><span class="sxs-lookup"><span data-stu-id="c8079-104">The text contained in the element will be added to a row in the table and stored in the new column.</span></span> <span data-ttu-id="c8079-105">**ColumnMapping**的新資料行的屬性會設定為**MappingType.SimpleContent**。</span><span class="sxs-lookup"><span data-stu-id="c8079-105">The **ColumnMapping** property of the new column will be set to **MappingType.SimpleContent**.</span></span>  
  
 <span data-ttu-id="c8079-106">例如，請考量下列 XML。</span><span class="sxs-lookup"><span data-stu-id="c8079-106">For example, consider the following XML.</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="c8079-107">推斷程序會產生一個名為資料表**Element1**兩個資料行： **attr1**並**Element1_Text**。</span><span class="sxs-lookup"><span data-stu-id="c8079-107">The inference process will produce a table named **Element1** with two columns: **attr1** and **Element1_Text**.</span></span> <span data-ttu-id="c8079-108">**ColumnMapping**屬性**attr1**資料行都會設定為**MappingType.Attribute**。</span><span class="sxs-lookup"><span data-stu-id="c8079-108">The **ColumnMapping** property of the **attr1** column will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="c8079-109">**ColumnMapping**屬性**Element1_Text**資料行都會設定為**MappingType.SimpleContent**。</span><span class="sxs-lookup"><span data-stu-id="c8079-109">The **ColumnMapping** property of the **Element1_Text** column will be set to **MappingType.SimpleContent**.</span></span>  
  
 <span data-ttu-id="c8079-110">**資料集：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="c8079-110">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="c8079-111">**資料表：** Element1</span><span class="sxs-lookup"><span data-stu-id="c8079-111">**Table:** Element1</span></span>  
  
|<span data-ttu-id="c8079-112">attr1</span><span class="sxs-lookup"><span data-stu-id="c8079-112">attr1</span></span>|<span data-ttu-id="c8079-113">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="c8079-113">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="c8079-114">value1</span><span class="sxs-lookup"><span data-stu-id="c8079-114">value1</span></span>|<span data-ttu-id="c8079-115">Text1</span><span class="sxs-lookup"><span data-stu-id="c8079-115">Text1</span></span>|  
  
 <span data-ttu-id="c8079-116">如果項目包含文字，但是它的項目子系也包含文字，則不會有資料行加入資料表來儲存項目中包含的文字。</span><span class="sxs-lookup"><span data-stu-id="c8079-116">If an element contains text, but also has child elements that contain text, a column will not be added to the table to store the text contained in the element.</span></span> <span data-ttu-id="c8079-117">包含在項目中的文字會被忽略，而項目子系中的文字會被包含在資料表的資料列內。</span><span class="sxs-lookup"><span data-stu-id="c8079-117">The text contained in the element will be ignored, while the text in the child elements is included in a row in the table.</span></span> <span data-ttu-id="c8079-118">例如，請考量下列 XML。</span><span class="sxs-lookup"><span data-stu-id="c8079-118">For example, consider the following XML.</span></span>  
  
```xml  
<Element1>  
  Text1  
  <ChildElement1>Text2</ChildElement1>  
  Text3  
</Element1>  
```  
  
 <span data-ttu-id="c8079-119">推斷程序會產生一個名為資料表**Element1**的資料行**ChildElement1**。</span><span class="sxs-lookup"><span data-stu-id="c8079-119">The inference process will produce a table named **Element1** with one column named **ChildElement1**.</span></span> <span data-ttu-id="c8079-120">文字**ChildElement1**項目將會包含在資料表中的資料列。</span><span class="sxs-lookup"><span data-stu-id="c8079-120">The text for the **ChildElement1** element will be included in a row in the table.</span></span> <span data-ttu-id="c8079-121">其他文字則被忽略。</span><span class="sxs-lookup"><span data-stu-id="c8079-121">The other text will be ignored.</span></span> <span data-ttu-id="c8079-122">**ColumnMapping**屬性**ChildElement1**資料行都會設定為**MappingType.Element**。</span><span class="sxs-lookup"><span data-stu-id="c8079-122">The **ColumnMapping** property of the **ChildElement1** column will be set to **MappingType.Element**.</span></span>  
  
 <span data-ttu-id="c8079-123">**資料集：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="c8079-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="c8079-124">**資料表：** Element1</span><span class="sxs-lookup"><span data-stu-id="c8079-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="c8079-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="c8079-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="c8079-126">Text2</span><span class="sxs-lookup"><span data-stu-id="c8079-126">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c8079-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8079-127">See also</span></span>

- [<span data-ttu-id="c8079-128">從 XML 推斷資料集關聯式結構</span><span class="sxs-lookup"><span data-stu-id="c8079-128">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="c8079-129">從 XML 載入資料集</span><span class="sxs-lookup"><span data-stu-id="c8079-129">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [<span data-ttu-id="c8079-130">從 XML 載入資料集結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="c8079-130">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="c8079-131">在 DataSet 中使用 XML</span><span class="sxs-lookup"><span data-stu-id="c8079-131">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [<span data-ttu-id="c8079-132">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="c8079-132">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="c8079-133">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="c8079-133">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
