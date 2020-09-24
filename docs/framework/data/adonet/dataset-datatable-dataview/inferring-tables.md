---
title: 推斷資料表
ms.date: 03/30/2017
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
ms.openlocfilehash: 4a3d7b239dbc405cf2acae967b5be401dc772e38
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177549"
---
# <a name="inferring-tables"></a><span data-ttu-id="71fb7-102">推斷資料表</span><span class="sxs-lookup"><span data-stu-id="71fb7-102">Inferring Tables</span></span>

<span data-ttu-id="71fb7-103">從 XML 文件推斷 <xref:System.Data.DataSet> 的結構描述時，ADO.NET 首先會決定要用哪些 XML 項目來表示資料表。</span><span class="sxs-lookup"><span data-stu-id="71fb7-103">When inferring a schema for a <xref:System.Data.DataSet> from an XML document, ADO.NET first determines which XML elements represent tables.</span></span> <span data-ttu-id="71fb7-104">下列 XML 結構會產生 **資料集** 架構的資料表：</span><span class="sxs-lookup"><span data-stu-id="71fb7-104">The following XML structures result in a table for the **DataSet** schema:</span></span>  
  
- <span data-ttu-id="71fb7-105">具有屬性的項目</span><span class="sxs-lookup"><span data-stu-id="71fb7-105">Elements with attributes</span></span>  
  
- <span data-ttu-id="71fb7-106">具有項目子系的項目</span><span class="sxs-lookup"><span data-stu-id="71fb7-106">Elements with child elements</span></span>  
  
- <span data-ttu-id="71fb7-107">重複項目</span><span class="sxs-lookup"><span data-stu-id="71fb7-107">Repeating elements</span></span>  
  
## <a name="elements-with-attributes"></a><span data-ttu-id="71fb7-108">具有屬性的項目</span><span class="sxs-lookup"><span data-stu-id="71fb7-108">Elements with Attributes</span></span>  

 <span data-ttu-id="71fb7-109">具有指定屬性的項目會產生推斷資料表。</span><span class="sxs-lookup"><span data-stu-id="71fb7-109">Elements that have attributes specified in them result in inferred tables.</span></span> <span data-ttu-id="71fb7-110">例如，請考量下列 XML：</span><span class="sxs-lookup"><span data-stu-id="71fb7-110">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="71fb7-111">推斷處理序會產生名為 Element1 的資料表。</span><span class="sxs-lookup"><span data-stu-id="71fb7-111">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="71fb7-112">**資料集：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="71fb7-112">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="71fb7-113">**資料表：** Element1</span><span class="sxs-lookup"><span data-stu-id="71fb7-113">**Table:** Element1</span></span>  
  
|<span data-ttu-id="71fb7-114">attr1</span><span class="sxs-lookup"><span data-stu-id="71fb7-114">attr1</span></span>|<span data-ttu-id="71fb7-115">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="71fb7-115">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="71fb7-116">value1</span><span class="sxs-lookup"><span data-stu-id="71fb7-116">value1</span></span>||  
|<span data-ttu-id="71fb7-117">value2</span><span class="sxs-lookup"><span data-stu-id="71fb7-117">value2</span></span>|<span data-ttu-id="71fb7-118">Text1</span><span class="sxs-lookup"><span data-stu-id="71fb7-118">Text1</span></span>|  
  
## <a name="elements-with-child-elements"></a><span data-ttu-id="71fb7-119">具有項目子系的項目</span><span class="sxs-lookup"><span data-stu-id="71fb7-119">Elements with Child Elements</span></span>  

 <span data-ttu-id="71fb7-120">具有項目子系的項目會產生推斷資料表。</span><span class="sxs-lookup"><span data-stu-id="71fb7-120">Elements that have child elements result in inferred tables.</span></span> <span data-ttu-id="71fb7-121">例如，請考量下列 XML：</span><span class="sxs-lookup"><span data-stu-id="71fb7-121">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="71fb7-122">推斷處理序會產生名為 Element1 的資料表。</span><span class="sxs-lookup"><span data-stu-id="71fb7-122">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="71fb7-123">**資料集：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="71fb7-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="71fb7-124">**資料表：** Element1</span><span class="sxs-lookup"><span data-stu-id="71fb7-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="71fb7-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="71fb7-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="71fb7-126">Text1</span><span class="sxs-lookup"><span data-stu-id="71fb7-126">Text1</span></span>|  
  
 <span data-ttu-id="71fb7-127">如果文件或根項目具有將推斷為資料行的屬性或項目子系，便會產生推斷資料表。</span><span class="sxs-lookup"><span data-stu-id="71fb7-127">The document, or root, element result in an inferred table if it has attributes or child elements that are inferred as columns.</span></span> <span data-ttu-id="71fb7-128">如果 document 元素沒有任何屬性，而且沒有任何子項目會被推斷為數據行，則會將該元素推斷為 **資料集**。</span><span class="sxs-lookup"><span data-stu-id="71fb7-128">If the document element has no attributes and no child elements that would be inferred as columns, the element is inferred as a **DataSet**.</span></span> <span data-ttu-id="71fb7-129">例如，請考量下列 XML：</span><span class="sxs-lookup"><span data-stu-id="71fb7-129">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 <span data-ttu-id="71fb7-130">推斷處理序會產生名為 DocumentElement 的資料表。</span><span class="sxs-lookup"><span data-stu-id="71fb7-130">The inference process produces a table named "DocumentElement."</span></span>  
  
 <span data-ttu-id="71fb7-131">**資料集：** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="71fb7-131">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="71fb7-132">**資料表：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="71fb7-132">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="71fb7-133">Element1</span><span class="sxs-lookup"><span data-stu-id="71fb7-133">Element1</span></span>|<span data-ttu-id="71fb7-134">Element2</span><span class="sxs-lookup"><span data-stu-id="71fb7-134">Element2</span></span>|  
|--------------|--------------|  
|<span data-ttu-id="71fb7-135">Text1</span><span class="sxs-lookup"><span data-stu-id="71fb7-135">Text1</span></span>|<span data-ttu-id="71fb7-136">Text2</span><span class="sxs-lookup"><span data-stu-id="71fb7-136">Text2</span></span>|  
  
 <span data-ttu-id="71fb7-137">另一個方法是考量下列 XML：</span><span class="sxs-lookup"><span data-stu-id="71fb7-137">Alternatively, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="71fb7-138">推斷進程會產生名為 "DocumentElement" 的 **資料集** ，其中包含名為 "Element1" 的資料表。</span><span class="sxs-lookup"><span data-stu-id="71fb7-138">The inference process produces a **DataSet** named "DocumentElement" that contains a table named "Element1."</span></span>  
  
 <span data-ttu-id="71fb7-139">**資料集：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="71fb7-139">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="71fb7-140">**資料表：** Element1</span><span class="sxs-lookup"><span data-stu-id="71fb7-140">**Table:** Element1</span></span>  
  
|<span data-ttu-id="71fb7-141">attr1</span><span class="sxs-lookup"><span data-stu-id="71fb7-141">attr1</span></span>|<span data-ttu-id="71fb7-142">attr2</span><span class="sxs-lookup"><span data-stu-id="71fb7-142">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="71fb7-143">value1</span><span class="sxs-lookup"><span data-stu-id="71fb7-143">value1</span></span>|<span data-ttu-id="71fb7-144">value2</span><span class="sxs-lookup"><span data-stu-id="71fb7-144">value2</span></span>|  
  
## <a name="repeating-elements"></a><span data-ttu-id="71fb7-145">重複項目</span><span class="sxs-lookup"><span data-stu-id="71fb7-145">Repeating Elements</span></span>  

 <span data-ttu-id="71fb7-146">重複項目會產生單一推斷資料表。</span><span class="sxs-lookup"><span data-stu-id="71fb7-146">Elements that repeat result in a single inferred table.</span></span> <span data-ttu-id="71fb7-147">例如，請考量下列 XML：</span><span class="sxs-lookup"><span data-stu-id="71fb7-147">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="71fb7-148">推斷處理序會產生名為 Element1 的資料表。</span><span class="sxs-lookup"><span data-stu-id="71fb7-148">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="71fb7-149">**資料集：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="71fb7-149">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="71fb7-150">**資料表：** Element1</span><span class="sxs-lookup"><span data-stu-id="71fb7-150">**Table:** Element1</span></span>  
  
|<span data-ttu-id="71fb7-151">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="71fb7-151">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="71fb7-152">Text1</span><span class="sxs-lookup"><span data-stu-id="71fb7-152">Text1</span></span>|  
|<span data-ttu-id="71fb7-153">Text2</span><span class="sxs-lookup"><span data-stu-id="71fb7-153">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="71fb7-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71fb7-154">See also</span></span>

- [<span data-ttu-id="71fb7-155">從 XML 推斷資料集關聯式結構</span><span class="sxs-lookup"><span data-stu-id="71fb7-155">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="71fb7-156">從 XML 載入資料集</span><span class="sxs-lookup"><span data-stu-id="71fb7-156">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="71fb7-157">從 XML 載入資料集結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="71fb7-157">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="71fb7-158">在資料集中使用 XML</span><span class="sxs-lookup"><span data-stu-id="71fb7-158">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="71fb7-159">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="71fb7-159">DataSets, DataTables, and DataViews</span></span>](index.md)
- <span data-ttu-id="71fb7-160">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="71fb7-160">[ADO.NET Overview](../ado-net-overview.md)</span></span>
