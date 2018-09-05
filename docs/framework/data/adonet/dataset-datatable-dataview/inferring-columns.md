---
title: 推斷資料行
ms.date: 03/30/2017
ms.assetid: 0e022699-c922-454c-93e2-957dd7e7247a
ms.openlocfilehash: 56de4b4d6cf704473ec46957625ad1c376f595c2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43671406"
---
# <a name="inferring-columns"></a><span data-ttu-id="7c7ac-102">推斷資料行</span><span class="sxs-lookup"><span data-stu-id="7c7ac-102">Inferring Columns</span></span>
<span data-ttu-id="7c7ac-103">ADO.NET 從 XML 文件中判斷要將哪些項目推斷成 <xref:System.Data.DataSet> 的資料表後，接著就會推斷這些資料表的資料行。</span><span class="sxs-lookup"><span data-stu-id="7c7ac-103">After ADO.NET has determined from an XML document which elements to infer as tables for a <xref:System.Data.DataSet>, it then infers the columns for those tables.</span></span> <span data-ttu-id="7c7ac-104">ADO.NET 2.0 導入了新結構描述推斷引擎，可推斷每個強型別的資料型別**simpleType**項目。</span><span class="sxs-lookup"><span data-stu-id="7c7ac-104">ADO.NET 2.0 introduced a new schema inference engine that infers a strongly typed data type for each **simpleType** element.</span></span> <span data-ttu-id="7c7ac-105">在舊版中中的資料型別推斷**simpleType**項目向來**xsd: string**。</span><span class="sxs-lookup"><span data-stu-id="7c7ac-105">In previous versions, the data type of an inferred **simpleType** element was always **xsd:string**.</span></span>  
  
## <a name="migration-and-backward-compatibility"></a><span data-ttu-id="7c7ac-106">移轉和回溯相容性</span><span class="sxs-lookup"><span data-stu-id="7c7ac-106">Migration and Backward Compatibility</span></span>  
 <span data-ttu-id="7c7ac-107">**ReadXml**方法會採用類型的引數**InferSchema**。</span><span class="sxs-lookup"><span data-stu-id="7c7ac-107">The **ReadXml** method takes an argument of type **InferSchema**.</span></span> <span data-ttu-id="7c7ac-108">這個引數可讓您指定與舊版本相容的推斷行為。</span><span class="sxs-lookup"><span data-stu-id="7c7ac-108">This argument allows you to specify inference behavior compatible with previous versions.</span></span> <span data-ttu-id="7c7ac-109">可用的值**InferSchema**列舉型別會顯示下表中。</span><span class="sxs-lookup"><span data-stu-id="7c7ac-109">The available values for the **InferSchema** enumeration are shown in the following table.</span></span>  
  
 <xref:System.Data.XmlReadMode.InferSchema>  
 <span data-ttu-id="7c7ac-110">將簡單型別永遠推斷為 <xref:System.String>，以提供回溯相容性 (Backward Compatibility)。</span><span class="sxs-lookup"><span data-stu-id="7c7ac-110">Provides backward compatibility by always inferring a simple type as <xref:System.String>.</span></span>  
  
 <xref:System.Data.XmlReadMode.InferTypedSchema>  
 <span data-ttu-id="7c7ac-111">推斷強型別資料型別。</span><span class="sxs-lookup"><span data-stu-id="7c7ac-111">Infers a strongly typed data type.</span></span> <span data-ttu-id="7c7ac-112">若用於 <xref:System.Data.DataTable>，則會擲回例外狀況 (Exception)。</span><span class="sxs-lookup"><span data-stu-id="7c7ac-112">Throws an exception if used with a <xref:System.Data.DataTable>.</span></span>  
  
 <xref:System.Data.XmlReadMode.IgnoreSchema>  
 <span data-ttu-id="7c7ac-113">忽略任何內嵌結構描述，並將資料讀入現有的 <xref:System.Data.DataSet> 結構描述中。</span><span class="sxs-lookup"><span data-stu-id="7c7ac-113">Ignores any inline schema and reads data into the existing <xref:System.Data.DataSet> schema.</span></span>  
  
## <a name="attributes"></a><span data-ttu-id="7c7ac-114">屬性</span><span class="sxs-lookup"><span data-stu-id="7c7ac-114">Attributes</span></span>  
 <span data-ttu-id="7c7ac-115">中所定義[推斷資料表](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md)，具有屬性的項目會推斷為資料表。</span><span class="sxs-lookup"><span data-stu-id="7c7ac-115">As defined in [Inferring Tables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md), an element with attributes will be inferred as a table.</span></span> <span data-ttu-id="7c7ac-116">然後，該項目的屬性會推斷為資料表的資料行。</span><span class="sxs-lookup"><span data-stu-id="7c7ac-116">The attributes of that element will then be inferred as columns for the table.</span></span> <span data-ttu-id="7c7ac-117">**ColumnMapping**資料行的屬性會設定為**MappingType.Attribute**，以確保為屬性將寫入的資料行名稱，如果結構描述會寫回至 XML。</span><span class="sxs-lookup"><span data-stu-id="7c7ac-117">The **ColumnMapping** property of the columns will be set to **MappingType.Attribute**, to ensure that the column names will be written as attributes if the schema is written back to XML.</span></span> <span data-ttu-id="7c7ac-118">屬性的值儲存在資料表的資料列中。</span><span class="sxs-lookup"><span data-stu-id="7c7ac-118">The values of the attributes are stored in a row in the table.</span></span> <span data-ttu-id="7c7ac-119">例如，請考量下列 XML：</span><span class="sxs-lookup"><span data-stu-id="7c7ac-119">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="7c7ac-120">推斷程序會產生一個名為資料表**Element1**具有兩個資料行**attr1**並**attr2**。</span><span class="sxs-lookup"><span data-stu-id="7c7ac-120">The inference process will produce a table named **Element1** with two columns, **attr1** and **attr2**.</span></span> <span data-ttu-id="7c7ac-121">**ColumnMapping**的兩個資料行的屬性會設定為**MappingType.Attribute**。</span><span class="sxs-lookup"><span data-stu-id="7c7ac-121">The **ColumnMapping** property of both columns will be set to **MappingType.Attribute**.</span></span>  
  
 <span data-ttu-id="7c7ac-122">**資料集：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="7c7ac-122">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="7c7ac-123">**資料表：** Element1</span><span class="sxs-lookup"><span data-stu-id="7c7ac-123">**Table:** Element1</span></span>  
  
|<span data-ttu-id="7c7ac-124">attr1</span><span class="sxs-lookup"><span data-stu-id="7c7ac-124">attr1</span></span>|<span data-ttu-id="7c7ac-125">attr2</span><span class="sxs-lookup"><span data-stu-id="7c7ac-125">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="7c7ac-126">value1</span><span class="sxs-lookup"><span data-stu-id="7c7ac-126">value1</span></span>|<span data-ttu-id="7c7ac-127">value2</span><span class="sxs-lookup"><span data-stu-id="7c7ac-127">value2</span></span>|  
  
## <a name="elements-without-attributes-or-child-elements"></a><span data-ttu-id="7c7ac-128">沒有屬性或項目子系的項目</span><span class="sxs-lookup"><span data-stu-id="7c7ac-128">Elements Without Attributes or Child Elements</span></span>  
 <span data-ttu-id="7c7ac-129">如果項目沒有項目子系或屬性，則會推斷為資料行。</span><span class="sxs-lookup"><span data-stu-id="7c7ac-129">If an element has no child elements or attributes, it will be inferred as a column.</span></span> <span data-ttu-id="7c7ac-130">**ColumnMapping**資料行的屬性會設定為**MappingType.Element**。</span><span class="sxs-lookup"><span data-stu-id="7c7ac-130">The **ColumnMapping** property of the column will be set to **MappingType.Element**.</span></span> <span data-ttu-id="7c7ac-131">項目子系的文字儲存在資料表的資料列中。</span><span class="sxs-lookup"><span data-stu-id="7c7ac-131">The text for child elements is stored in a row in the table.</span></span> <span data-ttu-id="7c7ac-132">例如，請考量下列 XML：</span><span class="sxs-lookup"><span data-stu-id="7c7ac-132">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="7c7ac-133">推斷程序會產生一個名為資料表**Element1**具有兩個資料行**ChildElement1**並**ChildElement2**。</span><span class="sxs-lookup"><span data-stu-id="7c7ac-133">The inference process will produce a table named **Element1** with two columns, **ChildElement1** and **ChildElement2**.</span></span> <span data-ttu-id="7c7ac-134">**ColumnMapping**的兩個資料行的屬性會設定為**MappingType.Element**。</span><span class="sxs-lookup"><span data-stu-id="7c7ac-134">The **ColumnMapping** property of both columns will be set to **MappingType.Element**.</span></span>  
  
 <span data-ttu-id="7c7ac-135">**資料集：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="7c7ac-135">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="7c7ac-136">**資料表：** Element1</span><span class="sxs-lookup"><span data-stu-id="7c7ac-136">**Table:** Element1</span></span>  
  
|<span data-ttu-id="7c7ac-137">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="7c7ac-137">ChildElement1</span></span>|<span data-ttu-id="7c7ac-138">ChildElement2</span><span class="sxs-lookup"><span data-stu-id="7c7ac-138">ChildElement2</span></span>|  
|-------------------|-------------------|  
|<span data-ttu-id="7c7ac-139">Text1</span><span class="sxs-lookup"><span data-stu-id="7c7ac-139">Text1</span></span>|<span data-ttu-id="7c7ac-140">Text2</span><span class="sxs-lookup"><span data-stu-id="7c7ac-140">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7c7ac-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c7ac-141">See Also</span></span>  
 [<span data-ttu-id="7c7ac-142">從 XML 推斷資料集關聯式結構</span><span class="sxs-lookup"><span data-stu-id="7c7ac-142">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="7c7ac-143">從 XML 載入資料集</span><span class="sxs-lookup"><span data-stu-id="7c7ac-143">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="7c7ac-144">從 XML 載入資料集結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="7c7ac-144">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="7c7ac-145">在 DataSet 中使用 XML</span><span class="sxs-lookup"><span data-stu-id="7c7ac-145">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="7c7ac-146">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="7c7ac-146">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="7c7ac-147">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="7c7ac-147">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
