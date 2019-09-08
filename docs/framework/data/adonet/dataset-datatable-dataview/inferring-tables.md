---
title: 推斷資料表
ms.date: 03/30/2017
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
ms.openlocfilehash: 52ffd3fe90eb491dd01acf8538276cc828fdb309
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784488"
---
# <a name="inferring-tables"></a><span data-ttu-id="8858b-102">推斷資料表</span><span class="sxs-lookup"><span data-stu-id="8858b-102">Inferring Tables</span></span>
<span data-ttu-id="8858b-103">從 XML 文件推斷 <xref:System.Data.DataSet> 的結構描述時，ADO.NET 首先會決定要用哪些 XML 項目來表示資料表。</span><span class="sxs-lookup"><span data-stu-id="8858b-103">When inferring a schema for a <xref:System.Data.DataSet> from an XML document, ADO.NET first determines which XML elements represent tables.</span></span> <span data-ttu-id="8858b-104">下列 XML 結構會產生**資料集**架構的資料表：</span><span class="sxs-lookup"><span data-stu-id="8858b-104">The following XML structures result in a table for the **DataSet** schema:</span></span>  
  
- <span data-ttu-id="8858b-105">具有屬性的項目</span><span class="sxs-lookup"><span data-stu-id="8858b-105">Elements with attributes</span></span>  
  
- <span data-ttu-id="8858b-106">具有項目子系的項目</span><span class="sxs-lookup"><span data-stu-id="8858b-106">Elements with child elements</span></span>  
  
- <span data-ttu-id="8858b-107">重複項目</span><span class="sxs-lookup"><span data-stu-id="8858b-107">Repeating elements</span></span>  
  
## <a name="elements-with-attributes"></a><span data-ttu-id="8858b-108">具有屬性的項目</span><span class="sxs-lookup"><span data-stu-id="8858b-108">Elements with Attributes</span></span>  
 <span data-ttu-id="8858b-109">具有指定屬性的項目會產生推斷資料表。</span><span class="sxs-lookup"><span data-stu-id="8858b-109">Elements that have attributes specified in them result in inferred tables.</span></span> <span data-ttu-id="8858b-110">例如，請考量下列 XML：</span><span class="sxs-lookup"><span data-stu-id="8858b-110">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="8858b-111">推斷處理序會產生名為 Element1 的資料表。</span><span class="sxs-lookup"><span data-stu-id="8858b-111">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="8858b-112">**集中**DocumentElement</span><span class="sxs-lookup"><span data-stu-id="8858b-112">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="8858b-113">**目錄**Element1</span><span class="sxs-lookup"><span data-stu-id="8858b-113">**Table:** Element1</span></span>  
  
|<span data-ttu-id="8858b-114">attr1</span><span class="sxs-lookup"><span data-stu-id="8858b-114">attr1</span></span>|<span data-ttu-id="8858b-115">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="8858b-115">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="8858b-116">value1</span><span class="sxs-lookup"><span data-stu-id="8858b-116">value1</span></span>||  
|<span data-ttu-id="8858b-117">value2</span><span class="sxs-lookup"><span data-stu-id="8858b-117">value2</span></span>|<span data-ttu-id="8858b-118">Text1</span><span class="sxs-lookup"><span data-stu-id="8858b-118">Text1</span></span>|  
  
## <a name="elements-with-child-elements"></a><span data-ttu-id="8858b-119">具有項目子系的項目</span><span class="sxs-lookup"><span data-stu-id="8858b-119">Elements with Child Elements</span></span>  
 <span data-ttu-id="8858b-120">具有項目子系的項目會產生推斷資料表。</span><span class="sxs-lookup"><span data-stu-id="8858b-120">Elements that have child elements result in inferred tables.</span></span> <span data-ttu-id="8858b-121">例如，請考量下列 XML：</span><span class="sxs-lookup"><span data-stu-id="8858b-121">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="8858b-122">推斷處理序會產生名為 Element1 的資料表。</span><span class="sxs-lookup"><span data-stu-id="8858b-122">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="8858b-123">**集中**DocumentElement</span><span class="sxs-lookup"><span data-stu-id="8858b-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="8858b-124">**目錄**Element1</span><span class="sxs-lookup"><span data-stu-id="8858b-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="8858b-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="8858b-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="8858b-126">Text1</span><span class="sxs-lookup"><span data-stu-id="8858b-126">Text1</span></span>|  
  
 <span data-ttu-id="8858b-127">如果文件或根項目具有將推斷為資料行的屬性或項目子系，便會產生推斷資料表。</span><span class="sxs-lookup"><span data-stu-id="8858b-127">The document, or root, element result in an inferred table if it has attributes or child elements that are inferred as columns.</span></span> <span data-ttu-id="8858b-128">如果 document 專案沒有任何屬性，而且沒有任何子專案會被推斷為數據行，則會將元素推斷為**DataSet**。</span><span class="sxs-lookup"><span data-stu-id="8858b-128">If the document element has no attributes and no child elements that would be inferred as columns, the element is inferred as a **DataSet**.</span></span> <span data-ttu-id="8858b-129">例如，請考量下列 XML：</span><span class="sxs-lookup"><span data-stu-id="8858b-129">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 <span data-ttu-id="8858b-130">推斷處理序會產生名為 DocumentElement 的資料表。</span><span class="sxs-lookup"><span data-stu-id="8858b-130">The inference process produces a table named "DocumentElement."</span></span>  
  
 <span data-ttu-id="8858b-131">**集中**NewDataSet</span><span class="sxs-lookup"><span data-stu-id="8858b-131">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="8858b-132">**目錄**DocumentElement</span><span class="sxs-lookup"><span data-stu-id="8858b-132">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="8858b-133">Element1</span><span class="sxs-lookup"><span data-stu-id="8858b-133">Element1</span></span>|<span data-ttu-id="8858b-134">Element2</span><span class="sxs-lookup"><span data-stu-id="8858b-134">Element2</span></span>|  
|--------------|--------------|  
|<span data-ttu-id="8858b-135">Text1</span><span class="sxs-lookup"><span data-stu-id="8858b-135">Text1</span></span>|<span data-ttu-id="8858b-136">Text2</span><span class="sxs-lookup"><span data-stu-id="8858b-136">Text2</span></span>|  
  
 <span data-ttu-id="8858b-137">另一個方法是考量下列 XML：</span><span class="sxs-lookup"><span data-stu-id="8858b-137">Alternatively, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="8858b-138">推斷進程會產生名為 "DocumentElement" 的**資料集**，其中包含名為 "Element1" 的資料表。</span><span class="sxs-lookup"><span data-stu-id="8858b-138">The inference process produces a **DataSet** named "DocumentElement" that contains a table named "Element1."</span></span>  
  
 <span data-ttu-id="8858b-139">**集中**DocumentElement</span><span class="sxs-lookup"><span data-stu-id="8858b-139">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="8858b-140">**目錄**Element1</span><span class="sxs-lookup"><span data-stu-id="8858b-140">**Table:** Element1</span></span>  
  
|<span data-ttu-id="8858b-141">attr1</span><span class="sxs-lookup"><span data-stu-id="8858b-141">attr1</span></span>|<span data-ttu-id="8858b-142">attr2</span><span class="sxs-lookup"><span data-stu-id="8858b-142">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="8858b-143">value1</span><span class="sxs-lookup"><span data-stu-id="8858b-143">value1</span></span>|<span data-ttu-id="8858b-144">value2</span><span class="sxs-lookup"><span data-stu-id="8858b-144">value2</span></span>|  
  
## <a name="repeating-elements"></a><span data-ttu-id="8858b-145">重複項目</span><span class="sxs-lookup"><span data-stu-id="8858b-145">Repeating Elements</span></span>  
 <span data-ttu-id="8858b-146">重複項目會產生單一推斷資料表。</span><span class="sxs-lookup"><span data-stu-id="8858b-146">Elements that repeat result in a single inferred table.</span></span> <span data-ttu-id="8858b-147">例如，請考量下列 XML：</span><span class="sxs-lookup"><span data-stu-id="8858b-147">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="8858b-148">推斷處理序會產生名為 Element1 的資料表。</span><span class="sxs-lookup"><span data-stu-id="8858b-148">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="8858b-149">**集中**DocumentElement</span><span class="sxs-lookup"><span data-stu-id="8858b-149">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="8858b-150">**目錄**Element1</span><span class="sxs-lookup"><span data-stu-id="8858b-150">**Table:** Element1</span></span>  
  
|<span data-ttu-id="8858b-151">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="8858b-151">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="8858b-152">Text1</span><span class="sxs-lookup"><span data-stu-id="8858b-152">Text1</span></span>|  
|<span data-ttu-id="8858b-153">Text2</span><span class="sxs-lookup"><span data-stu-id="8858b-153">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8858b-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8858b-154">See also</span></span>

- [<span data-ttu-id="8858b-155">從 XML 推斷資料集關聯式結構</span><span class="sxs-lookup"><span data-stu-id="8858b-155">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="8858b-156">從 XML 載入資料集</span><span class="sxs-lookup"><span data-stu-id="8858b-156">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="8858b-157">從 XML 載入資料集結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="8858b-157">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="8858b-158">在 DataSet 中使用 XML</span><span class="sxs-lookup"><span data-stu-id="8858b-158">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="8858b-159">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="8858b-159">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="8858b-160">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="8858b-160">ADO.NET Overview</span></span>](../ado-net-overview.md)
