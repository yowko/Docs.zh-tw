---
title: 修改 XML 樹狀中的項目、屬性和節點
description: 瞭解您可以用來修改元素、其子節點或其屬性的方法和屬性。
ms.date: 07/20/2015
ms.assetid: 0ed22e4e-4c6b-4eb1-b0eb-06685efd8c33
ms.openlocfilehash: bfff882dc57a4f6f4b228563ac923122097d88d0
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303162"
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a><span data-ttu-id="630d6-103">修改 XML 樹狀中的項目、屬性和節點</span><span class="sxs-lookup"><span data-stu-id="630d6-103">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>
<span data-ttu-id="630d6-104">下表摘要說明您可以用於修改項目、其子項目或其屬性的方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="630d6-104">The following table summarizes the methods and properties that you can use to modify an element, its child elements, or its attributes.</span></span>  
  
 <span data-ttu-id="630d6-105">下列方法會修改 <xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="630d6-105">The following methods modify an <xref:System.Xml.Linq.XElement>.</span></span>  
  
|<span data-ttu-id="630d6-106">方法</span><span class="sxs-lookup"><span data-stu-id="630d6-106">Method</span></span>|<span data-ttu-id="630d6-107">描述</span><span class="sxs-lookup"><span data-stu-id="630d6-107">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|<span data-ttu-id="630d6-108">以剖析的 XML 取代項目。</span><span class="sxs-lookup"><span data-stu-id="630d6-108">Replaces an element with parsed XML.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="630d6-109">移除項目的所有內容 (子節點和屬性)。</span><span class="sxs-lookup"><span data-stu-id="630d6-109">Removes all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="630d6-110">移除項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="630d6-110">Removes the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|<span data-ttu-id="630d6-111">取代項目的所有內容 (子節點和屬性)。</span><span class="sxs-lookup"><span data-stu-id="630d6-111">Replaces all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="630d6-112">取代項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="630d6-112">Replaces the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="630d6-113">設定屬性的值。</span><span class="sxs-lookup"><span data-stu-id="630d6-113">Sets the value of an attribute.</span></span> <span data-ttu-id="630d6-114">建立屬性 (如果不存在)。</span><span class="sxs-lookup"><span data-stu-id="630d6-114">Creates the attribute if it doesn't exist.</span></span> <span data-ttu-id="630d6-115">如果值設定為 `null`，移除屬性。</span><span class="sxs-lookup"><span data-stu-id="630d6-115">If the value is set to `null`, removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="630d6-116">設定子項目的值。</span><span class="sxs-lookup"><span data-stu-id="630d6-116">Sets the value of a child element.</span></span> <span data-ttu-id="630d6-117">建立項目 (如果不存在)。</span><span class="sxs-lookup"><span data-stu-id="630d6-117">Creates the element if it doesn't exist.</span></span> <span data-ttu-id="630d6-118">如果值設定為 `null`，移除項目。</span><span class="sxs-lookup"><span data-stu-id="630d6-118">If the value is set to `null`, removes the element.</span></span>|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="630d6-119">以指定的文字取代項目的內容 (子節點)。</span><span class="sxs-lookup"><span data-stu-id="630d6-119">Replaces the content (child nodes) of an element with the specified text.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="630d6-120">設定項目的值。</span><span class="sxs-lookup"><span data-stu-id="630d6-120">Sets the value of an element.</span></span>|  
  
 <span data-ttu-id="630d6-121">下列方法會修改 <xref:System.Xml.Linq.XAttribute>。</span><span class="sxs-lookup"><span data-stu-id="630d6-121">The following methods modify an <xref:System.Xml.Linq.XAttribute>.</span></span>  
  
|<span data-ttu-id="630d6-122">方法</span><span class="sxs-lookup"><span data-stu-id="630d6-122">Method</span></span>|<span data-ttu-id="630d6-123">描述</span><span class="sxs-lookup"><span data-stu-id="630d6-123">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="630d6-124">設定屬性的值。</span><span class="sxs-lookup"><span data-stu-id="630d6-124">Sets the value of an attribute.</span></span>|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="630d6-125">設定屬性的值。</span><span class="sxs-lookup"><span data-stu-id="630d6-125">Sets the value of an attribute.</span></span>|  
  
 <span data-ttu-id="630d6-126">下列方法會修改 <xref:System.Xml.Linq.XNode> (包括 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument>)。</span><span class="sxs-lookup"><span data-stu-id="630d6-126">The following methods modify an <xref:System.Xml.Linq.XNode> (including an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="630d6-127">方法</span><span class="sxs-lookup"><span data-stu-id="630d6-127">Method</span></span>|<span data-ttu-id="630d6-128">描述</span><span class="sxs-lookup"><span data-stu-id="630d6-128">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|<span data-ttu-id="630d6-129">以新內容取代節點。</span><span class="sxs-lookup"><span data-stu-id="630d6-129">Replaces a node with new content.</span></span>|  
  
 <span data-ttu-id="630d6-130">下列方法會修改 <xref:System.Xml.Linq.XContainer> (<xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument>)。</span><span class="sxs-lookup"><span data-stu-id="630d6-130">The following methods modify an <xref:System.Xml.Linq.XContainer> (an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="630d6-131">方法</span><span class="sxs-lookup"><span data-stu-id="630d6-131">Method</span></span>|<span data-ttu-id="630d6-132">描述</span><span class="sxs-lookup"><span data-stu-id="630d6-132">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="630d6-133">以新的內容取代子節點。</span><span class="sxs-lookup"><span data-stu-id="630d6-133">Replaces the children nodes with new content.</span></span>|  
