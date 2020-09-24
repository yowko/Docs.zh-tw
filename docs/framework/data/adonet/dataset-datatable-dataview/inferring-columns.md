---
title: 推斷資料行
ms.date: 03/30/2017
ms.assetid: 0e022699-c922-454c-93e2-957dd7e7247a
ms.openlocfilehash: 45d27b78b5d83d333c16192e172e7b7e3dd88c10
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164697"
---
# <a name="inferring-columns"></a><span data-ttu-id="0a6bd-102">推斷資料行</span><span class="sxs-lookup"><span data-stu-id="0a6bd-102">Inferring Columns</span></span>

<span data-ttu-id="0a6bd-103">ADO.NET 從 XML 文件中判斷要將哪些項目推斷成 <xref:System.Data.DataSet> 的資料表後，接著就會推斷這些資料表的資料行。</span><span class="sxs-lookup"><span data-stu-id="0a6bd-103">After ADO.NET has determined from an XML document which elements to infer as tables for a <xref:System.Data.DataSet>, it then infers the columns for those tables.</span></span> <span data-ttu-id="0a6bd-104">ADO.NET 2.0 引進了新的架構推斷引擎，可推斷每個 **simpleType** 專案的強型別資料型別。</span><span class="sxs-lookup"><span data-stu-id="0a6bd-104">ADO.NET 2.0 introduced a new schema inference engine that infers a strongly typed data type for each **simpleType** element.</span></span> <span data-ttu-id="0a6bd-105">在先前的版本中，推斷的 **simpleType** 專案的資料類型一律為 **xsd： string**。</span><span class="sxs-lookup"><span data-stu-id="0a6bd-105">In previous versions, the data type of an inferred **simpleType** element was always **xsd:string**.</span></span>  
  
## <a name="migration-and-backward-compatibility"></a><span data-ttu-id="0a6bd-106">移轉和回溯相容性</span><span class="sxs-lookup"><span data-stu-id="0a6bd-106">Migration and Backward Compatibility</span></span>  

 <span data-ttu-id="0a6bd-107">**ReadXml**方法會採用**InferSchema**類型的引數。</span><span class="sxs-lookup"><span data-stu-id="0a6bd-107">The **ReadXml** method takes an argument of type **InferSchema**.</span></span> <span data-ttu-id="0a6bd-108">這個引數可讓您指定與舊版本相容的推斷行為。</span><span class="sxs-lookup"><span data-stu-id="0a6bd-108">This argument allows you to specify inference behavior compatible with previous versions.</span></span> <span data-ttu-id="0a6bd-109">下表顯示 **InferSchema** 列舉的可用值。</span><span class="sxs-lookup"><span data-stu-id="0a6bd-109">The available values for the **InferSchema** enumeration are shown in the following table.</span></span>  
  
 <xref:System.Data.XmlReadMode.InferSchema>  
 <span data-ttu-id="0a6bd-110">將簡單型別永遠推斷為 <xref:System.String>，以提供回溯相容性 (Backward Compatibility)。</span><span class="sxs-lookup"><span data-stu-id="0a6bd-110">Provides backward compatibility by always inferring a simple type as <xref:System.String>.</span></span>  
  
 <xref:System.Data.XmlReadMode.InferTypedSchema>  
 <span data-ttu-id="0a6bd-111">推斷強型別資料型別。</span><span class="sxs-lookup"><span data-stu-id="0a6bd-111">Infers a strongly typed data type.</span></span> <span data-ttu-id="0a6bd-112">若用於 <xref:System.Data.DataTable>，則會擲回例外狀況 (Exception)。</span><span class="sxs-lookup"><span data-stu-id="0a6bd-112">Throws an exception if used with a <xref:System.Data.DataTable>.</span></span>  
  
 <xref:System.Data.XmlReadMode.IgnoreSchema>  
 <span data-ttu-id="0a6bd-113">忽略任何內嵌結構描述，並將資料讀入現有的 <xref:System.Data.DataSet> 結構描述中。</span><span class="sxs-lookup"><span data-stu-id="0a6bd-113">Ignores any inline schema and reads data into the existing <xref:System.Data.DataSet> schema.</span></span>  
  
## <a name="attributes"></a><span data-ttu-id="0a6bd-114">屬性</span><span class="sxs-lookup"><span data-stu-id="0a6bd-114">Attributes</span></span>  

 <span data-ttu-id="0a6bd-115">如 [推斷資料表](inferring-tables.md)中所定義，具有屬性的元素將會推斷為數據表。</span><span class="sxs-lookup"><span data-stu-id="0a6bd-115">As defined in [Inferring Tables](inferring-tables.md), an element with attributes will be inferred as a table.</span></span> <span data-ttu-id="0a6bd-116">然後，該項目的屬性會推斷為資料表的資料行。</span><span class="sxs-lookup"><span data-stu-id="0a6bd-116">The attributes of that element will then be inferred as columns for the table.</span></span> <span data-ttu-id="0a6bd-117">資料行的 **ColumnMapping** 屬性將會設定為 **MappingType**，以確保將架構寫回 XML 時，資料行名稱會寫入為屬性。</span><span class="sxs-lookup"><span data-stu-id="0a6bd-117">The **ColumnMapping** property of the columns will be set to **MappingType.Attribute**, to ensure that the column names will be written as attributes if the schema is written back to XML.</span></span> <span data-ttu-id="0a6bd-118">屬性的值儲存在資料表的資料列中。</span><span class="sxs-lookup"><span data-stu-id="0a6bd-118">The values of the attributes are stored in a row in the table.</span></span> <span data-ttu-id="0a6bd-119">例如，請考量下列 XML：</span><span class="sxs-lookup"><span data-stu-id="0a6bd-119">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="0a6bd-120">推斷進程會產生名為 **Element1** 的資料表，其中包含兩個數據行： **attr1** 和 **attr2**。</span><span class="sxs-lookup"><span data-stu-id="0a6bd-120">The inference process will produce a table named **Element1** with two columns, **attr1** and **attr2**.</span></span> <span data-ttu-id="0a6bd-121">這兩個數據行的 **ColumnMapping** 屬性將會設定為 **MappingType. Attribute**。</span><span class="sxs-lookup"><span data-stu-id="0a6bd-121">The **ColumnMapping** property of both columns will be set to **MappingType.Attribute**.</span></span>  
  
 <span data-ttu-id="0a6bd-122">**資料集：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="0a6bd-122">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="0a6bd-123">**資料表：** Element1</span><span class="sxs-lookup"><span data-stu-id="0a6bd-123">**Table:** Element1</span></span>  
  
|<span data-ttu-id="0a6bd-124">attr1</span><span class="sxs-lookup"><span data-stu-id="0a6bd-124">attr1</span></span>|<span data-ttu-id="0a6bd-125">attr2</span><span class="sxs-lookup"><span data-stu-id="0a6bd-125">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="0a6bd-126">value1</span><span class="sxs-lookup"><span data-stu-id="0a6bd-126">value1</span></span>|<span data-ttu-id="0a6bd-127">value2</span><span class="sxs-lookup"><span data-stu-id="0a6bd-127">value2</span></span>|  
  
## <a name="elements-without-attributes-or-child-elements"></a><span data-ttu-id="0a6bd-128">沒有屬性或項目子系的項目</span><span class="sxs-lookup"><span data-stu-id="0a6bd-128">Elements Without Attributes or Child Elements</span></span>  

 <span data-ttu-id="0a6bd-129">如果項目沒有項目子系或屬性，則會推斷為資料行。</span><span class="sxs-lookup"><span data-stu-id="0a6bd-129">If an element has no child elements or attributes, it will be inferred as a column.</span></span> <span data-ttu-id="0a6bd-130">資料行的 **ColumnMapping** 屬性將會設定為 **MappingType. Element**。</span><span class="sxs-lookup"><span data-stu-id="0a6bd-130">The **ColumnMapping** property of the column will be set to **MappingType.Element**.</span></span> <span data-ttu-id="0a6bd-131">項目子系的文字儲存在資料表的資料列中。</span><span class="sxs-lookup"><span data-stu-id="0a6bd-131">The text for child elements is stored in a row in the table.</span></span> <span data-ttu-id="0a6bd-132">例如，請考量下列 XML：</span><span class="sxs-lookup"><span data-stu-id="0a6bd-132">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="0a6bd-133">推斷進程會產生名為 **Element1** 的資料表，其中包含兩個數據行： **ChildElement1** 和 **ChildElement2**。</span><span class="sxs-lookup"><span data-stu-id="0a6bd-133">The inference process will produce a table named **Element1** with two columns, **ChildElement1** and **ChildElement2**.</span></span> <span data-ttu-id="0a6bd-134">這兩個數據行的 **ColumnMapping** 屬性將會設定為 **MappingType. Element**。</span><span class="sxs-lookup"><span data-stu-id="0a6bd-134">The **ColumnMapping** property of both columns will be set to **MappingType.Element**.</span></span>  
  
 <span data-ttu-id="0a6bd-135">**資料集：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="0a6bd-135">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="0a6bd-136">**資料表：** Element1</span><span class="sxs-lookup"><span data-stu-id="0a6bd-136">**Table:** Element1</span></span>  
  
|<span data-ttu-id="0a6bd-137">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="0a6bd-137">ChildElement1</span></span>|<span data-ttu-id="0a6bd-138">ChildElement2</span><span class="sxs-lookup"><span data-stu-id="0a6bd-138">ChildElement2</span></span>|  
|-------------------|-------------------|  
|<span data-ttu-id="0a6bd-139">Text1</span><span class="sxs-lookup"><span data-stu-id="0a6bd-139">Text1</span></span>|<span data-ttu-id="0a6bd-140">Text2</span><span class="sxs-lookup"><span data-stu-id="0a6bd-140">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0a6bd-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a6bd-141">See also</span></span>

- [<span data-ttu-id="0a6bd-142">從 XML 推斷資料集關聯式結構</span><span class="sxs-lookup"><span data-stu-id="0a6bd-142">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="0a6bd-143">從 XML 載入資料集</span><span class="sxs-lookup"><span data-stu-id="0a6bd-143">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="0a6bd-144">從 XML 載入資料集結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="0a6bd-144">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="0a6bd-145">在資料集中使用 XML</span><span class="sxs-lookup"><span data-stu-id="0a6bd-145">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="0a6bd-146">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="0a6bd-146">DataSets, DataTables, and DataViews</span></span>](index.md)
- <span data-ttu-id="0a6bd-147">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="0a6bd-147">[ADO.NET Overview](../ado-net-overview.md)</span></span>
