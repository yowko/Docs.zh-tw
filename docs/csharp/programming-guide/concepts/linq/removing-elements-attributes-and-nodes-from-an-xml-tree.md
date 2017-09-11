---
title: "從 XML 樹狀結構移除項目、屬性和節點 (C#) | Microsoft Docs"
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
ms.assetid: 07dd06d6-1117-4077-bf98-9120cf51176e
caps.latest.revision: 4
author: BillWagner
ms.author: wiwagn
ms.translationtype: Human Translation
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: 527ebac9156a0b08cbc6b7fcae9192be8a7d71ee
ms.contentlocale: zh-tw
ms.lasthandoff: 03/24/2017


---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-c"></a><span data-ttu-id="4347e-102">從 XML 樹狀結構移除項目、屬性和節點 (C#)</span><span class="sxs-lookup"><span data-stu-id="4347e-102">Removing Elements, Attributes, and Nodes from an XML Tree (C#)</span></span>
<span data-ttu-id="4347e-103">您可以修改 XML 樹狀以移除項目、屬性以及其他類型的節點。</span><span class="sxs-lookup"><span data-stu-id="4347e-103">You can modify an XML tree, removing elements, attributes, and other types of nodes.</span></span>  
  
 <span data-ttu-id="4347e-104">從 XML 文件移除單一項目或單一屬性很直接。</span><span class="sxs-lookup"><span data-stu-id="4347e-104">Removing a single element or a single attribute from an XML document is straightforward.</span></span> <span data-ttu-id="4347e-105">不過，移除項目或屬性的集合時，您應該先將集合具體化到清單中，然後從清單中刪除項目或屬性。</span><span class="sxs-lookup"><span data-stu-id="4347e-105">However, when removing collections of elements or attributes, you should first materialize a collection into a list, and then delete the elements or attributes from the list.</span></span> <span data-ttu-id="4347e-106">最好的方法是使用 <xref:System.Xml.Linq.Extensions.Remove%2A> 擴充方法自動執行。</span><span class="sxs-lookup"><span data-stu-id="4347e-106">The best approach is to use the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method, which will do this for you.</span></span>  
  
 <span data-ttu-id="4347e-107">這麼做的主要原因是因為您從 XML 樹狀結構中擷取的大部分集合都是使用延後執行產生的。</span><span class="sxs-lookup"><span data-stu-id="4347e-107">The main reason for doing this is that most of the collections you retrieve from an XML tree are yielded using deferred execution.</span></span> <span data-ttu-id="4347e-108">如果您沒有先將這些集合具體化到清單中，或沒有使用擴充方法，則可能發生特定類別的 Bug。</span><span class="sxs-lookup"><span data-stu-id="4347e-108">If you do not first materialize them into a list, or if you do not use the extension methods, it is possible to encounter a certain class of bugs.</span></span> <span data-ttu-id="4347e-109">如需詳細資訊，請參閱[混合的宣告式程式碼/命令式程式碼 Bug (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="4347e-109">For more information, see [Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="4347e-110">下列方法會從 XML 樹狀移除節點和屬性。</span><span class="sxs-lookup"><span data-stu-id="4347e-110">The following methods remove nodes and attributes from an XML tree.</span></span>  
  
|<span data-ttu-id="4347e-111">方法</span><span class="sxs-lookup"><span data-stu-id="4347e-111">Method</span></span>|<span data-ttu-id="4347e-112">描述</span><span class="sxs-lookup"><span data-stu-id="4347e-112">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4347e-113">[XAttribute.Remove](https://msdn.microsoft.com/library/system.xml.linq.xattribute.remove\(v=vs.110\).aspx)</span><span class="sxs-lookup"><span data-stu-id="4347e-113">[XAttribute.Remove](https://msdn.microsoft.com/library/system.xml.linq.xattribute.remove\(v=vs.110\).aspx)</span></span>|<span data-ttu-id="4347e-114">從其父代移除 <xref:System.Xml.Linq.XAttribute>。</span><span class="sxs-lookup"><span data-stu-id="4347e-114">Removes an <xref:System.Xml.Linq.XAttribute> from its parent.</span></span>|  
|<span data-ttu-id="4347e-115">[XContainer.RemoveNodes](https://msdn.microsoft.com/library/system.xml.linq.xcontainer.removenodes\(v=vs.110\).aspx)</span><span class="sxs-lookup"><span data-stu-id="4347e-115">[XContainer.RemoveNodes](https://msdn.microsoft.com/library/system.xml.linq.xcontainer.removenodes\(v=vs.110\).aspx)</span></span>|<span data-ttu-id="4347e-116">從 <xref:System.Xml.Linq.XContainer> 移除子節點。</span><span class="sxs-lookup"><span data-stu-id="4347e-116">Removes the child nodes from an <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<span data-ttu-id="4347e-117"><xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4347e-117"><xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=fullName></span></span>|<span data-ttu-id="4347e-118">從 <xref:System.Xml.Linq.XElement> 移除內容和屬性。</span><span class="sxs-lookup"><span data-stu-id="4347e-118">Removes content and attributes from an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<span data-ttu-id="4347e-119"><xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4347e-119"><xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=fullName></span></span>|<span data-ttu-id="4347e-120">移除 <xref:System.Xml.Linq.XElement> 的屬性。</span><span class="sxs-lookup"><span data-stu-id="4347e-120">Removes the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<span data-ttu-id="4347e-121"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4347e-121"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=fullName></span></span>|<span data-ttu-id="4347e-122">如果您針對值傳遞 `null`，則會移除屬性。</span><span class="sxs-lookup"><span data-stu-id="4347e-122">If you pass `null` for value, then removes the attribute.</span></span>|  
|<span data-ttu-id="4347e-123"><xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4347e-123"><xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=fullName></span></span>|<span data-ttu-id="4347e-124">如果您針對值傳遞 `null`，則會移除子項目。</span><span class="sxs-lookup"><span data-stu-id="4347e-124">If you pass `null` for value, then removes the child element.</span></span>|  
|<span data-ttu-id="4347e-125"><xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4347e-125"><xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=fullName></span></span>|<span data-ttu-id="4347e-126">從其父代移除 <xref:System.Xml.Linq.XNode>。</span><span class="sxs-lookup"><span data-stu-id="4347e-126">Removes an <xref:System.Xml.Linq.XNode> from its parent.</span></span>|  
|<span data-ttu-id="4347e-127"><xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4347e-127"><xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=fullName></span></span>|<span data-ttu-id="4347e-128">從其父項目移除來源集合中的每個屬性或項目。</span><span class="sxs-lookup"><span data-stu-id="4347e-128">Removes every attribute or element in the source collection from its parent element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4347e-129">範例</span><span class="sxs-lookup"><span data-stu-id="4347e-129">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="4347e-130">描述</span><span class="sxs-lookup"><span data-stu-id="4347e-130">Description</span></span>  
 <span data-ttu-id="4347e-131">這個範例會示範三種移除項目的方法。</span><span class="sxs-lookup"><span data-stu-id="4347e-131">This example demonstrates three approaches to removing elements.</span></span> <span data-ttu-id="4347e-132">首先，它會移除單一項目。</span><span class="sxs-lookup"><span data-stu-id="4347e-132">First, it removes a single element.</span></span> <span data-ttu-id="4347e-133">接著，它會擷取項目的集合，並使用 <xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName> 運算子進行具體化，然後移除集合。</span><span class="sxs-lookup"><span data-stu-id="4347e-133">Second, it retrieves a collection of elements, materializes them using the <xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName> operator, and removes the collection.</span></span> <span data-ttu-id="4347e-134">最後，它會擷取項目的集合，並使用 <xref:System.Xml.Linq.Extensions.Remove%2A> 擴充方法加以移除。</span><span class="sxs-lookup"><span data-stu-id="4347e-134">Finally, it retrieves a collection of elements and removes them using the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method.</span></span>  
  
 <span data-ttu-id="4347e-135">如需 <xref:System.Linq.Enumerable.ToList%2A> 運算子的詳細資訊，請參閱[轉換資料類型 (C#)](../../../../csharp/programming-guide/concepts/linq/converting-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="4347e-135">For more information on the <xref:System.Linq.Enumerable.ToList%2A> operator, see [Converting Data Types (C#)](../../../../csharp/programming-guide/concepts/linq/converting-data-types.md).</span></span>  
  
### <a name="code"></a><span data-ttu-id="4347e-136">程式碼</span><span class="sxs-lookup"><span data-stu-id="4347e-136">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="4347e-137">註解</span><span class="sxs-lookup"><span data-stu-id="4347e-137">Comments</span></span>  
 <span data-ttu-id="4347e-138">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="4347e-138">This code produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="4347e-139">請注意，第一個後代子項目已從 `Child1` 移除。</span><span class="sxs-lookup"><span data-stu-id="4347e-139">Notice that the first grandchild element has been removed from `Child1`.</span></span> <span data-ttu-id="4347e-140">所有後代子項目都已經從 `Child2` 和 `Child3` 移除。</span><span class="sxs-lookup"><span data-stu-id="4347e-140">All grandchildren elements have been removed from `Child2` and from `Child3`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4347e-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4347e-141">See Also</span></span>  
 [<span data-ttu-id="4347e-142">修改 XML 樹狀結構 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="4347e-142">Modifying XML Trees (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
