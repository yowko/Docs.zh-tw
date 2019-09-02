---
title: 推斷項目文字
ms.date: 03/30/2017
ms.assetid: 789799e5-716f-459f-a168-76c5cf22178b
ms.openlocfilehash: d8d64c0cbb0aecf736a54fa6816e286ab7efa191
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203536"
---
# <a name="inferring-element-text"></a><span data-ttu-id="a5791-102">推斷項目文字</span><span class="sxs-lookup"><span data-stu-id="a5791-102">Inferring Element Text</span></span>
<span data-ttu-id="a5791-103">如果專案包含文字, 且沒有任何子專案要推斷為數據表 (例如具有屬性或重複元素的專案), 則會將名稱為**TableName_Text**的新資料行加入至為專案推斷的資料表。</span><span class="sxs-lookup"><span data-stu-id="a5791-103">If an element contains text and has no child elements to be inferred as tables (such as elements with attributes or repeated elements), a new column with the name **TableName_Text** will be added to the table that is inferred for the element.</span></span> <span data-ttu-id="a5791-104">項目中包含的文字會加入資料表中的資料列，並儲存在新資料行內。</span><span class="sxs-lookup"><span data-stu-id="a5791-104">The text contained in the element will be added to a row in the table and stored in the new column.</span></span> <span data-ttu-id="a5791-105">新資料行的**ColumnMapping**屬性會設定為**MappingType**。</span><span class="sxs-lookup"><span data-stu-id="a5791-105">The **ColumnMapping** property of the new column will be set to **MappingType.SimpleContent**.</span></span>  
  
 <span data-ttu-id="a5791-106">例如，請考量下列 XML。</span><span class="sxs-lookup"><span data-stu-id="a5791-106">For example, consider the following XML.</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="a5791-107">推斷進程會產生名為**Element1**的資料表, 其中包含兩個數據行: **attr1**和**Element1_Text**。</span><span class="sxs-lookup"><span data-stu-id="a5791-107">The inference process will produce a table named **Element1** with two columns: **attr1** and **Element1_Text**.</span></span> <span data-ttu-id="a5791-108">**Attr1**資料行的**ColumnMapping**屬性會設定為**MappingType. Attribute**。</span><span class="sxs-lookup"><span data-stu-id="a5791-108">The **ColumnMapping** property of the **attr1** column will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="a5791-109">**Element1_Text**資料行的**ColumnMapping**屬性會設定為**MappingType。**</span><span class="sxs-lookup"><span data-stu-id="a5791-109">The **ColumnMapping** property of the **Element1_Text** column will be set to **MappingType.SimpleContent**.</span></span>  
  
 <span data-ttu-id="a5791-110">**集中**DocumentElement</span><span class="sxs-lookup"><span data-stu-id="a5791-110">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="a5791-111">**目錄**Element1</span><span class="sxs-lookup"><span data-stu-id="a5791-111">**Table:** Element1</span></span>  
  
|<span data-ttu-id="a5791-112">attr1</span><span class="sxs-lookup"><span data-stu-id="a5791-112">attr1</span></span>|<span data-ttu-id="a5791-113">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="a5791-113">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="a5791-114">value1</span><span class="sxs-lookup"><span data-stu-id="a5791-114">value1</span></span>|<span data-ttu-id="a5791-115">Text1</span><span class="sxs-lookup"><span data-stu-id="a5791-115">Text1</span></span>|  
  
 <span data-ttu-id="a5791-116">如果項目包含文字，但是它的項目子系也包含文字，則不會有資料行加入資料表來儲存項目中包含的文字。</span><span class="sxs-lookup"><span data-stu-id="a5791-116">If an element contains text, but also has child elements that contain text, a column will not be added to the table to store the text contained in the element.</span></span> <span data-ttu-id="a5791-117">包含在項目中的文字會被忽略，而項目子系中的文字會被包含在資料表的資料列內。</span><span class="sxs-lookup"><span data-stu-id="a5791-117">The text contained in the element will be ignored, while the text in the child elements is included in a row in the table.</span></span> <span data-ttu-id="a5791-118">例如，請考量下列 XML。</span><span class="sxs-lookup"><span data-stu-id="a5791-118">For example, consider the following XML.</span></span>  
  
```xml  
<Element1>  
  Text1  
  <ChildElement1>Text2</ChildElement1>  
  Text3  
</Element1>  
```  
  
 <span data-ttu-id="a5791-119">推斷程式會產生名為**Element1**的資料表, 其中有一個名為**ChildElement1**的資料行。</span><span class="sxs-lookup"><span data-stu-id="a5791-119">The inference process will produce a table named **Element1** with one column named **ChildElement1**.</span></span> <span data-ttu-id="a5791-120">**ChildElement1**元素的文字會包含在資料表的資料列中。</span><span class="sxs-lookup"><span data-stu-id="a5791-120">The text for the **ChildElement1** element will be included in a row in the table.</span></span> <span data-ttu-id="a5791-121">其他文字則被忽略。</span><span class="sxs-lookup"><span data-stu-id="a5791-121">The other text will be ignored.</span></span> <span data-ttu-id="a5791-122">**ChildElement1**資料行的**ColumnMapping**屬性會設定為**MappingType。**</span><span class="sxs-lookup"><span data-stu-id="a5791-122">The **ColumnMapping** property of the **ChildElement1** column will be set to **MappingType.Element**.</span></span>  
  
 <span data-ttu-id="a5791-123">**集中**DocumentElement</span><span class="sxs-lookup"><span data-stu-id="a5791-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="a5791-124">**目錄**Element1</span><span class="sxs-lookup"><span data-stu-id="a5791-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="a5791-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="a5791-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="a5791-126">Text2</span><span class="sxs-lookup"><span data-stu-id="a5791-126">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a5791-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5791-127">See also</span></span>

- [<span data-ttu-id="a5791-128">從 XML 推斷資料集關聯式結構</span><span class="sxs-lookup"><span data-stu-id="a5791-128">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="a5791-129">從 XML 載入資料集</span><span class="sxs-lookup"><span data-stu-id="a5791-129">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="a5791-130">從 XML 載入資料集結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="a5791-130">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="a5791-131">在 DataSet 中使用 XML</span><span class="sxs-lookup"><span data-stu-id="a5791-131">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="a5791-132">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="a5791-132">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="a5791-133">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="a5791-133">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
