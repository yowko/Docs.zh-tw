---
title: "移除項目、 屬性和節點從 XML 樹狀結構 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 5cf21919-4360-4b49-b29d-58ea3164ac72
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 8842858080ce1f27d997e6af61a8dd2301cdc2bc
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017


---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-visual-basic"></a><span data-ttu-id="9e3ea-102">移除項目、 屬性和節點從 XML 樹狀結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e3ea-102">Removing Elements, Attributes, and Nodes from an XML Tree (Visual Basic)</span></span>
<span data-ttu-id="9e3ea-103">您可以修改 XML 樹狀以移除項目、屬性以及其他類型的節點。</span><span class="sxs-lookup"><span data-stu-id="9e3ea-103">You can modify an XML tree, removing elements, attributes, and other types of nodes.</span></span>  
  
 <span data-ttu-id="9e3ea-104">從 XML 文件移除單一項目或單一屬性很直接。</span><span class="sxs-lookup"><span data-stu-id="9e3ea-104">Removing a single element or a single attribute from an XML document is straightforward.</span></span> <span data-ttu-id="9e3ea-105">不過，移除項目或屬性的集合時，您應該先將集合具體化到清單中，然後從清單中刪除項目或屬性。</span><span class="sxs-lookup"><span data-stu-id="9e3ea-105">However, when removing collections of elements or attributes, you should first materialize a collection into a list, and then delete the elements or attributes from the list.</span></span> <span data-ttu-id="9e3ea-106">最好的方法是使用<xref:System.Xml.Linq.Extensions.Remove%2A>擴充方法，將您執行此工作。</xref:System.Xml.Linq.Extensions.Remove%2A></span><span class="sxs-lookup"><span data-stu-id="9e3ea-106">The best approach is to use the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method, which will do this for you.</span></span>  
  
 <span data-ttu-id="9e3ea-107">這麼做的主要原因是因為您從 XML 樹狀結構中擷取的大部分集合都是使用延後執行產生的。</span><span class="sxs-lookup"><span data-stu-id="9e3ea-107">The main reason for doing this is that most of the collections you retrieve from an XML tree are yielded using deferred execution.</span></span> <span data-ttu-id="9e3ea-108">如果您沒有先將這些集合具體化到清單中，或沒有使用擴充方法，則可能發生特定類別的 Bug。</span><span class="sxs-lookup"><span data-stu-id="9e3ea-108">If you do not first materialize them into a list, or if you do not use the extension methods, it is possible to encounter a certain class of bugs.</span></span> <span data-ttu-id="9e3ea-109">如需詳細資訊，請參閱[混合宣告式程式碼/命令式程式碼 Bug (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="9e3ea-109">For more information, see [Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="9e3ea-110">下列方法會從 XML 樹狀移除節點和屬性。</span><span class="sxs-lookup"><span data-stu-id="9e3ea-110">The following methods remove nodes and attributes from an XML tree.</span></span>  
  
|<span data-ttu-id="9e3ea-111">方法</span><span class="sxs-lookup"><span data-stu-id="9e3ea-111">Method</span></span>|<span data-ttu-id="9e3ea-112">描述</span><span class="sxs-lookup"><span data-stu-id="9e3ea-112">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="9e3ea-113">[XAttribute.Remove](https://msdn.microsoft.com/library/system.xml.linq.xattribute.remove\(v=vs.110\).aspx)</span><span class="sxs-lookup"><span data-stu-id="9e3ea-113">[XAttribute.Remove](https://msdn.microsoft.com/library/system.xml.linq.xattribute.remove\(v=vs.110\).aspx)</span></span>|<span data-ttu-id="9e3ea-114">移除<xref:System.Xml.Linq.XAttribute>從其父代。</xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="9e3ea-114">Removes an <xref:System.Xml.Linq.XAttribute> from its parent.</span></span>|  
|<span data-ttu-id="9e3ea-115">[XContainer.RemoveNodes](https://msdn.microsoft.com/library/system.xml.linq.xcontainer.removenodes\(v=vs.110\).aspx)</span><span class="sxs-lookup"><span data-stu-id="9e3ea-115">[XContainer.RemoveNodes](https://msdn.microsoft.com/library/system.xml.linq.xcontainer.removenodes\(v=vs.110\).aspx)</span></span>|<span data-ttu-id="9e3ea-116">從<xref:System.Xml.Linq.XContainer>.</xref:System.Xml.Linq.XContainer>移除子節點</span><span class="sxs-lookup"><span data-stu-id="9e3ea-116">Removes the child nodes from an <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<span data-ttu-id="9e3ea-117"><xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="9e3ea-117"><xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=fullName></span></span>|<span data-ttu-id="9e3ea-118">從<xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement>移除內容和屬性</span><span class="sxs-lookup"><span data-stu-id="9e3ea-118">Removes content and attributes from an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<span data-ttu-id="9e3ea-119"><xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="9e3ea-119"><xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=fullName></span></span>|<span data-ttu-id="9e3ea-120">移除<xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement>屬性</span><span class="sxs-lookup"><span data-stu-id="9e3ea-120">Removes the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<span data-ttu-id="9e3ea-121"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="9e3ea-121"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=fullName></span></span>|<span data-ttu-id="9e3ea-122">如果您針對值傳遞 `null`，則會移除屬性。</span><span class="sxs-lookup"><span data-stu-id="9e3ea-122">If you pass `null` for value, then removes the attribute.</span></span>|  
|<span data-ttu-id="9e3ea-123"><xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="9e3ea-123"><xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=fullName></span></span>|<span data-ttu-id="9e3ea-124">如果您針對值傳遞 `null`，則會移除子項目。</span><span class="sxs-lookup"><span data-stu-id="9e3ea-124">If you pass `null` for value, then removes the child element.</span></span>|  
|<span data-ttu-id="9e3ea-125"><xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=fullName></xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="9e3ea-125"><xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=fullName></span></span>|<span data-ttu-id="9e3ea-126">移除<xref:System.Xml.Linq.XNode>從其父代。</xref:System.Xml.Linq.XNode></span><span class="sxs-lookup"><span data-stu-id="9e3ea-126">Removes an <xref:System.Xml.Linq.XNode> from its parent.</span></span>|  
|<span data-ttu-id="9e3ea-127"><xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=fullName></xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="9e3ea-127"><xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=fullName></span></span>|<span data-ttu-id="9e3ea-128">從其父項目移除來源集合中的每個屬性或項目。</span><span class="sxs-lookup"><span data-stu-id="9e3ea-128">Removes every attribute or element in the source collection from its parent element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9e3ea-129">範例</span><span class="sxs-lookup"><span data-stu-id="9e3ea-129">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="9e3ea-130">描述</span><span class="sxs-lookup"><span data-stu-id="9e3ea-130">Description</span></span>  
 <span data-ttu-id="9e3ea-131">這個範例會示範三種移除項目的方法。</span><span class="sxs-lookup"><span data-stu-id="9e3ea-131">This example demonstrates three approaches to removing elements.</span></span> <span data-ttu-id="9e3ea-132">首先，它會移除單一項目。</span><span class="sxs-lookup"><span data-stu-id="9e3ea-132">First, it removes a single element.</span></span> <span data-ttu-id="9e3ea-133">第二，它會擷取項目的集合，具體化它們使用<xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName>運算子，並將集合中移除。</xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="9e3ea-133">Second, it retrieves a collection of elements, materializes them using the <xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName> operator, and removes the collection.</span></span> <span data-ttu-id="9e3ea-134">最後，它會擷取項目的集合，並將其移除使用<xref:System.Xml.Linq.Extensions.Remove%2A>擴充方法。</xref:System.Xml.Linq.Extensions.Remove%2A></span><span class="sxs-lookup"><span data-stu-id="9e3ea-134">Finally, it retrieves a collection of elements and removes them using the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method.</span></span>  
  
 <span data-ttu-id="9e3ea-135">如需有關<xref:System.Linq.Enumerable.ToList%2A>運算子，請參閱[轉換資料類型 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md)。</xref:System.Linq.Enumerable.ToList%2A></span><span class="sxs-lookup"><span data-stu-id="9e3ea-135">For more information on the <xref:System.Linq.Enumerable.ToList%2A> operator, see [Converting Data Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md).</span></span>  
  
### <a name="code"></a><span data-ttu-id="9e3ea-136">程式碼</span><span class="sxs-lookup"><span data-stu-id="9e3ea-136">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="9e3ea-137">註解</span><span class="sxs-lookup"><span data-stu-id="9e3ea-137">Comments</span></span>  
 <span data-ttu-id="9e3ea-138">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="9e3ea-138">This code produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="9e3ea-139">請注意，第一個後代子項目已從 `Child1` 移除。</span><span class="sxs-lookup"><span data-stu-id="9e3ea-139">Notice that the first grandchild element has been removed from `Child1`.</span></span> <span data-ttu-id="9e3ea-140">所有後代子項目都已經從 `Child2` 和 `Child3` 移除。</span><span class="sxs-lookup"><span data-stu-id="9e3ea-140">All grandchildren elements have been removed from `Child2` and from `Child3`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e3ea-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e3ea-141">See Also</span></span>  
 [<span data-ttu-id="9e3ea-142">修改 XML 樹狀結構 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e3ea-142">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
