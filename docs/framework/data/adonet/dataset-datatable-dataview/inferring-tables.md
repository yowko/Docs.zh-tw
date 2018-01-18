---
title: "推斷資料表"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 2c00dd11d4d93e5d3b0e2f1c3b75765056a10cab
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="inferring-tables"></a><span data-ttu-id="d7174-102">推斷資料表</span><span class="sxs-lookup"><span data-stu-id="d7174-102">Inferring Tables</span></span>
<span data-ttu-id="d7174-103">從 XML 文件推斷 <xref:System.Data.DataSet> 的結構描述時，ADO.NET 首先會決定要用哪些 XML 項目來表示資料表。</span><span class="sxs-lookup"><span data-stu-id="d7174-103">When inferring a schema for a <xref:System.Data.DataSet> from an XML document, ADO.NET first determines which XML elements represent tables.</span></span> <span data-ttu-id="d7174-104">下列 XML 結構會導致資料表**資料集**結構描述：</span><span class="sxs-lookup"><span data-stu-id="d7174-104">The following XML structures result in a table for the **DataSet** schema:</span></span>  
  
-   <span data-ttu-id="d7174-105">具有屬性的項目</span><span class="sxs-lookup"><span data-stu-id="d7174-105">Elements with attributes</span></span>  
  
-   <span data-ttu-id="d7174-106">具有項目子系的項目</span><span class="sxs-lookup"><span data-stu-id="d7174-106">Elements with child elements</span></span>  
  
-   <span data-ttu-id="d7174-107">重複項目</span><span class="sxs-lookup"><span data-stu-id="d7174-107">Repeating elements</span></span>  
  
## <a name="elements-with-attributes"></a><span data-ttu-id="d7174-108">具有屬性的項目</span><span class="sxs-lookup"><span data-stu-id="d7174-108">Elements with Attributes</span></span>  
 <span data-ttu-id="d7174-109">具有指定屬性的項目會產生推斷資料表。</span><span class="sxs-lookup"><span data-stu-id="d7174-109">Elements that have attributes specified in them result in inferred tables.</span></span> <span data-ttu-id="d7174-110">例如，請考量下列 XML：</span><span class="sxs-lookup"><span data-stu-id="d7174-110">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="d7174-111">推斷處理序會產生名為 Element1 的資料表。</span><span class="sxs-lookup"><span data-stu-id="d7174-111">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="d7174-112">**資料集：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="d7174-112">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="d7174-113">**Table:** Element1</span><span class="sxs-lookup"><span data-stu-id="d7174-113">**Table:** Element1</span></span>  
  
|<span data-ttu-id="d7174-114">attr1</span><span class="sxs-lookup"><span data-stu-id="d7174-114">attr1</span></span>|<span data-ttu-id="d7174-115">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="d7174-115">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="d7174-116">value1</span><span class="sxs-lookup"><span data-stu-id="d7174-116">value1</span></span>||  
|<span data-ttu-id="d7174-117">value2</span><span class="sxs-lookup"><span data-stu-id="d7174-117">value2</span></span>|<span data-ttu-id="d7174-118">Text1</span><span class="sxs-lookup"><span data-stu-id="d7174-118">Text1</span></span>|  
  
## <a name="elements-with-child-elements"></a><span data-ttu-id="d7174-119">具有項目子系的項目</span><span class="sxs-lookup"><span data-stu-id="d7174-119">Elements with Child Elements</span></span>  
 <span data-ttu-id="d7174-120">具有項目子系的項目會產生推斷資料表。</span><span class="sxs-lookup"><span data-stu-id="d7174-120">Elements that have child elements result in inferred tables.</span></span> <span data-ttu-id="d7174-121">例如，請考量下列 XML：</span><span class="sxs-lookup"><span data-stu-id="d7174-121">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="d7174-122">推斷處理序會產生名為 Element1 的資料表。</span><span class="sxs-lookup"><span data-stu-id="d7174-122">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="d7174-123">**資料集：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="d7174-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="d7174-124">**Table:** Element1</span><span class="sxs-lookup"><span data-stu-id="d7174-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="d7174-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="d7174-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="d7174-126">Text1</span><span class="sxs-lookup"><span data-stu-id="d7174-126">Text1</span></span>|  
  
 <span data-ttu-id="d7174-127">如果文件或根項目具有將推斷為資料行的屬性或項目子系，便會產生推斷資料表。</span><span class="sxs-lookup"><span data-stu-id="d7174-127">The document, or root, element result in an inferred table if it has attributes or child elements that are inferred as columns.</span></span> <span data-ttu-id="d7174-128">如果文件項目沒有屬性和任何子項目會推斷為資料行，項目會推斷為**資料集**。</span><span class="sxs-lookup"><span data-stu-id="d7174-128">If the document element has no attributes and no child elements that would be inferred as columns, the element is inferred as a **DataSet**.</span></span> <span data-ttu-id="d7174-129">例如，請考量下列 XML：</span><span class="sxs-lookup"><span data-stu-id="d7174-129">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 <span data-ttu-id="d7174-130">推斷處理序會產生名為 DocumentElement 的資料表。</span><span class="sxs-lookup"><span data-stu-id="d7174-130">The inference process produces a table named "DocumentElement."</span></span>  
  
 <span data-ttu-id="d7174-131">**資料集：** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="d7174-131">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="d7174-132">**Table:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="d7174-132">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="d7174-133">Element1</span><span class="sxs-lookup"><span data-stu-id="d7174-133">Element1</span></span>|<span data-ttu-id="d7174-134">Element2</span><span class="sxs-lookup"><span data-stu-id="d7174-134">Element2</span></span>|  
|--------------|--------------|  
|<span data-ttu-id="d7174-135">Text1</span><span class="sxs-lookup"><span data-stu-id="d7174-135">Text1</span></span>|<span data-ttu-id="d7174-136">Text2</span><span class="sxs-lookup"><span data-stu-id="d7174-136">Text2</span></span>|  
  
 <span data-ttu-id="d7174-137">另一個方法是考量下列 XML：</span><span class="sxs-lookup"><span data-stu-id="d7174-137">Alternatively, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="d7174-138">推斷程序產生**資料集**名為"DocumentElement"，其中包含名為"Element1。 」 的資料表</span><span class="sxs-lookup"><span data-stu-id="d7174-138">The inference process produces a **DataSet** named "DocumentElement" that contains a table named "Element1."</span></span>  
  
 <span data-ttu-id="d7174-139">**資料集：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="d7174-139">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="d7174-140">**Table:** Element1</span><span class="sxs-lookup"><span data-stu-id="d7174-140">**Table:** Element1</span></span>  
  
|<span data-ttu-id="d7174-141">attr1</span><span class="sxs-lookup"><span data-stu-id="d7174-141">attr1</span></span>|<span data-ttu-id="d7174-142">attr2</span><span class="sxs-lookup"><span data-stu-id="d7174-142">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="d7174-143">value1</span><span class="sxs-lookup"><span data-stu-id="d7174-143">value1</span></span>|<span data-ttu-id="d7174-144">value2</span><span class="sxs-lookup"><span data-stu-id="d7174-144">value2</span></span>|  
  
## <a name="repeating-elements"></a><span data-ttu-id="d7174-145">重複項目</span><span class="sxs-lookup"><span data-stu-id="d7174-145">Repeating Elements</span></span>  
 <span data-ttu-id="d7174-146">重複項目會產生單一推斷資料表。</span><span class="sxs-lookup"><span data-stu-id="d7174-146">Elements that repeat result in a single inferred table.</span></span> <span data-ttu-id="d7174-147">例如，請考量下列 XML：</span><span class="sxs-lookup"><span data-stu-id="d7174-147">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="d7174-148">推斷處理序會產生名為 Element1 的資料表。</span><span class="sxs-lookup"><span data-stu-id="d7174-148">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="d7174-149">**資料集：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="d7174-149">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="d7174-150">**Table:** Element1</span><span class="sxs-lookup"><span data-stu-id="d7174-150">**Table:** Element1</span></span>  
  
|<span data-ttu-id="d7174-151">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="d7174-151">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="d7174-152">Text1</span><span class="sxs-lookup"><span data-stu-id="d7174-152">Text1</span></span>|  
|<span data-ttu-id="d7174-153">Text2</span><span class="sxs-lookup"><span data-stu-id="d7174-153">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d7174-154">請參閱</span><span class="sxs-lookup"><span data-stu-id="d7174-154">See Also</span></span>  
 [<span data-ttu-id="d7174-155">從 XML 推斷資料集關聯式結構</span><span class="sxs-lookup"><span data-stu-id="d7174-155">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="d7174-156">從 XML 載入資料集</span><span class="sxs-lookup"><span data-stu-id="d7174-156">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="d7174-157">從 XML 載入資料集結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="d7174-157">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="d7174-158">在 DataSet 中使用 XML</span><span class="sxs-lookup"><span data-stu-id="d7174-158">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="d7174-159">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="d7174-159">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="d7174-160">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="d7174-160">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
