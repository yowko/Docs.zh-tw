---
title: "推斷資料行"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e022699-c922-454c-93e2-957dd7e7247a
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ba06bce55db53de1da1c07d2a6451d5664fa23bf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="inferring-columns"></a><span data-ttu-id="af499-102">推斷資料行</span><span class="sxs-lookup"><span data-stu-id="af499-102">Inferring Columns</span></span>
<span data-ttu-id="af499-103">ADO.NET 從 XML 文件中判斷要將哪些項目推斷成 <xref:System.Data.DataSet> 的資料表後，接著就會推斷這些資料表的資料行。</span><span class="sxs-lookup"><span data-stu-id="af499-103">After ADO.NET has determined from an XML document which elements to infer as tables for a <xref:System.Data.DataSet>, it then infers the columns for those tables.</span></span> <span data-ttu-id="af499-104">ADO.NET 2.0 導入了新的結構描述推斷引擎，為每個推斷強型別的資料型別**simpleType**項目。</span><span class="sxs-lookup"><span data-stu-id="af499-104">ADO.NET 2.0 introduced a new schema inference engine that infers a strongly typed data type for each **simpleType** element.</span></span> <span data-ttu-id="af499-105">在較舊的版本中的資料型別推斷**simpleType**項目一律為**xsd: string**。</span><span class="sxs-lookup"><span data-stu-id="af499-105">In previous versions, the data type of an inferred **simpleType** element was always **xsd:string**.</span></span>  
  
## <a name="migration-and-backward-compatibility"></a><span data-ttu-id="af499-106">移轉和回溯相容性</span><span class="sxs-lookup"><span data-stu-id="af499-106">Migration and Backward Compatibility</span></span>  
 <span data-ttu-id="af499-107">**ReadXml**方法接受型別引數**InferSchema**。</span><span class="sxs-lookup"><span data-stu-id="af499-107">The **ReadXml** method takes an argument of type **InferSchema**.</span></span> <span data-ttu-id="af499-108">這個引數可讓您指定與舊版本相容的推斷行為。</span><span class="sxs-lookup"><span data-stu-id="af499-108">This argument allows you to specify inference behavior compatible with previous versions.</span></span> <span data-ttu-id="af499-109">可用的值**InferSchema**列舉型別會顯示下表中。</span><span class="sxs-lookup"><span data-stu-id="af499-109">The available values for the **InferSchema** enumeration are shown in the following table.</span></span>  
  
 <xref:System.Data.XmlReadMode.InferSchema>  
 <span data-ttu-id="af499-110">將簡單型別永遠推斷為 <xref:System.String>，以提供回溯相容性 (Backward Compatibility)。</span><span class="sxs-lookup"><span data-stu-id="af499-110">Provides backward compatibility by always inferring a simple type as <xref:System.String>.</span></span>  
  
 <xref:System.Data.XmlReadMode.InferTypedSchema>  
 <span data-ttu-id="af499-111">推斷強型別資料型別。</span><span class="sxs-lookup"><span data-stu-id="af499-111">Infers a strongly typed data type.</span></span> <span data-ttu-id="af499-112">若用於 <xref:System.Data.DataTable>，則會擲回例外狀況 (Exception)。</span><span class="sxs-lookup"><span data-stu-id="af499-112">Throws an exception if used with a <xref:System.Data.DataTable>.</span></span>  
  
 <xref:System.Data.XmlReadMode.IgnoreSchema>  
 <span data-ttu-id="af499-113">忽略任何內嵌結構描述，並將資料讀入現有的 <xref:System.Data.DataSet> 結構描述中。</span><span class="sxs-lookup"><span data-stu-id="af499-113">Ignores any inline schema and reads data into the existing <xref:System.Data.DataSet> schema.</span></span>  
  
## <a name="attributes"></a><span data-ttu-id="af499-114">屬性</span><span class="sxs-lookup"><span data-stu-id="af499-114">Attributes</span></span>  
 <span data-ttu-id="af499-115">中所定義[推斷資料表](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md)，具有屬性的項目會推斷為資料表。</span><span class="sxs-lookup"><span data-stu-id="af499-115">As defined in [Inferring Tables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md), an element with attributes will be inferred as a table.</span></span> <span data-ttu-id="af499-116">然後，該項目的屬性會推斷為資料表的資料行。</span><span class="sxs-lookup"><span data-stu-id="af499-116">The attributes of that element will then be inferred as columns for the table.</span></span> <span data-ttu-id="af499-117">**ColumnMapping**的資料行的屬性會設定為**MappingType.Attribute**，以確保做為屬性將寫入的資料行名稱，如果結構描述寫回為 XML。</span><span class="sxs-lookup"><span data-stu-id="af499-117">The **ColumnMapping** property of the columns will be set to **MappingType.Attribute**, to ensure that the column names will be written as attributes if the schema is written back to XML.</span></span> <span data-ttu-id="af499-118">屬性的值儲存在資料表的資料列中。</span><span class="sxs-lookup"><span data-stu-id="af499-118">The values of the attributes are stored in a row in the table.</span></span> <span data-ttu-id="af499-119">例如，請考量下列 XML：</span><span class="sxs-lookup"><span data-stu-id="af499-119">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="af499-120">推斷程序將會產生名為的資料表**Element1**具有兩個資料行， **attr1**和**attr2**。</span><span class="sxs-lookup"><span data-stu-id="af499-120">The inference process will produce a table named **Element1** with two columns, **attr1** and **attr2**.</span></span> <span data-ttu-id="af499-121">**ColumnMapping**的兩個資料行的屬性會設定為**MappingType.Attribute**。</span><span class="sxs-lookup"><span data-stu-id="af499-121">The **ColumnMapping** property of both columns will be set to **MappingType.Attribute**.</span></span>  
  
 <span data-ttu-id="af499-122">**資料集：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="af499-122">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="af499-123">**Table:** Element1</span><span class="sxs-lookup"><span data-stu-id="af499-123">**Table:** Element1</span></span>  
  
|<span data-ttu-id="af499-124">attr1</span><span class="sxs-lookup"><span data-stu-id="af499-124">attr1</span></span>|<span data-ttu-id="af499-125">attr2</span><span class="sxs-lookup"><span data-stu-id="af499-125">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="af499-126">value1</span><span class="sxs-lookup"><span data-stu-id="af499-126">value1</span></span>|<span data-ttu-id="af499-127">value2</span><span class="sxs-lookup"><span data-stu-id="af499-127">value2</span></span>|  
  
## <a name="elements-without-attributes-or-child-elements"></a><span data-ttu-id="af499-128">沒有屬性或項目子系的項目</span><span class="sxs-lookup"><span data-stu-id="af499-128">Elements Without Attributes or Child Elements</span></span>  
 <span data-ttu-id="af499-129">如果項目沒有項目子系或屬性，則會推斷為資料行。</span><span class="sxs-lookup"><span data-stu-id="af499-129">If an element has no child elements or attributes, it will be inferred as a column.</span></span> <span data-ttu-id="af499-130">**ColumnMapping**資料行的屬性會設定為**MappingType.Element**。</span><span class="sxs-lookup"><span data-stu-id="af499-130">The **ColumnMapping** property of the column will be set to **MappingType.Element**.</span></span> <span data-ttu-id="af499-131">項目子系的文字儲存在資料表的資料列中。</span><span class="sxs-lookup"><span data-stu-id="af499-131">The text for child elements is stored in a row in the table.</span></span> <span data-ttu-id="af499-132">例如，請考量下列 XML：</span><span class="sxs-lookup"><span data-stu-id="af499-132">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="af499-133">推斷程序將會產生名為的資料表**Element1**具有兩個資料行， **ChildElement1**和**ChildElement2**。</span><span class="sxs-lookup"><span data-stu-id="af499-133">The inference process will produce a table named **Element1** with two columns, **ChildElement1** and **ChildElement2**.</span></span> <span data-ttu-id="af499-134">**ColumnMapping**的兩個資料行的屬性會設定為**MappingType.Element**。</span><span class="sxs-lookup"><span data-stu-id="af499-134">The **ColumnMapping** property of both columns will be set to **MappingType.Element**.</span></span>  
  
 <span data-ttu-id="af499-135">**資料集：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="af499-135">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="af499-136">**Table:** Element1</span><span class="sxs-lookup"><span data-stu-id="af499-136">**Table:** Element1</span></span>  
  
|<span data-ttu-id="af499-137">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="af499-137">ChildElement1</span></span>|<span data-ttu-id="af499-138">ChildElement2</span><span class="sxs-lookup"><span data-stu-id="af499-138">ChildElement2</span></span>|  
|-------------------|-------------------|  
|<span data-ttu-id="af499-139">Text1</span><span class="sxs-lookup"><span data-stu-id="af499-139">Text1</span></span>|<span data-ttu-id="af499-140">Text2</span><span class="sxs-lookup"><span data-stu-id="af499-140">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="af499-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af499-141">See Also</span></span>  
 [<span data-ttu-id="af499-142">從 XML 推斷資料集關聯式結構</span><span class="sxs-lookup"><span data-stu-id="af499-142">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="af499-143">從 XML 載入資料集</span><span class="sxs-lookup"><span data-stu-id="af499-143">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="af499-144">從 XML 載入資料集結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="af499-144">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="af499-145">在 DataSet 中使用 XML</span><span class="sxs-lookup"><span data-stu-id="af499-145">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="af499-146">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="af499-146">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="af499-147">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="af499-147">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
