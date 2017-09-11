---
title: "修改 XML Tree3 中的項目、屬性和節點 | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 0ed22e4e-4c6b-4eb1-b0eb-06685efd8c33
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6fa51b22af73d716b01444540edb7c8d814cd293
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017


---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a><span data-ttu-id="4a018-102">修改 XML 樹狀中的項目、屬性和節點</span><span class="sxs-lookup"><span data-stu-id="4a018-102">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>
<span data-ttu-id="4a018-103">下表摘要說明您可以用於修改項目、其子項目或其屬性的方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="4a018-103">The following table summarizes the methods and properties that you can use to modify an element, its child elements, or its attributes.</span></span>  
  
 <span data-ttu-id="4a018-104">下列方法會修改 <xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="4a018-104">The following methods modify an <xref:System.Xml.Linq.XElement>.</span></span>  
  
|<span data-ttu-id="4a018-105">方法</span><span class="sxs-lookup"><span data-stu-id="4a018-105">Method</span></span>|<span data-ttu-id="4a018-106">描述</span><span class="sxs-lookup"><span data-stu-id="4a018-106">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4a018-107"><xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4a018-107"><xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName></span></span>|<span data-ttu-id="4a018-108">以剖析的 XML 取代項目。</span><span class="sxs-lookup"><span data-stu-id="4a018-108">Replaces an element with parsed XML.</span></span>|  
|<span data-ttu-id="4a018-109"><xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4a018-109"><xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=fullName></span></span>|<span data-ttu-id="4a018-110">移除項目的所有內容 (子節點和屬性)。</span><span class="sxs-lookup"><span data-stu-id="4a018-110">Removes all content (child nodes and attributes) of an element.</span></span>|  
|<span data-ttu-id="4a018-111"><xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4a018-111"><xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=fullName></span></span>|<span data-ttu-id="4a018-112">移除項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="4a018-112">Removes the attributes of an element.</span></span>|  
|<span data-ttu-id="4a018-113"><xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4a018-113"><xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=fullName></span></span>|<span data-ttu-id="4a018-114">取代項目的所有內容 (子節點和屬性)。</span><span class="sxs-lookup"><span data-stu-id="4a018-114">Replaces all content (child nodes and attributes) of an element.</span></span>|  
|<span data-ttu-id="4a018-115"><xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4a018-115"><xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=fullName></span></span>|<span data-ttu-id="4a018-116">取代項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="4a018-116">Replaces the attributes of an element.</span></span>|  
|<span data-ttu-id="4a018-117"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4a018-117"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=fullName></span></span>|<span data-ttu-id="4a018-118">設定屬性的值。</span><span class="sxs-lookup"><span data-stu-id="4a018-118">Sets the value of an attribute.</span></span> <span data-ttu-id="4a018-119">建立屬性 (如果不存在)。</span><span class="sxs-lookup"><span data-stu-id="4a018-119">Creates the attribute if it doesn't exist.</span></span> <span data-ttu-id="4a018-120">如果值設定為 `null`，移除屬性。</span><span class="sxs-lookup"><span data-stu-id="4a018-120">If the value is set to `null`, removes the attribute.</span></span>|  
|<span data-ttu-id="4a018-121"><xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4a018-121"><xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=fullName></span></span>|<span data-ttu-id="4a018-122">設定子項目的值。</span><span class="sxs-lookup"><span data-stu-id="4a018-122">Sets the value of a child element.</span></span> <span data-ttu-id="4a018-123">建立項目 (如果不存在)。</span><span class="sxs-lookup"><span data-stu-id="4a018-123">Creates the element if it doesn't exist.</span></span> <span data-ttu-id="4a018-124">如果值設定為 `null`，移除項目。</span><span class="sxs-lookup"><span data-stu-id="4a018-124">If the value is set to `null`, removes the element.</span></span>|  
|<span data-ttu-id="4a018-125"><xref:System.Xml.Linq.XElement.Value%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4a018-125"><xref:System.Xml.Linq.XElement.Value%2A?displayProperty=fullName></span></span>|<span data-ttu-id="4a018-126">以指定的文字取代項目的內容 (子節點)。</span><span class="sxs-lookup"><span data-stu-id="4a018-126">Replaces the content (child nodes) of an element with the specified text.</span></span>|  
|<span data-ttu-id="4a018-127"><xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4a018-127"><xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=fullName></span></span>|<span data-ttu-id="4a018-128">設定項目的值。</span><span class="sxs-lookup"><span data-stu-id="4a018-128">Sets the value of an element.</span></span>|  
  
 <span data-ttu-id="4a018-129">下列方法會修改 <xref:System.Xml.Linq.XAttribute>。</span><span class="sxs-lookup"><span data-stu-id="4a018-129">The following methods modify an <xref:System.Xml.Linq.XAttribute>.</span></span>  
  
|<span data-ttu-id="4a018-130">方法</span><span class="sxs-lookup"><span data-stu-id="4a018-130">Method</span></span>|<span data-ttu-id="4a018-131">描述</span><span class="sxs-lookup"><span data-stu-id="4a018-131">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4a018-132"><xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4a018-132"><xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName></span></span>|<span data-ttu-id="4a018-133">設定屬性的值。</span><span class="sxs-lookup"><span data-stu-id="4a018-133">Sets the value of an attribute.</span></span>|  
|<span data-ttu-id="4a018-134"><xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4a018-134"><xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=fullName></span></span>|<span data-ttu-id="4a018-135">設定屬性的值。</span><span class="sxs-lookup"><span data-stu-id="4a018-135">Sets the value of an attribute.</span></span>|  
  
 <span data-ttu-id="4a018-136">下列方法會修改 <xref:System.Xml.Linq.XNode> (包括 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument>)。</span><span class="sxs-lookup"><span data-stu-id="4a018-136">The following methods modify an <xref:System.Xml.Linq.XNode> (including an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="4a018-137">方法</span><span class="sxs-lookup"><span data-stu-id="4a018-137">Method</span></span>|<span data-ttu-id="4a018-138">說明</span><span class="sxs-lookup"><span data-stu-id="4a018-138">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4a018-139"><xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4a018-139"><xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=fullName></span></span>|<span data-ttu-id="4a018-140">以新內容取代節點。</span><span class="sxs-lookup"><span data-stu-id="4a018-140">Replaces a node with new content.</span></span>|  
  
 <span data-ttu-id="4a018-141">下列方法會修改 <xref:System.Xml.Linq.XContainer> (<xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument>)。</span><span class="sxs-lookup"><span data-stu-id="4a018-141">The following methods modify an <xref:System.Xml.Linq.XContainer> (an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="4a018-142">方法</span><span class="sxs-lookup"><span data-stu-id="4a018-142">Method</span></span>|<span data-ttu-id="4a018-143">描述</span><span class="sxs-lookup"><span data-stu-id="4a018-143">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4a018-144"><xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4a018-144"><xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=fullName></span></span>|<span data-ttu-id="4a018-145">以新的內容取代子節點。</span><span class="sxs-lookup"><span data-stu-id="4a018-145">Replaces the children nodes with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4a018-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a018-146">See Also</span></span>  
 [<span data-ttu-id="4a018-147">修改 XML 樹狀結構 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="4a018-147">Modifying XML Trees (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
