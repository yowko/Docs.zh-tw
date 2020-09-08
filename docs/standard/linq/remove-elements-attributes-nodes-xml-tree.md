---
title: 從 XML 樹狀結構移除元素、屬性和節點-LINQ to XML
description: 瞭解如何從 XML 樹狀結構移除專案、屬性和其他類型的節點。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 07dd06d6-1117-4077-bf98-9120cf51176e
ms.openlocfilehash: 1a7c10892ccf1baaab7dde700266a134abe727de
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552729"
---
# <a name="remove-elements-attributes-and-nodes-from-an-xml-tree-linq-to-xml"></a><span data-ttu-id="589c1-103">從 XML 樹狀結構中移除元素、屬性和節點 (LINQ to XML) </span><span class="sxs-lookup"><span data-stu-id="589c1-103">Remove elements, attributes, and nodes from an XML tree (LINQ to XML)</span></span>

<span data-ttu-id="589c1-104">您可以修改 XML 樹狀以移除項目、屬性以及其他類型的節點。</span><span class="sxs-lookup"><span data-stu-id="589c1-104">You can modify an XML tree, removing elements, attributes, and other types of nodes.</span></span>

<span data-ttu-id="589c1-105">從 XML 文件移除單一項目或單一屬性很直接。</span><span class="sxs-lookup"><span data-stu-id="589c1-105">Removing a single element or a single attribute from an XML document is straightforward.</span></span> <span data-ttu-id="589c1-106">不過，移除項目或屬性的集合時，您應該先將集合具體化到清單中，然後從清單中刪除項目或屬性。</span><span class="sxs-lookup"><span data-stu-id="589c1-106">However, when removing collections of elements or attributes, you should first materialize a collection into a list, and then delete the elements or attributes from the list.</span></span> <span data-ttu-id="589c1-107">最好的方法是使用 <xref:System.Xml.Linq.Extensions.Remove%2A> 擴充方法來執行這項作業。</span><span class="sxs-lookup"><span data-stu-id="589c1-107">The best approach is to use the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method to do this.</span></span>

<span data-ttu-id="589c1-108">使用這種方法的主要原因是，您從 XML 樹狀結構取出的大部分集合都是使用延後執行所產生的。</span><span class="sxs-lookup"><span data-stu-id="589c1-108">The main reason to use this approach is that most of the collections you retrieve from an XML tree are yielded using deferred execution.</span></span> <span data-ttu-id="589c1-109">如果您未先將它們具體化為清單，或未使用擴充方法，您可能會遇到特定類別的 bug。</span><span class="sxs-lookup"><span data-stu-id="589c1-109">If you don't first materialize them into a list, or if you don't use the extension methods, you may encounter a certain class of bugs.</span></span> <span data-ttu-id="589c1-110">如需詳細資訊，請參閱 [混合的宣告式/命令式程式碼錯誤（bug](mixed-declarative-imperative-code-bugs.md)）。</span><span class="sxs-lookup"><span data-stu-id="589c1-110">For more information, see [Mixed declarative/imperative code bugs](mixed-declarative-imperative-code-bugs.md).</span></span>

<span data-ttu-id="589c1-111">下列方法會從 XML 樹狀移除節點和屬性。</span><span class="sxs-lookup"><span data-stu-id="589c1-111">The following methods remove nodes and attributes from an XML tree.</span></span>

|<span data-ttu-id="589c1-112">方法</span><span class="sxs-lookup"><span data-stu-id="589c1-112">Method</span></span>|<span data-ttu-id="589c1-113">描述</span><span class="sxs-lookup"><span data-stu-id="589c1-113">Description</span></span>|
|------------|-----------------|
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="589c1-114"><xref:System.Xml.Linq.XAttribute>從其父代移除。</span><span class="sxs-lookup"><span data-stu-id="589c1-114">Remove an <xref:System.Xml.Linq.XAttribute> from its parent.</span></span>|
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="589c1-115">從移除子節點 <xref:System.Xml.Linq.XContainer> 。</span><span class="sxs-lookup"><span data-stu-id="589c1-115">Remove the child nodes from an <xref:System.Xml.Linq.XContainer>.</span></span>|
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="589c1-116">從移除內容和屬性 <xref:System.Xml.Linq.XElement> 。</span><span class="sxs-lookup"><span data-stu-id="589c1-116">Remove content and attributes from an <xref:System.Xml.Linq.XElement>.</span></span>|
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="589c1-117">移除的屬性 <xref:System.Xml.Linq.XElement> 。</span><span class="sxs-lookup"><span data-stu-id="589c1-117">Remove the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="589c1-118">如果您傳遞此值，請移除該屬性 `null` 。</span><span class="sxs-lookup"><span data-stu-id="589c1-118">Remove the attribute if you pass the value `null`.</span></span>|
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="589c1-119">如果您傳遞值，請移除子項目 `null` 。</span><span class="sxs-lookup"><span data-stu-id="589c1-119">Remove the child element if you pass the value `null`.</span></span>|
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="589c1-120"><xref:System.Xml.Linq.XNode>從其父代移除。</span><span class="sxs-lookup"><span data-stu-id="589c1-120">Remove an <xref:System.Xml.Linq.XNode> from its parent.</span></span>|
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="589c1-121">從其父元素移除來源集合中的每個屬性或元素。</span><span class="sxs-lookup"><span data-stu-id="589c1-121">Remove every attribute or element in the source collection from its parent element.</span></span>|

## <a name="example-remove-a-single-element-and-remove-a-collection-of-elements-in-two-ways"></a><span data-ttu-id="589c1-122">範例：移除單一專案，並以兩種方式移除元素集合</span><span class="sxs-lookup"><span data-stu-id="589c1-122">Example: Remove a single element, and remove a collection of elements in two ways</span></span>

<span data-ttu-id="589c1-123">這個範例會示範三種移除項目的方法。</span><span class="sxs-lookup"><span data-stu-id="589c1-123">This example demonstrates three approaches to removing elements.</span></span> <span data-ttu-id="589c1-124">首先，它會移除單一項目。</span><span class="sxs-lookup"><span data-stu-id="589c1-124">First, it removes a single element.</span></span> <span data-ttu-id="589c1-125">其次，它會抓取專案的集合，使用運算子將它們具體化，然後 <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> 移除集合。</span><span class="sxs-lookup"><span data-stu-id="589c1-125">Second, it retrieves a collection of elements, materializes them using the <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> operator, and then removes the collection.</span></span> <span data-ttu-id="589c1-126">最後，它會擷取項目的集合，並使用 <xref:System.Xml.Linq.Extensions.Remove%2A> 擴充方法加以移除。</span><span class="sxs-lookup"><span data-stu-id="589c1-126">Finally, it retrieves a collection of elements and removes them using the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method.</span></span>

<span data-ttu-id="589c1-127">如需運算子的詳細資訊 <xref:System.Linq.Enumerable.ToList%2A> ，請參閱 [轉換資料類型 (c # ) ](../../csharp/programming-guide/concepts/linq/converting-data-types.md) 和 [轉換資料類型 (Visual Basic) ](../../visual-basic/programming-guide/concepts/linq/converting-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="589c1-127">For more information on the <xref:System.Linq.Enumerable.ToList%2A> operator, see [Converting Data Types (C#)](../../csharp/programming-guide/concepts/linq/converting-data-types.md) and [Converting Data Types (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/converting-data-types.md).</span></span>

```csharp
XElement root = XElement.Parse(@"<Root>
    <Child1>
        <GrandChild1/>
        <GrandChild2/>
        <GrandChild3/>
    </Child1>
    <Child2>
        <GrandChild4/>
        <GrandChild5/>
        <GrandChild6/>
    </Child2>
    <Child3>
        <GrandChild7/>
        <GrandChild8/>
        <GrandChild9/>
    </Child3>
</Root>");
root.Element("Child1").Element("GrandChild1").Remove();
root.Element("Child2").Elements().ToList().Remove();
root.Element("Child3").Elements().Remove();
Console.WriteLine(root);
```

```vb
Dim root As XElement = _
    <Root>
        <Child1>
            <GrandChild1/>
            <GrandChild2/>
            <GrandChild3/>
        </Child1>
        <Child2>
            <GrandChild4/>
            <GrandChild5/>
            <GrandChild6/>
        </Child2>
        <Child3>
            <GrandChild7/>
            <GrandChild8/>
            <GrandChild9/>
        </Child3>
    </Root>
root.<Child1>.<GrandChild1>.Remove()
root.<Child2>.Elements().ToList().Remove()
root.<Child3>.Elements().Remove()
Console.WriteLine(root)
```

<span data-ttu-id="589c1-128">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="589c1-128">This example produces the following output:</span></span>

```xml
<Root>
  <Child1>
    <GrandChild2 />
    <GrandChild3 />
  </Child1>
  <Child2 />
  <Child3 />
</Root>
```

<span data-ttu-id="589c1-129">第一個孫元素已從移除 `Child1` ，而且所有孫系元素都已從 `Child2` 和移除 `Child3` 。</span><span class="sxs-lookup"><span data-stu-id="589c1-129">The first grandchild element was removed from `Child1`, and all grandchildren elements were removed from `Child2` and from `Child3`.</span></span>
