---
title: "使用 XPathNavigator 巡覽屬性及命名空間節點"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 23975f88-e0af-4b88-93de-9e20e11880ad
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2f86abb7da5509a80cceede0f1092a75cef4d8da
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="attribute-and-namespace-node-navigation-using-xpathnavigator"></a><span data-ttu-id="7794b-102">使用 XPathNavigator 巡覽屬性及命名空間節點</span><span class="sxs-lookup"><span data-stu-id="7794b-102">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>
<span data-ttu-id="7794b-103"><xref:System.Xml.XPath.XPathNavigator> 類別提供兩組巡覽方法，第一組 (可在[使用 XPathNavigator 巡覽節點集](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)主題中找到) 用於巡覽 <xref:System.Xml.XPath.XPathDocument> 或 <xref:System.Xml.XmlDocument> 物件中的*節點集*。</span><span class="sxs-lookup"><span data-stu-id="7794b-103">The <xref:System.Xml.XPath.XPathNavigator> class provides two sets of navigation methods, the first set, found in the [Node Set Navigation Using XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) topic, are used to navigate *node sets* in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="7794b-104">第二組 (在本主題中說明) 用於巡覽 <xref:System.Xml.XPath.XPathDocument> 或 <xref:System.Xml.XmlDocument> 物件中的「屬性及命名空間節點」。</span><span class="sxs-lookup"><span data-stu-id="7794b-104">The second set, described in this topic, are used to navigate *attribute and namespace nodes* in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object.</span></span>  
  
## <a name="attribute-node-navigation"></a><span data-ttu-id="7794b-105">屬性節點巡覽</span><span class="sxs-lookup"><span data-stu-id="7794b-105">Attribute Node Navigation</span></span>  
 <span data-ttu-id="7794b-106">屬性 (Attribute) 是項目的屬性 (Property)，而不是項目的子系。</span><span class="sxs-lookup"><span data-stu-id="7794b-106">Attributes are properties of an element, not children of an element.</span></span> <span data-ttu-id="7794b-107">這個差別是很重要的，因為這關係到用來巡覽同層級節點、父節點及子節點之 <xref:System.Xml.XPath.XPathNavigator> 類別的方法。</span><span class="sxs-lookup"><span data-stu-id="7794b-107">This distinction is important, because of the methods of the <xref:System.Xml.XPath.XPathNavigator> class used to navigate sibling, parent, and child nodes.</span></span>  
  
 <span data-ttu-id="7794b-108">例如，<xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> 及 <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> 方法無法用來從項目巡覽到屬性，或在屬性之間巡覽。</span><span class="sxs-lookup"><span data-stu-id="7794b-108">For example, the <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> and <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> methods are not used to navigate from an element to an attribute or between attributes.</span></span> <span data-ttu-id="7794b-109">應改用不同的方法來巡覽屬性。</span><span class="sxs-lookup"><span data-stu-id="7794b-109">Instead, attributes have distinct methods of navigation.</span></span>  
  
 <span data-ttu-id="7794b-110">以下是 <xref:System.Xml.XPath.XPathNavigator> 類別的屬性巡覽方法。</span><span class="sxs-lookup"><span data-stu-id="7794b-110">The following are the attribute navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToAttribute%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirstAttribute%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToNextAttribute%2A>  
  
 <span data-ttu-id="7794b-111">當目前的節點為項目時，您可以使用 <xref:System.Xml.XPath.XPathNavigator.HasAttributes%2A> 屬性 (Property)，來查看是否有與項目相關的屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="7794b-111">When the current node is an element, you can use the <xref:System.Xml.XPath.XPathNavigator.HasAttributes%2A> property to see if there are any attributes associated with the element.</span></span> <span data-ttu-id="7794b-112">一旦知道項目有屬性，就有多種存取屬性的方法。</span><span class="sxs-lookup"><span data-stu-id="7794b-112">After it is known that an element has attributes, there are multiple methods for accessing attributes.</span></span> <span data-ttu-id="7794b-113">若要從項目擷取單一屬性，請使用 <xref:System.Xml.XPath.XPathNavigator.GetAttribute%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="7794b-113">To retrieve a single attribute from the element, use the <xref:System.Xml.XPath.XPathNavigator.GetAttribute%2A> method.</span></span> <span data-ttu-id="7794b-114">若要將 <xref:System.Xml.XPath.XPathNavigator> 移至特定的屬性，請使用 <xref:System.Xml.XPath.XPathNavigator.MoveToAttribute%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="7794b-114">To move the <xref:System.Xml.XPath.XPathNavigator> to a particular attribute, use the <xref:System.Xml.XPath.XPathNavigator.MoveToAttribute%2A> method.</span></span> <span data-ttu-id="7794b-115">您還可以重複處理項目的每個屬性，方法是使用 <xref:System.Xml.XPath.XPathNavigator.MoveToFirstAttribute%2A> 方法，然後多次呼叫 <xref:System.Xml.XPath.XPathNavigator.MoveToNextAttribute%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="7794b-115">You can also iterate over each attribute of an element by using the <xref:System.Xml.XPath.XPathNavigator.MoveToFirstAttribute%2A> method, followed by multiple calls to the <xref:System.Xml.XPath.XPathNavigator.MoveToNextAttribute%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7794b-116">當 <xref:System.Xml.XPath.XPathNavigator> 物件定位於屬性或命名空間節點上時，<xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>、<xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>、<xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>、<xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>、<xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>、<xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> 和 <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> 方法一律會傳回 `false`，且對 <xref:System.Xml.XPath.XPathNavigator> 的位置毫無影響。</span><span class="sxs-lookup"><span data-stu-id="7794b-116">When the <xref:System.Xml.XPath.XPathNavigator> object is positioned on an attribute or namespace node, the <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> and <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> methods always return `false`, and have no effect on the position of the <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="7794b-117"><xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>、<xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A> 及 <xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A> 方法則例外。</span><span class="sxs-lookup"><span data-stu-id="7794b-117">The exceptions are the <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>, and <xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A> methods.</span></span>  
  
## <a name="namespace-node-navigation"></a><span data-ttu-id="7794b-118">命名空間節點巡覽</span><span class="sxs-lookup"><span data-stu-id="7794b-118">Namespace Node Navigation</span></span>  
 <span data-ttu-id="7794b-119">每個項目都有一組相關聯的命名空間節點，一個用於每個與此項目範圍內命名空間 URI 繫結的個別命名空間前置詞 (包括繫結至 `http://www.w3.org/XML/1998/namespace` 命名空間的 XML 前置詞，其在每個 XML 文件中隱含宣告)，另一個用於預設命名空間 (若命名空間節點位於此項目的範圍內)。</span><span class="sxs-lookup"><span data-stu-id="7794b-119">Each element has an associated set of namespace nodes, one for each distinct namespace prefix that is bound to a namespace URI in scope for the element (including the XML prefix bound to the `http://www.w3.org/XML/1998/namespace` namespace, which is implicitly declared in every XML document) and one for the default namespace if one is in scope for the element.</span></span> <span data-ttu-id="7794b-120">此項目為上述每個命名空間節點的父代；但命名空間節點並非其父項目的子系。</span><span class="sxs-lookup"><span data-stu-id="7794b-120">The element is the parent of each of these namespace nodes; however, a namespace node is not a child of its parent element.</span></span>  
  
 <span data-ttu-id="7794b-121">與屬性一樣，<xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> 及 <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> 方法無法用來從項目巡覽到命名空間節點，或在命名空間節點之間巡覽。</span><span class="sxs-lookup"><span data-stu-id="7794b-121">As with attributes, the <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> and <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> methods are not used to navigate from an element to a namespace node, or between namespace nodes.</span></span> <span data-ttu-id="7794b-122">而是命名空間節點具有不同的巡覽方法。</span><span class="sxs-lookup"><span data-stu-id="7794b-122">Instead, namespace nodes have distinct methods of navigation.</span></span>  
  
 <span data-ttu-id="7794b-123">以下是 <xref:System.Xml.XPath.XPathNavigator> 類別的命名空間巡覽方法。</span><span class="sxs-lookup"><span data-stu-id="7794b-123">The following are the namespace navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToNamespace%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A>  
  
 <span data-ttu-id="7794b-124">在 XML 文件中，任何項目的範圍內總是至少有一個命名空間節點。</span><span class="sxs-lookup"><span data-stu-id="7794b-124">There is always at least one namespace node in scope for any element in an XML document.</span></span> <span data-ttu-id="7794b-125">此命名空間節點具有前置詞 `xml` 及命名空間 URI `http://www.w3.org/XML/1998/namespace`。</span><span class="sxs-lookup"><span data-stu-id="7794b-125">This is the namespace node with the prefix `xml` and namespace URI `http://www.w3.org/XML/1998/namespace`.</span></span> <span data-ttu-id="7794b-126">若要在給定特定前置詞的情況下，擷取範圍內的命名空間 URI，請使用 <xref:System.Xml.XPath.XPathNavigator.GetNamespace%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="7794b-126">To retrieve a namespace URI in scope given a particular prefix, use the <xref:System.Xml.XPath.XPathNavigator.GetNamespace%2A> method.</span></span> <span data-ttu-id="7794b-127">若要將 <xref:System.Xml.XPath.XPathNavigator> 物件移至特定的命名空間節點，請使用 <xref:System.Xml.XPath.XPathNavigator.MoveToNamespace%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="7794b-127">To move the <xref:System.Xml.XPath.XPathNavigator> object to a particular namespace node, use the <xref:System.Xml.XPath.XPathNavigator.MoveToNamespace%2A> method.</span></span> <span data-ttu-id="7794b-128">您還可以重複處理項目範圍內的每個命名空間節點，方法是使用 <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> 方法，然後多次呼叫 <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="7794b-128">You can also iterate over each namespace node in scope for an element by using the <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> method followed by multiple calls to the <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7794b-129">當 <xref:System.Xml.XPath.XPathNavigator> 物件定位於屬性或命名空間節點上時，<xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>、<xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>、<xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>、<xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>、<xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>、<xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> 和 <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> 方法一律會傳回 `false`，且對 <xref:System.Xml.XPath.XPathNavigator> 的位置毫無影響。</span><span class="sxs-lookup"><span data-stu-id="7794b-129">When the <xref:System.Xml.XPath.XPathNavigator> object is positioned on an attribute or namespace node, the <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A> and <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A> methods always return `false`, and have no effect on the position of the <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="7794b-130"><xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>、<xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A> 及 <xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A> 方法則例外。</span><span class="sxs-lookup"><span data-stu-id="7794b-130">The exceptions are the <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>, <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>, and <xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A> methods.</span></span>  
  
### <a name="the-xpathnamespacescope-enumeration"></a><span data-ttu-id="7794b-131">XPathNamespaceScope 列舉型別</span><span class="sxs-lookup"><span data-stu-id="7794b-131">The XPathNamespaceScope Enumeration</span></span>  
 <span data-ttu-id="7794b-132">巡覽命名空間節點時，可使用 <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> 參數呼叫 <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> 及 <xref:System.Xml.XPath.XPathNamespaceScope> 方法。</span><span class="sxs-lookup"><span data-stu-id="7794b-132">When navigating namespace nodes the <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> and <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> methods can be called with an <xref:System.Xml.XPath.XPathNamespaceScope> parameter.</span></span> <span data-ttu-id="7794b-133">這些方法的行為模式，與其不使用參數呼叫的對應方法不同。</span><span class="sxs-lookup"><span data-stu-id="7794b-133">These methods behave differently than their counterparts called with no parameters.</span></span> <span data-ttu-id="7794b-134"><xref:System.Xml.XPath.XPathNamespaceScope> 列舉型別具有值 <xref:System.Xml.XPath.XPathNamespaceScope.All>、<xref:System.Xml.XPath.XPathNamespaceScope.ExcludeXml> 或 <xref:System.Xml.XPath.XPathNamespaceScope.Local>。</span><span class="sxs-lookup"><span data-stu-id="7794b-134">The <xref:System.Xml.XPath.XPathNamespaceScope> enumeration has values of <xref:System.Xml.XPath.XPathNamespaceScope.All>, <xref:System.Xml.XPath.XPathNamespaceScope.ExcludeXml>, or <xref:System.Xml.XPath.XPathNamespaceScope.Local>.</span></span>  
  
 <span data-ttu-id="7794b-135">下列範例顯示在 XML 文件的不同範圍由 <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> 及 <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> 方法傳回的命名空間。</span><span class="sxs-lookup"><span data-stu-id="7794b-135">The following examples show what namespaces are returned by the <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> and <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> methods at various scopes in an XML document.</span></span>  
  
```xml  
<root>  
    <element1 xmlns="http://www.contoso.com" xmlns:books="http://www.contoso.com/books">  
        <element2 />  
    </element1>  
</root>  
```  
  
 <span data-ttu-id="7794b-136">命名空間序列 (在呼叫 <xref:System.Xml.XPath.XPathNavigator> 方法，然後對 <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> 方法進行一系列呼叫之後，<xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> 所在的命名空間) 如下所示。</span><span class="sxs-lookup"><span data-stu-id="7794b-136">The namespace sequence (the namespace the <xref:System.Xml.XPath.XPathNavigator> is positioned upon after calling the <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> method followed by a series of calls to the <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> method) is as follows.</span></span>  
  
-   <span data-ttu-id="7794b-137">當定位於 `element2` 上時：`xmlns:books="http://www.contoso.com/books"`, `xmlns="http://www.contoso.com"` 和 `xmlns:xml="http://www.w3.org/XML/1998/namespace"`。</span><span class="sxs-lookup"><span data-stu-id="7794b-137">When positioned on `element2`: `xmlns:books="http://www.contoso.com/books"`, `xmlns="http://www.contoso.com"`, and `xmlns:xml="http://www.w3.org/XML/1998/namespace"`.</span></span>  
  
-   <span data-ttu-id="7794b-138">當定位於 `element1` 上時：`xmlns:books="http://www.contoso.com/books"`, `xmlns="http://www.contoso.com"` 和 `xmlns:xml="http://www.w3.org/XML/1998/namespace"`。</span><span class="sxs-lookup"><span data-stu-id="7794b-138">When positioned on `element1`: `xmlns:books="http://www.contoso.com/books"`, `xmlns="http://www.contoso.com"`, and `xmlns:xml="http://www.w3.org/XML/1998/namespace"`.</span></span>  
  
-   <span data-ttu-id="7794b-139">當定位於 `root` 上時：`xmlns:xml="http://www.w3.org/XML/1998/namespace".`</span><span class="sxs-lookup"><span data-stu-id="7794b-139">When positioned on `root`: `xmlns:xml="http://www.w3.org/XML/1998/namespace".`</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7794b-140"><xref:System.Xml.XPath.XPathNavigator> 類別會以反向的文件順序傳回命名空間節點。</span><span class="sxs-lookup"><span data-stu-id="7794b-140">The <xref:System.Xml.XPath.XPathNavigator> class returns namespace nodes in reverse document order.</span></span> <span data-ttu-id="7794b-141">因此，<xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> 實際上會移至目前範圍中的最後一個命名空間節點。</span><span class="sxs-lookup"><span data-stu-id="7794b-141">Therefore, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> essentially moves to the last namespace node in the current scope.</span></span>  
  
 <span data-ttu-id="7794b-142">下列範例顯示在 XML 文件的不同範圍指定了 <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> 列舉型別時，由 <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> 及 <xref:System.Xml.XPath.XPathNamespaceScope> 方法傳回的命名空間。</span><span class="sxs-lookup"><span data-stu-id="7794b-142">The following examples show what namespaces are returned by the <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> and <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> methods with the <xref:System.Xml.XPath.XPathNamespaceScope> enumeration specified at various scopes in an XML document.</span></span>  
  
```xml  
<root xmlns="http://www.contoso.com" xmlns:a="http://www.contoso.com/a" xmlns:b="http://www.contoso.com/b">  
    <child1 xmlns="" xmlns:a="urn:a">  
        <child2 xmlns:c="urn:c" />  
    </child1>  
</root>  
```  
  
 <span data-ttu-id="7794b-143">當定位於 `child2` 時，命名空間序列 (在呼叫 <xref:System.Xml.XPath.XPathNavigator> 方法，然後對 <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> 方法進行一系列呼叫之後，<xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> 所在的命名空間) 如下所示。</span><span class="sxs-lookup"><span data-stu-id="7794b-143">When positioned on `child2`, the namespace sequence (the namespace the <xref:System.Xml.XPath.XPathNavigator> is positioned upon after calling the <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> method followed by a series of calls to the <xref:System.Xml.XPath.XPathNavigator.MoveToNextNamespace%2A> method) is as follows.</span></span>  
  
-   <span data-ttu-id="7794b-144"><xref:System.Xml.XPath.XPathNamespaceScope.All>：`xmlns:c="urn:c"`、`xmlns:a="urn:a"`、`xmlns=""`、`xmlns:b="http://www.contoso.com/b"`、`xmlns:a="http://www.contoso.com/a"`、`xmlns="http://www.contoso.com"` 及 `xmlns:xml="http://www.w3.org/XML/1998/namespace"`。</span><span class="sxs-lookup"><span data-stu-id="7794b-144"><xref:System.Xml.XPath.XPathNamespaceScope.All>: `xmlns:c="urn:c"`, `xmlns:a="urn:a"`, `xmlns=""`, `xmlns:b="http://www.contoso.com/b"`, `xmlns:a="http://www.contoso.com/a"`, `xmlns="http://www.contoso.com"`, and `xmlns:xml="http://www.w3.org/XML/1998/namespace"`.</span></span>  
  
-   <span data-ttu-id="7794b-145"><xref:System.Xml.XPath.XPathNamespaceScope.ExcludeXml>：`xmlns:c="urn:c"`、`xmlns:a="urn:a"`、`xmlns=""`、`xmlns:b="http://www.contoso.com/b"`、`xmlns:a="http://www.contoso.com/a"` 及 `xmlns="http://www.contoso.com"`。</span><span class="sxs-lookup"><span data-stu-id="7794b-145"><xref:System.Xml.XPath.XPathNamespaceScope.ExcludeXml>: `xmlns:c="urn:c"`, `xmlns:a="urn:a"`, `xmlns=""`, `xmlns:b="http://www.contoso.com/b"`, `xmlns:a="http://www.contoso.com/a"`, and `xmlns="http://www.contoso.com"`.</span></span>  
  
-   <span data-ttu-id="7794b-146"><xref:System.Xml.XPath.XPathNamespaceScope.Local>: `xmlns:c="urn:c"`.</span><span class="sxs-lookup"><span data-stu-id="7794b-146"><xref:System.Xml.XPath.XPathNamespaceScope.Local>: `xmlns:c="urn:c"`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7794b-147"><xref:System.Xml.XPath.XPathNavigator> 類別會以反向的文件順序傳回命名空間節點。</span><span class="sxs-lookup"><span data-stu-id="7794b-147">The <xref:System.Xml.XPath.XPathNavigator> class returns namespace nodes in reverse document order.</span></span> <span data-ttu-id="7794b-148">因此，<xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> 實際上會移至目前範圍中的最後一個命名空間節點。</span><span class="sxs-lookup"><span data-stu-id="7794b-148">Therefore, <xref:System.Xml.XPath.XPathNavigator.MoveToFirstNamespace%2A> essentially moves to the last namespace node in the current scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7794b-149">請參閱</span><span class="sxs-lookup"><span data-stu-id="7794b-149">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="7794b-150">使用 XPath 資料模型處理 XML 資料</span><span class="sxs-lookup"><span data-stu-id="7794b-150">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="7794b-151">使用 XPathNavigator 導覽節點集</span><span class="sxs-lookup"><span data-stu-id="7794b-151">Node Set Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)  
 [<span data-ttu-id="7794b-152">使用 XPathNavigator 擷取 XML 資料</span><span class="sxs-lookup"><span data-stu-id="7794b-152">Extract XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="7794b-153">使用 XPathNavigator 存取強型別 XML 資料</span><span class="sxs-lookup"><span data-stu-id="7794b-153">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
