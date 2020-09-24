---
title: 推斷項目文字
ms.date: 03/30/2017
ms.assetid: 789799e5-716f-459f-a168-76c5cf22178b
ms.openlocfilehash: 7389e24f39902edf041c3cd3502303b17fd008ba
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164684"
---
# <a name="inferring-element-text"></a><span data-ttu-id="4ebe2-102">推斷項目文字</span><span class="sxs-lookup"><span data-stu-id="4ebe2-102">Inferring Element Text</span></span>

<span data-ttu-id="4ebe2-103">如果專案包含文字，而且沒有要推斷為數據表的子專案 (例如) 具有屬性或重複專案的元素，則會將名稱 **TableName_Text** 的新資料行加入至針對元素推斷的資料表中。</span><span class="sxs-lookup"><span data-stu-id="4ebe2-103">If an element contains text and has no child elements to be inferred as tables (such as elements with attributes or repeated elements), a new column with the name **TableName_Text** will be added to the table that is inferred for the element.</span></span> <span data-ttu-id="4ebe2-104">項目中包含的文字會加入資料表中的資料列，並儲存在新資料行內。</span><span class="sxs-lookup"><span data-stu-id="4ebe2-104">The text contained in the element will be added to a row in the table and stored in the new column.</span></span> <span data-ttu-id="4ebe2-105">新資料行的**ColumnMapping**屬性將會設定為**MappingType。**</span><span class="sxs-lookup"><span data-stu-id="4ebe2-105">The **ColumnMapping** property of the new column will be set to **MappingType.SimpleContent**.</span></span>  
  
 <span data-ttu-id="4ebe2-106">例如，請考量下列 XML。</span><span class="sxs-lookup"><span data-stu-id="4ebe2-106">For example, consider the following XML.</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="4ebe2-107">推斷進程會產生名為 **Element1** 的資料表，其中包含兩個數據行： **attr1** 和 **Element1_Text**。</span><span class="sxs-lookup"><span data-stu-id="4ebe2-107">The inference process will produce a table named **Element1** with two columns: **attr1** and **Element1_Text**.</span></span> <span data-ttu-id="4ebe2-108">**Attr1**資料行的**ColumnMapping**屬性將會設定為**MappingType. Attribute**。</span><span class="sxs-lookup"><span data-stu-id="4ebe2-108">The **ColumnMapping** property of the **attr1** column will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="4ebe2-109">**Element1_Text**資料行的**ColumnMapping**屬性將會設定為**MappingType。**</span><span class="sxs-lookup"><span data-stu-id="4ebe2-109">The **ColumnMapping** property of the **Element1_Text** column will be set to **MappingType.SimpleContent**.</span></span>  
  
 <span data-ttu-id="4ebe2-110">**資料集：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="4ebe2-110">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="4ebe2-111">**資料表：** Element1</span><span class="sxs-lookup"><span data-stu-id="4ebe2-111">**Table:** Element1</span></span>  
  
|<span data-ttu-id="4ebe2-112">attr1</span><span class="sxs-lookup"><span data-stu-id="4ebe2-112">attr1</span></span>|<span data-ttu-id="4ebe2-113">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="4ebe2-113">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="4ebe2-114">value1</span><span class="sxs-lookup"><span data-stu-id="4ebe2-114">value1</span></span>|<span data-ttu-id="4ebe2-115">Text1</span><span class="sxs-lookup"><span data-stu-id="4ebe2-115">Text1</span></span>|  
  
 <span data-ttu-id="4ebe2-116">如果項目包含文字，但是它的項目子系也包含文字，則不會有資料行加入資料表來儲存項目中包含的文字。</span><span class="sxs-lookup"><span data-stu-id="4ebe2-116">If an element contains text, but also has child elements that contain text, a column will not be added to the table to store the text contained in the element.</span></span> <span data-ttu-id="4ebe2-117">包含在項目中的文字會被忽略，而項目子系中的文字會被包含在資料表的資料列內。</span><span class="sxs-lookup"><span data-stu-id="4ebe2-117">The text contained in the element will be ignored, while the text in the child elements is included in a row in the table.</span></span> <span data-ttu-id="4ebe2-118">例如，請考量下列 XML。</span><span class="sxs-lookup"><span data-stu-id="4ebe2-118">For example, consider the following XML.</span></span>  
  
```xml  
<Element1>  
  Text1  
  <ChildElement1>Text2</ChildElement1>  
  Text3  
</Element1>  
```  
  
 <span data-ttu-id="4ebe2-119">推斷進程會產生名為 **Element1** 的資料表，其中有一個名為 **ChildElement1**的資料行。</span><span class="sxs-lookup"><span data-stu-id="4ebe2-119">The inference process will produce a table named **Element1** with one column named **ChildElement1**.</span></span> <span data-ttu-id="4ebe2-120">**ChildElement1**元素的文字將會包含在資料表的資料列中。</span><span class="sxs-lookup"><span data-stu-id="4ebe2-120">The text for the **ChildElement1** element will be included in a row in the table.</span></span> <span data-ttu-id="4ebe2-121">其他文字則被忽略。</span><span class="sxs-lookup"><span data-stu-id="4ebe2-121">The other text will be ignored.</span></span> <span data-ttu-id="4ebe2-122">**ChildElement1**資料行的**ColumnMapping**屬性將會設定為**MappingType. Element**。</span><span class="sxs-lookup"><span data-stu-id="4ebe2-122">The **ColumnMapping** property of the **ChildElement1** column will be set to **MappingType.Element**.</span></span>  
  
 <span data-ttu-id="4ebe2-123">**資料集：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="4ebe2-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="4ebe2-124">**資料表：** Element1</span><span class="sxs-lookup"><span data-stu-id="4ebe2-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="4ebe2-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="4ebe2-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="4ebe2-126">Text2</span><span class="sxs-lookup"><span data-stu-id="4ebe2-126">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4ebe2-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ebe2-127">See also</span></span>

- [<span data-ttu-id="4ebe2-128">從 XML 推斷資料集關聯式結構</span><span class="sxs-lookup"><span data-stu-id="4ebe2-128">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="4ebe2-129">從 XML 載入資料集</span><span class="sxs-lookup"><span data-stu-id="4ebe2-129">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="4ebe2-130">從 XML 載入資料集結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="4ebe2-130">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="4ebe2-131">在資料集中使用 XML</span><span class="sxs-lookup"><span data-stu-id="4ebe2-131">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="4ebe2-132">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="4ebe2-132">DataSets, DataTables, and DataViews</span></span>](index.md)
- <span data-ttu-id="4ebe2-133">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="4ebe2-133">[ADO.NET Overview](../ado-net-overview.md)</span></span>
