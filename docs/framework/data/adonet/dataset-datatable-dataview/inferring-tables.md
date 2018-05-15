---
title: 推斷資料表
ms.date: 03/30/2017
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
ms.openlocfilehash: b14cbc39b02136ac7f226faf2636a69ac072f529
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="inferring-tables"></a><span data-ttu-id="f53f3-102">推斷資料表</span><span class="sxs-lookup"><span data-stu-id="f53f3-102">Inferring Tables</span></span>
<span data-ttu-id="f53f3-103">從 XML 文件推斷 <xref:System.Data.DataSet> 的結構描述時，ADO.NET 首先會決定要用哪些 XML 項目來表示資料表。</span><span class="sxs-lookup"><span data-stu-id="f53f3-103">When inferring a schema for a <xref:System.Data.DataSet> from an XML document, ADO.NET first determines which XML elements represent tables.</span></span> <span data-ttu-id="f53f3-104">下列 XML 結構會導致資料表**資料集**結構描述：</span><span class="sxs-lookup"><span data-stu-id="f53f3-104">The following XML structures result in a table for the **DataSet** schema:</span></span>  
  
-   <span data-ttu-id="f53f3-105">具有屬性的項目</span><span class="sxs-lookup"><span data-stu-id="f53f3-105">Elements with attributes</span></span>  
  
-   <span data-ttu-id="f53f3-106">具有項目子系的項目</span><span class="sxs-lookup"><span data-stu-id="f53f3-106">Elements with child elements</span></span>  
  
-   <span data-ttu-id="f53f3-107">重複項目</span><span class="sxs-lookup"><span data-stu-id="f53f3-107">Repeating elements</span></span>  
  
## <a name="elements-with-attributes"></a><span data-ttu-id="f53f3-108">具有屬性的項目</span><span class="sxs-lookup"><span data-stu-id="f53f3-108">Elements with Attributes</span></span>  
 <span data-ttu-id="f53f3-109">具有指定屬性的項目會產生推斷資料表。</span><span class="sxs-lookup"><span data-stu-id="f53f3-109">Elements that have attributes specified in them result in inferred tables.</span></span> <span data-ttu-id="f53f3-110">例如，請考量下列 XML：</span><span class="sxs-lookup"><span data-stu-id="f53f3-110">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="f53f3-111">推斷處理序會產生名為 Element1 的資料表。</span><span class="sxs-lookup"><span data-stu-id="f53f3-111">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="f53f3-112">**資料集：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="f53f3-112">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="f53f3-113">**Table:** Element1</span><span class="sxs-lookup"><span data-stu-id="f53f3-113">**Table:** Element1</span></span>  
  
|<span data-ttu-id="f53f3-114">attr1</span><span class="sxs-lookup"><span data-stu-id="f53f3-114">attr1</span></span>|<span data-ttu-id="f53f3-115">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="f53f3-115">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="f53f3-116">value1</span><span class="sxs-lookup"><span data-stu-id="f53f3-116">value1</span></span>||  
|<span data-ttu-id="f53f3-117">value2</span><span class="sxs-lookup"><span data-stu-id="f53f3-117">value2</span></span>|<span data-ttu-id="f53f3-118">Text1</span><span class="sxs-lookup"><span data-stu-id="f53f3-118">Text1</span></span>|  
  
## <a name="elements-with-child-elements"></a><span data-ttu-id="f53f3-119">具有項目子系的項目</span><span class="sxs-lookup"><span data-stu-id="f53f3-119">Elements with Child Elements</span></span>  
 <span data-ttu-id="f53f3-120">具有項目子系的項目會產生推斷資料表。</span><span class="sxs-lookup"><span data-stu-id="f53f3-120">Elements that have child elements result in inferred tables.</span></span> <span data-ttu-id="f53f3-121">例如，請考量下列 XML：</span><span class="sxs-lookup"><span data-stu-id="f53f3-121">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="f53f3-122">推斷處理序會產生名為 Element1 的資料表。</span><span class="sxs-lookup"><span data-stu-id="f53f3-122">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="f53f3-123">**資料集：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="f53f3-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="f53f3-124">**Table:** Element1</span><span class="sxs-lookup"><span data-stu-id="f53f3-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="f53f3-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="f53f3-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="f53f3-126">Text1</span><span class="sxs-lookup"><span data-stu-id="f53f3-126">Text1</span></span>|  
  
 <span data-ttu-id="f53f3-127">如果文件或根項目具有將推斷為資料行的屬性或項目子系，便會產生推斷資料表。</span><span class="sxs-lookup"><span data-stu-id="f53f3-127">The document, or root, element result in an inferred table if it has attributes or child elements that are inferred as columns.</span></span> <span data-ttu-id="f53f3-128">如果文件項目沒有屬性和任何子項目會推斷為資料行，項目會推斷為**資料集**。</span><span class="sxs-lookup"><span data-stu-id="f53f3-128">If the document element has no attributes and no child elements that would be inferred as columns, the element is inferred as a **DataSet**.</span></span> <span data-ttu-id="f53f3-129">例如，請考量下列 XML：</span><span class="sxs-lookup"><span data-stu-id="f53f3-129">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 <span data-ttu-id="f53f3-130">推斷處理序會產生名為 DocumentElement 的資料表。</span><span class="sxs-lookup"><span data-stu-id="f53f3-130">The inference process produces a table named "DocumentElement."</span></span>  
  
 <span data-ttu-id="f53f3-131">**資料集：** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="f53f3-131">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="f53f3-132">**Table:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="f53f3-132">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="f53f3-133">Element1</span><span class="sxs-lookup"><span data-stu-id="f53f3-133">Element1</span></span>|<span data-ttu-id="f53f3-134">Element2</span><span class="sxs-lookup"><span data-stu-id="f53f3-134">Element2</span></span>|  
|--------------|--------------|  
|<span data-ttu-id="f53f3-135">Text1</span><span class="sxs-lookup"><span data-stu-id="f53f3-135">Text1</span></span>|<span data-ttu-id="f53f3-136">Text2</span><span class="sxs-lookup"><span data-stu-id="f53f3-136">Text2</span></span>|  
  
 <span data-ttu-id="f53f3-137">另一個方法是考量下列 XML：</span><span class="sxs-lookup"><span data-stu-id="f53f3-137">Alternatively, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="f53f3-138">推斷程序產生**資料集**名為"DocumentElement"，其中包含名為"Element1。 」 的資料表</span><span class="sxs-lookup"><span data-stu-id="f53f3-138">The inference process produces a **DataSet** named "DocumentElement" that contains a table named "Element1."</span></span>  
  
 <span data-ttu-id="f53f3-139">**資料集：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="f53f3-139">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="f53f3-140">**Table:** Element1</span><span class="sxs-lookup"><span data-stu-id="f53f3-140">**Table:** Element1</span></span>  
  
|<span data-ttu-id="f53f3-141">attr1</span><span class="sxs-lookup"><span data-stu-id="f53f3-141">attr1</span></span>|<span data-ttu-id="f53f3-142">attr2</span><span class="sxs-lookup"><span data-stu-id="f53f3-142">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="f53f3-143">value1</span><span class="sxs-lookup"><span data-stu-id="f53f3-143">value1</span></span>|<span data-ttu-id="f53f3-144">value2</span><span class="sxs-lookup"><span data-stu-id="f53f3-144">value2</span></span>|  
  
## <a name="repeating-elements"></a><span data-ttu-id="f53f3-145">重複項目</span><span class="sxs-lookup"><span data-stu-id="f53f3-145">Repeating Elements</span></span>  
 <span data-ttu-id="f53f3-146">重複項目會產生單一推斷資料表。</span><span class="sxs-lookup"><span data-stu-id="f53f3-146">Elements that repeat result in a single inferred table.</span></span> <span data-ttu-id="f53f3-147">例如，請考量下列 XML：</span><span class="sxs-lookup"><span data-stu-id="f53f3-147">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="f53f3-148">推斷處理序會產生名為 Element1 的資料表。</span><span class="sxs-lookup"><span data-stu-id="f53f3-148">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="f53f3-149">**資料集：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="f53f3-149">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="f53f3-150">**Table:** Element1</span><span class="sxs-lookup"><span data-stu-id="f53f3-150">**Table:** Element1</span></span>  
  
|<span data-ttu-id="f53f3-151">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="f53f3-151">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="f53f3-152">Text1</span><span class="sxs-lookup"><span data-stu-id="f53f3-152">Text1</span></span>|  
|<span data-ttu-id="f53f3-153">Text2</span><span class="sxs-lookup"><span data-stu-id="f53f3-153">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f53f3-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f53f3-154">See Also</span></span>  
 [<span data-ttu-id="f53f3-155">從 XML 推斷資料集關聯式結構</span><span class="sxs-lookup"><span data-stu-id="f53f3-155">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="f53f3-156">從 XML 載入資料集</span><span class="sxs-lookup"><span data-stu-id="f53f3-156">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="f53f3-157">從 XML 載入資料集結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="f53f3-157">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="f53f3-158">在 DataSet 中使用 XML</span><span class="sxs-lookup"><span data-stu-id="f53f3-158">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="f53f3-159">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="f53f3-159">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="f53f3-160">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="f53f3-160">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
