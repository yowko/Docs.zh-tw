---
title: 推斷資料表
ms.date: 03/30/2017
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
ms.openlocfilehash: 38709f91e01c7f85d9e8482bdd49bc0892121f09
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2018
ms.locfileid: "43332849"
---
# <a name="inferring-tables"></a><span data-ttu-id="d6c17-102">推斷資料表</span><span class="sxs-lookup"><span data-stu-id="d6c17-102">Inferring Tables</span></span>
<span data-ttu-id="d6c17-103">從 XML 文件推斷 <xref:System.Data.DataSet> 的結構描述時，ADO.NET 首先會決定要用哪些 XML 項目來表示資料表。</span><span class="sxs-lookup"><span data-stu-id="d6c17-103">When inferring a schema for a <xref:System.Data.DataSet> from an XML document, ADO.NET first determines which XML elements represent tables.</span></span> <span data-ttu-id="d6c17-104">下列 XML 結構會導致資料表**資料集**結構描述：</span><span class="sxs-lookup"><span data-stu-id="d6c17-104">The following XML structures result in a table for the **DataSet** schema:</span></span>  
  
-   <span data-ttu-id="d6c17-105">具有屬性的項目</span><span class="sxs-lookup"><span data-stu-id="d6c17-105">Elements with attributes</span></span>  
  
-   <span data-ttu-id="d6c17-106">具有項目子系的項目</span><span class="sxs-lookup"><span data-stu-id="d6c17-106">Elements with child elements</span></span>  
  
-   <span data-ttu-id="d6c17-107">重複項目</span><span class="sxs-lookup"><span data-stu-id="d6c17-107">Repeating elements</span></span>  
  
## <a name="elements-with-attributes"></a><span data-ttu-id="d6c17-108">具有屬性的項目</span><span class="sxs-lookup"><span data-stu-id="d6c17-108">Elements with Attributes</span></span>  
 <span data-ttu-id="d6c17-109">具有指定屬性的項目會產生推斷資料表。</span><span class="sxs-lookup"><span data-stu-id="d6c17-109">Elements that have attributes specified in them result in inferred tables.</span></span> <span data-ttu-id="d6c17-110">例如，請考量下列 XML：</span><span class="sxs-lookup"><span data-stu-id="d6c17-110">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="d6c17-111">推斷處理序會產生名為 Element1 的資料表。</span><span class="sxs-lookup"><span data-stu-id="d6c17-111">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="d6c17-112">**資料集：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="d6c17-112">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="d6c17-113">**資料表：** Element1</span><span class="sxs-lookup"><span data-stu-id="d6c17-113">**Table:** Element1</span></span>  
  
|<span data-ttu-id="d6c17-114">attr1</span><span class="sxs-lookup"><span data-stu-id="d6c17-114">attr1</span></span>|<span data-ttu-id="d6c17-115">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="d6c17-115">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="d6c17-116">value1</span><span class="sxs-lookup"><span data-stu-id="d6c17-116">value1</span></span>||  
|<span data-ttu-id="d6c17-117">value2</span><span class="sxs-lookup"><span data-stu-id="d6c17-117">value2</span></span>|<span data-ttu-id="d6c17-118">Text1</span><span class="sxs-lookup"><span data-stu-id="d6c17-118">Text1</span></span>|  
  
## <a name="elements-with-child-elements"></a><span data-ttu-id="d6c17-119">具有項目子系的項目</span><span class="sxs-lookup"><span data-stu-id="d6c17-119">Elements with Child Elements</span></span>  
 <span data-ttu-id="d6c17-120">具有項目子系的項目會產生推斷資料表。</span><span class="sxs-lookup"><span data-stu-id="d6c17-120">Elements that have child elements result in inferred tables.</span></span> <span data-ttu-id="d6c17-121">例如，請考量下列 XML：</span><span class="sxs-lookup"><span data-stu-id="d6c17-121">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="d6c17-122">推斷處理序會產生名為 Element1 的資料表。</span><span class="sxs-lookup"><span data-stu-id="d6c17-122">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="d6c17-123">**資料集：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="d6c17-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="d6c17-124">**資料表：** Element1</span><span class="sxs-lookup"><span data-stu-id="d6c17-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="d6c17-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="d6c17-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="d6c17-126">Text1</span><span class="sxs-lookup"><span data-stu-id="d6c17-126">Text1</span></span>|  
  
 <span data-ttu-id="d6c17-127">如果文件或根項目具有將推斷為資料行的屬性或項目子系，便會產生推斷資料表。</span><span class="sxs-lookup"><span data-stu-id="d6c17-127">The document, or root, element result in an inferred table if it has attributes or child elements that are inferred as columns.</span></span> <span data-ttu-id="d6c17-128">如果文件項目沒有屬性和任何子項目會推斷為資料行，將項目被推斷為**資料集**。</span><span class="sxs-lookup"><span data-stu-id="d6c17-128">If the document element has no attributes and no child elements that would be inferred as columns, the element is inferred as a **DataSet**.</span></span> <span data-ttu-id="d6c17-129">例如，請考量下列 XML：</span><span class="sxs-lookup"><span data-stu-id="d6c17-129">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 <span data-ttu-id="d6c17-130">推斷處理序會產生名為 DocumentElement 的資料表。</span><span class="sxs-lookup"><span data-stu-id="d6c17-130">The inference process produces a table named "DocumentElement."</span></span>  
  
 <span data-ttu-id="d6c17-131">**資料集：** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="d6c17-131">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="d6c17-132">**資料表：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="d6c17-132">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="d6c17-133">Element1</span><span class="sxs-lookup"><span data-stu-id="d6c17-133">Element1</span></span>|<span data-ttu-id="d6c17-134">Element2</span><span class="sxs-lookup"><span data-stu-id="d6c17-134">Element2</span></span>|  
|--------------|--------------|  
|<span data-ttu-id="d6c17-135">Text1</span><span class="sxs-lookup"><span data-stu-id="d6c17-135">Text1</span></span>|<span data-ttu-id="d6c17-136">Text2</span><span class="sxs-lookup"><span data-stu-id="d6c17-136">Text2</span></span>|  
  
 <span data-ttu-id="d6c17-137">另一個方法是考量下列 XML：</span><span class="sxs-lookup"><span data-stu-id="d6c17-137">Alternatively, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="d6c17-138">推斷程序會產生**資料集**名為"DocumentElement"，其中包含名為"Element1。 」</span><span class="sxs-lookup"><span data-stu-id="d6c17-138">The inference process produces a **DataSet** named "DocumentElement" that contains a table named "Element1."</span></span>  
  
 <span data-ttu-id="d6c17-139">**資料集：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="d6c17-139">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="d6c17-140">**資料表：** Element1</span><span class="sxs-lookup"><span data-stu-id="d6c17-140">**Table:** Element1</span></span>  
  
|<span data-ttu-id="d6c17-141">attr1</span><span class="sxs-lookup"><span data-stu-id="d6c17-141">attr1</span></span>|<span data-ttu-id="d6c17-142">attr2</span><span class="sxs-lookup"><span data-stu-id="d6c17-142">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="d6c17-143">value1</span><span class="sxs-lookup"><span data-stu-id="d6c17-143">value1</span></span>|<span data-ttu-id="d6c17-144">value2</span><span class="sxs-lookup"><span data-stu-id="d6c17-144">value2</span></span>|  
  
## <a name="repeating-elements"></a><span data-ttu-id="d6c17-145">重複項目</span><span class="sxs-lookup"><span data-stu-id="d6c17-145">Repeating Elements</span></span>  
 <span data-ttu-id="d6c17-146">重複項目會產生單一推斷資料表。</span><span class="sxs-lookup"><span data-stu-id="d6c17-146">Elements that repeat result in a single inferred table.</span></span> <span data-ttu-id="d6c17-147">例如，請考量下列 XML：</span><span class="sxs-lookup"><span data-stu-id="d6c17-147">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="d6c17-148">推斷處理序會產生名為 Element1 的資料表。</span><span class="sxs-lookup"><span data-stu-id="d6c17-148">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="d6c17-149">**資料集：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="d6c17-149">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="d6c17-150">**資料表：** Element1</span><span class="sxs-lookup"><span data-stu-id="d6c17-150">**Table:** Element1</span></span>  
  
|<span data-ttu-id="d6c17-151">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="d6c17-151">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="d6c17-152">Text1</span><span class="sxs-lookup"><span data-stu-id="d6c17-152">Text1</span></span>|  
|<span data-ttu-id="d6c17-153">Text2</span><span class="sxs-lookup"><span data-stu-id="d6c17-153">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d6c17-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6c17-154">See Also</span></span>  
 [<span data-ttu-id="d6c17-155">從 XML 推斷資料集關聯式結構</span><span class="sxs-lookup"><span data-stu-id="d6c17-155">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="d6c17-156">從 XML 載入資料集</span><span class="sxs-lookup"><span data-stu-id="d6c17-156">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="d6c17-157">從 XML 載入資料集結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="d6c17-157">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="d6c17-158">在 DataSet 中使用 XML</span><span class="sxs-lookup"><span data-stu-id="d6c17-158">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="d6c17-159">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="d6c17-159">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="d6c17-160">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="d6c17-160">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
