---
title: "修改項目、 屬性和節點在 XML Tree1 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 865cf54e-f8ac-4871-863b-a3e6fc61a4b9
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 88531f2af88074f4406c4859354860829efda69f
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017


---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a><span data-ttu-id="8e10a-102">修改 XML 樹狀中的項目、屬性和節點</span><span class="sxs-lookup"><span data-stu-id="8e10a-102">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>
<span data-ttu-id="8e10a-103">下表摘要說明您可以用於修改項目、其子項目或其屬性的方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="8e10a-103">The following table summarizes the methods and properties that you can use to modify an element, its child elements, or its attributes.</span></span>  
  
 <span data-ttu-id="8e10a-104">下列方法修改<xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="8e10a-104">The following methods modify an <xref:System.Xml.Linq.XElement>.</span></span>  
  
|<span data-ttu-id="8e10a-105">方法</span><span class="sxs-lookup"><span data-stu-id="8e10a-105">Method</span></span>|<span data-ttu-id="8e10a-106">描述</span><span class="sxs-lookup"><span data-stu-id="8e10a-106">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="8e10a-107"><xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="8e10a-107"><xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName></span></span>|<span data-ttu-id="8e10a-108">以剖析的 XML 取代項目。</span><span class="sxs-lookup"><span data-stu-id="8e10a-108">Replaces an element with parsed XML.</span></span>|  
|<span data-ttu-id="8e10a-109"><xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="8e10a-109"><xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=fullName></span></span>|<span data-ttu-id="8e10a-110">移除項目的所有內容 (子節點和屬性)。</span><span class="sxs-lookup"><span data-stu-id="8e10a-110">Removes all content (child nodes and attributes) of an element.</span></span>|  
|<span data-ttu-id="8e10a-111"><xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="8e10a-111"><xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=fullName></span></span>|<span data-ttu-id="8e10a-112">移除項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="8e10a-112">Removes the attributes of an element.</span></span>|  
|<span data-ttu-id="8e10a-113"><xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="8e10a-113"><xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=fullName></span></span>|<span data-ttu-id="8e10a-114">取代項目的所有內容 (子節點和屬性)。</span><span class="sxs-lookup"><span data-stu-id="8e10a-114">Replaces all content (child nodes and attributes) of an element.</span></span>|  
|<span data-ttu-id="8e10a-115"><xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="8e10a-115"><xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=fullName></span></span>|<span data-ttu-id="8e10a-116">取代項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="8e10a-116">Replaces the attributes of an element.</span></span>|  
|<span data-ttu-id="8e10a-117"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="8e10a-117"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=fullName></span></span>|<span data-ttu-id="8e10a-118">設定屬性的值。</span><span class="sxs-lookup"><span data-stu-id="8e10a-118">Sets the value of an attribute.</span></span> <span data-ttu-id="8e10a-119">建立屬性 (如果不存在)。</span><span class="sxs-lookup"><span data-stu-id="8e10a-119">Creates the attribute if it doesn't exist.</span></span> <span data-ttu-id="8e10a-120">如果值設定為 `null`，移除屬性。</span><span class="sxs-lookup"><span data-stu-id="8e10a-120">If the value is set to `null`, removes the attribute.</span></span>|  
|<span data-ttu-id="8e10a-121"><xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="8e10a-121"><xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=fullName></span></span>|<span data-ttu-id="8e10a-122">設定子項目的值。</span><span class="sxs-lookup"><span data-stu-id="8e10a-122">Sets the value of a child element.</span></span> <span data-ttu-id="8e10a-123">建立項目 (如果不存在)。</span><span class="sxs-lookup"><span data-stu-id="8e10a-123">Creates the element if it doesn't exist.</span></span> <span data-ttu-id="8e10a-124">如果值設定為 `null`，移除項目。</span><span class="sxs-lookup"><span data-stu-id="8e10a-124">If the value is set to `null`, removes the element.</span></span>|  
|<span data-ttu-id="8e10a-125"><xref:System.Xml.Linq.XElement.Value%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Value%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="8e10a-125"><xref:System.Xml.Linq.XElement.Value%2A?displayProperty=fullName></span></span>|<span data-ttu-id="8e10a-126">以指定的文字取代項目的內容 (子節點)。</span><span class="sxs-lookup"><span data-stu-id="8e10a-126">Replaces the content (child nodes) of an element with the specified text.</span></span>|  
|<span data-ttu-id="8e10a-127"><xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="8e10a-127"><xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=fullName></span></span>|<span data-ttu-id="8e10a-128">設定項目的值。</span><span class="sxs-lookup"><span data-stu-id="8e10a-128">Sets the value of an element.</span></span>|  
  
 <span data-ttu-id="8e10a-129">下列方法修改<xref:System.Xml.Linq.XAttribute>.</xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="8e10a-129">The following methods modify an <xref:System.Xml.Linq.XAttribute>.</span></span>  
  
|<span data-ttu-id="8e10a-130">方法</span><span class="sxs-lookup"><span data-stu-id="8e10a-130">Method</span></span>|<span data-ttu-id="8e10a-131">描述</span><span class="sxs-lookup"><span data-stu-id="8e10a-131">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="8e10a-132"><xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="8e10a-132"><xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName></span></span>|<span data-ttu-id="8e10a-133">設定屬性的值。</span><span class="sxs-lookup"><span data-stu-id="8e10a-133">Sets the value of an attribute.</span></span>|  
|<span data-ttu-id="8e10a-134"><xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=fullName></xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="8e10a-134"><xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=fullName></span></span>|<span data-ttu-id="8e10a-135">設定屬性的值。</span><span class="sxs-lookup"><span data-stu-id="8e10a-135">Sets the value of an attribute.</span></span>|  
  
 <span data-ttu-id="8e10a-136">下列方法修改<xref:System.Xml.Linq.XNode>(包括<xref:System.Xml.Linq.XElement>或<xref:System.Xml.Linq.XDocument>)。</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XNode></span><span class="sxs-lookup"><span data-stu-id="8e10a-136">The following methods modify an <xref:System.Xml.Linq.XNode> (including an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="8e10a-137">方法</span><span class="sxs-lookup"><span data-stu-id="8e10a-137">Method</span></span>|<span data-ttu-id="8e10a-138">說明</span><span class="sxs-lookup"><span data-stu-id="8e10a-138">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="8e10a-139"><xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=fullName></xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="8e10a-139"><xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=fullName></span></span>|<span data-ttu-id="8e10a-140">以新內容取代節點。</span><span class="sxs-lookup"><span data-stu-id="8e10a-140">Replaces a node with new content.</span></span>|  
  
 <span data-ttu-id="8e10a-141">下列方法修改<xref:System.Xml.Linq.XContainer>(<xref:System.Xml.Linq.XElement>或<xref:System.Xml.Linq.XDocument>)。</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XContainer></span><span class="sxs-lookup"><span data-stu-id="8e10a-141">The following methods modify an <xref:System.Xml.Linq.XContainer> (an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="8e10a-142">方法</span><span class="sxs-lookup"><span data-stu-id="8e10a-142">Method</span></span>|<span data-ttu-id="8e10a-143">描述</span><span class="sxs-lookup"><span data-stu-id="8e10a-143">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="8e10a-144"><xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=fullName></xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="8e10a-144"><xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=fullName></span></span>|<span data-ttu-id="8e10a-145">以新的內容取代子節點。</span><span class="sxs-lookup"><span data-stu-id="8e10a-145">Replaces the children nodes with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8e10a-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e10a-146">See Also</span></span>  
 [<span data-ttu-id="8e10a-147">修改 XML 樹狀結構 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e10a-147">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
