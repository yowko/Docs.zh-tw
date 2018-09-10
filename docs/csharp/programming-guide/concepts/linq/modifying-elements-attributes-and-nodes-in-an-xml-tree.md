---
title: 修改 XML 樹狀結構中的項目、屬性和節點
ms.date: 07/20/2015
ms.assetid: 0ed22e4e-4c6b-4eb1-b0eb-06685efd8c33
ms.openlocfilehash: 9567d0c6c5cd4853eeb2a86066cd1a805f20a031
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43777346"
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a><span data-ttu-id="9af85-102">修改 XML 樹狀中的項目、屬性和節點</span><span class="sxs-lookup"><span data-stu-id="9af85-102">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>
<span data-ttu-id="9af85-103">下表摘要說明您可以用於修改項目、其子項目或其屬性的方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="9af85-103">The following table summarizes the methods and properties that you can use to modify an element, its child elements, or its attributes.</span></span>  
  
 <span data-ttu-id="9af85-104">下列方法會修改 <xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="9af85-104">The following methods modify an <xref:System.Xml.Linq.XElement>.</span></span>  
  
|<span data-ttu-id="9af85-105">方法</span><span class="sxs-lookup"><span data-stu-id="9af85-105">Method</span></span>|<span data-ttu-id="9af85-106">描述</span><span class="sxs-lookup"><span data-stu-id="9af85-106">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|<span data-ttu-id="9af85-107">以剖析的 XML 取代項目。</span><span class="sxs-lookup"><span data-stu-id="9af85-107">Replaces an element with parsed XML.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="9af85-108">移除項目的所有內容 (子節點和屬性)。</span><span class="sxs-lookup"><span data-stu-id="9af85-108">Removes all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="9af85-109">移除項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="9af85-109">Removes the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|<span data-ttu-id="9af85-110">取代項目的所有內容 (子節點和屬性)。</span><span class="sxs-lookup"><span data-stu-id="9af85-110">Replaces all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="9af85-111">取代項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="9af85-111">Replaces the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="9af85-112">設定屬性的值。</span><span class="sxs-lookup"><span data-stu-id="9af85-112">Sets the value of an attribute.</span></span> <span data-ttu-id="9af85-113">建立屬性 (如果不存在)。</span><span class="sxs-lookup"><span data-stu-id="9af85-113">Creates the attribute if it doesn't exist.</span></span> <span data-ttu-id="9af85-114">如果值設定為 `null`，移除屬性。</span><span class="sxs-lookup"><span data-stu-id="9af85-114">If the value is set to `null`, removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="9af85-115">設定子項目的值。</span><span class="sxs-lookup"><span data-stu-id="9af85-115">Sets the value of a child element.</span></span> <span data-ttu-id="9af85-116">建立項目 (如果不存在)。</span><span class="sxs-lookup"><span data-stu-id="9af85-116">Creates the element if it doesn't exist.</span></span> <span data-ttu-id="9af85-117">如果值設定為 `null`，移除項目。</span><span class="sxs-lookup"><span data-stu-id="9af85-117">If the value is set to `null`, removes the element.</span></span>|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="9af85-118">以指定的文字取代項目的內容 (子節點)。</span><span class="sxs-lookup"><span data-stu-id="9af85-118">Replaces the content (child nodes) of an element with the specified text.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="9af85-119">設定項目的值。</span><span class="sxs-lookup"><span data-stu-id="9af85-119">Sets the value of an element.</span></span>|  
  
 <span data-ttu-id="9af85-120">下列方法會修改 <xref:System.Xml.Linq.XAttribute>。</span><span class="sxs-lookup"><span data-stu-id="9af85-120">The following methods modify an <xref:System.Xml.Linq.XAttribute>.</span></span>  
  
|<span data-ttu-id="9af85-121">方法</span><span class="sxs-lookup"><span data-stu-id="9af85-121">Method</span></span>|<span data-ttu-id="9af85-122">描述</span><span class="sxs-lookup"><span data-stu-id="9af85-122">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="9af85-123">設定屬性的值。</span><span class="sxs-lookup"><span data-stu-id="9af85-123">Sets the value of an attribute.</span></span>|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="9af85-124">設定屬性的值。</span><span class="sxs-lookup"><span data-stu-id="9af85-124">Sets the value of an attribute.</span></span>|  
  
 <span data-ttu-id="9af85-125">下列方法會修改 <xref:System.Xml.Linq.XNode> (包括 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument>)。</span><span class="sxs-lookup"><span data-stu-id="9af85-125">The following methods modify an <xref:System.Xml.Linq.XNode> (including an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="9af85-126">方法</span><span class="sxs-lookup"><span data-stu-id="9af85-126">Method</span></span>|<span data-ttu-id="9af85-127">描述</span><span class="sxs-lookup"><span data-stu-id="9af85-127">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|<span data-ttu-id="9af85-128">以新內容取代節點。</span><span class="sxs-lookup"><span data-stu-id="9af85-128">Replaces a node with new content.</span></span>|  
  
 <span data-ttu-id="9af85-129">下列方法會修改 <xref:System.Xml.Linq.XContainer> (<xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument>)。</span><span class="sxs-lookup"><span data-stu-id="9af85-129">The following methods modify an <xref:System.Xml.Linq.XContainer> (an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="9af85-130">方法</span><span class="sxs-lookup"><span data-stu-id="9af85-130">Method</span></span>|<span data-ttu-id="9af85-131">描述</span><span class="sxs-lookup"><span data-stu-id="9af85-131">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="9af85-132">以新的內容取代子節點。</span><span class="sxs-lookup"><span data-stu-id="9af85-132">Replaces the children nodes with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9af85-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="9af85-133">See Also</span></span>

- [<span data-ttu-id="9af85-134">修改 XML 樹狀結構 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="9af85-134">Modifying XML Trees (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
