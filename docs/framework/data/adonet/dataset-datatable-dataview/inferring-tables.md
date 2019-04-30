---
title: 推斷資料表
ms.date: 03/30/2017
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
ms.openlocfilehash: 2c2a93d413f301dc3006b701e4bc7979a3fa7a1d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034251"
---
# <a name="inferring-tables"></a><span data-ttu-id="b2bf0-102">推斷資料表</span><span class="sxs-lookup"><span data-stu-id="b2bf0-102">Inferring Tables</span></span>
<span data-ttu-id="b2bf0-103">從 XML 文件推斷 <xref:System.Data.DataSet> 的結構描述時，ADO.NET 首先會決定要用哪些 XML 項目來表示資料表。</span><span class="sxs-lookup"><span data-stu-id="b2bf0-103">When inferring a schema for a <xref:System.Data.DataSet> from an XML document, ADO.NET first determines which XML elements represent tables.</span></span> <span data-ttu-id="b2bf0-104">下列 XML 結構會導致資料表**資料集**結構描述：</span><span class="sxs-lookup"><span data-stu-id="b2bf0-104">The following XML structures result in a table for the **DataSet** schema:</span></span>  
  
- <span data-ttu-id="b2bf0-105">具有屬性的項目</span><span class="sxs-lookup"><span data-stu-id="b2bf0-105">Elements with attributes</span></span>  
  
- <span data-ttu-id="b2bf0-106">具有項目子系的項目</span><span class="sxs-lookup"><span data-stu-id="b2bf0-106">Elements with child elements</span></span>  
  
- <span data-ttu-id="b2bf0-107">重複項目</span><span class="sxs-lookup"><span data-stu-id="b2bf0-107">Repeating elements</span></span>  
  
## <a name="elements-with-attributes"></a><span data-ttu-id="b2bf0-108">具有屬性的項目</span><span class="sxs-lookup"><span data-stu-id="b2bf0-108">Elements with Attributes</span></span>  
 <span data-ttu-id="b2bf0-109">具有指定屬性的項目會產生推斷資料表。</span><span class="sxs-lookup"><span data-stu-id="b2bf0-109">Elements that have attributes specified in them result in inferred tables.</span></span> <span data-ttu-id="b2bf0-110">例如，請考量下列 XML：</span><span class="sxs-lookup"><span data-stu-id="b2bf0-110">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="b2bf0-111">推斷處理序會產生名為 Element1 的資料表。</span><span class="sxs-lookup"><span data-stu-id="b2bf0-111">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="b2bf0-112">**資料集：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="b2bf0-112">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="b2bf0-113">**資料表：** Element1</span><span class="sxs-lookup"><span data-stu-id="b2bf0-113">**Table:** Element1</span></span>  
  
|<span data-ttu-id="b2bf0-114">attr1</span><span class="sxs-lookup"><span data-stu-id="b2bf0-114">attr1</span></span>|<span data-ttu-id="b2bf0-115">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="b2bf0-115">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="b2bf0-116">value1</span><span class="sxs-lookup"><span data-stu-id="b2bf0-116">value1</span></span>||  
|<span data-ttu-id="b2bf0-117">value2</span><span class="sxs-lookup"><span data-stu-id="b2bf0-117">value2</span></span>|<span data-ttu-id="b2bf0-118">Text1</span><span class="sxs-lookup"><span data-stu-id="b2bf0-118">Text1</span></span>|  
  
## <a name="elements-with-child-elements"></a><span data-ttu-id="b2bf0-119">具有項目子系的項目</span><span class="sxs-lookup"><span data-stu-id="b2bf0-119">Elements with Child Elements</span></span>  
 <span data-ttu-id="b2bf0-120">具有項目子系的項目會產生推斷資料表。</span><span class="sxs-lookup"><span data-stu-id="b2bf0-120">Elements that have child elements result in inferred tables.</span></span> <span data-ttu-id="b2bf0-121">例如，請考量下列 XML：</span><span class="sxs-lookup"><span data-stu-id="b2bf0-121">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="b2bf0-122">推斷處理序會產生名為 Element1 的資料表。</span><span class="sxs-lookup"><span data-stu-id="b2bf0-122">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="b2bf0-123">**資料集：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="b2bf0-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="b2bf0-124">**資料表：** Element1</span><span class="sxs-lookup"><span data-stu-id="b2bf0-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="b2bf0-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="b2bf0-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="b2bf0-126">Text1</span><span class="sxs-lookup"><span data-stu-id="b2bf0-126">Text1</span></span>|  
  
 <span data-ttu-id="b2bf0-127">如果文件或根項目具有將推斷為資料行的屬性或項目子系，便會產生推斷資料表。</span><span class="sxs-lookup"><span data-stu-id="b2bf0-127">The document, or root, element result in an inferred table if it has attributes or child elements that are inferred as columns.</span></span> <span data-ttu-id="b2bf0-128">如果文件項目沒有屬性和任何子項目會推斷為資料行，將項目被推斷為**資料集**。</span><span class="sxs-lookup"><span data-stu-id="b2bf0-128">If the document element has no attributes and no child elements that would be inferred as columns, the element is inferred as a **DataSet**.</span></span> <span data-ttu-id="b2bf0-129">例如，請考量下列 XML：</span><span class="sxs-lookup"><span data-stu-id="b2bf0-129">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 <span data-ttu-id="b2bf0-130">推斷處理序會產生名為 DocumentElement 的資料表。</span><span class="sxs-lookup"><span data-stu-id="b2bf0-130">The inference process produces a table named "DocumentElement."</span></span>  
  
 <span data-ttu-id="b2bf0-131">**資料集：** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="b2bf0-131">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="b2bf0-132">**資料表：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="b2bf0-132">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="b2bf0-133">Element1</span><span class="sxs-lookup"><span data-stu-id="b2bf0-133">Element1</span></span>|<span data-ttu-id="b2bf0-134">Element2</span><span class="sxs-lookup"><span data-stu-id="b2bf0-134">Element2</span></span>|  
|--------------|--------------|  
|<span data-ttu-id="b2bf0-135">Text1</span><span class="sxs-lookup"><span data-stu-id="b2bf0-135">Text1</span></span>|<span data-ttu-id="b2bf0-136">Text2</span><span class="sxs-lookup"><span data-stu-id="b2bf0-136">Text2</span></span>|  
  
 <span data-ttu-id="b2bf0-137">另一個方法是考量下列 XML：</span><span class="sxs-lookup"><span data-stu-id="b2bf0-137">Alternatively, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="b2bf0-138">推斷程序會產生**資料集**名為"DocumentElement"，其中包含名為"Element1。 」</span><span class="sxs-lookup"><span data-stu-id="b2bf0-138">The inference process produces a **DataSet** named "DocumentElement" that contains a table named "Element1."</span></span>  
  
 <span data-ttu-id="b2bf0-139">**資料集：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="b2bf0-139">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="b2bf0-140">**資料表：** Element1</span><span class="sxs-lookup"><span data-stu-id="b2bf0-140">**Table:** Element1</span></span>  
  
|<span data-ttu-id="b2bf0-141">attr1</span><span class="sxs-lookup"><span data-stu-id="b2bf0-141">attr1</span></span>|<span data-ttu-id="b2bf0-142">attr2</span><span class="sxs-lookup"><span data-stu-id="b2bf0-142">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="b2bf0-143">value1</span><span class="sxs-lookup"><span data-stu-id="b2bf0-143">value1</span></span>|<span data-ttu-id="b2bf0-144">value2</span><span class="sxs-lookup"><span data-stu-id="b2bf0-144">value2</span></span>|  
  
## <a name="repeating-elements"></a><span data-ttu-id="b2bf0-145">重複項目</span><span class="sxs-lookup"><span data-stu-id="b2bf0-145">Repeating Elements</span></span>  
 <span data-ttu-id="b2bf0-146">重複項目會產生單一推斷資料表。</span><span class="sxs-lookup"><span data-stu-id="b2bf0-146">Elements that repeat result in a single inferred table.</span></span> <span data-ttu-id="b2bf0-147">例如，請考量下列 XML：</span><span class="sxs-lookup"><span data-stu-id="b2bf0-147">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="b2bf0-148">推斷處理序會產生名為 Element1 的資料表。</span><span class="sxs-lookup"><span data-stu-id="b2bf0-148">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="b2bf0-149">**資料集：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="b2bf0-149">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="b2bf0-150">**資料表：** Element1</span><span class="sxs-lookup"><span data-stu-id="b2bf0-150">**Table:** Element1</span></span>  
  
|<span data-ttu-id="b2bf0-151">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="b2bf0-151">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="b2bf0-152">Text1</span><span class="sxs-lookup"><span data-stu-id="b2bf0-152">Text1</span></span>|  
|<span data-ttu-id="b2bf0-153">Text2</span><span class="sxs-lookup"><span data-stu-id="b2bf0-153">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b2bf0-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2bf0-154">See also</span></span>

- [<span data-ttu-id="b2bf0-155">從 XML 推斷資料集關聯式結構</span><span class="sxs-lookup"><span data-stu-id="b2bf0-155">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="b2bf0-156">從 XML 載入資料集</span><span class="sxs-lookup"><span data-stu-id="b2bf0-156">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [<span data-ttu-id="b2bf0-157">從 XML 載入資料集結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="b2bf0-157">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="b2bf0-158">在 DataSet 中使用 XML</span><span class="sxs-lookup"><span data-stu-id="b2bf0-158">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [<span data-ttu-id="b2bf0-159">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="b2bf0-159">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="b2bf0-160">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="b2bf0-160">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
