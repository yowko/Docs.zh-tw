---
title: 移除項目、 屬性和節點從 XML 樹狀結構 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 5cf21919-4360-4b49-b29d-58ea3164ac72
ms.openlocfilehash: dbc5cfd7bf6e1f1b77dd14a6771c387fac29d062
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33645924"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-visual-basic"></a><span data-ttu-id="28b6e-102">移除項目、 屬性和節點從 XML 樹狀結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="28b6e-102">Removing Elements, Attributes, and Nodes from an XML Tree (Visual Basic)</span></span>
<span data-ttu-id="28b6e-103">您可以修改 XML 樹狀以移除項目、屬性以及其他類型的節點。</span><span class="sxs-lookup"><span data-stu-id="28b6e-103">You can modify an XML tree, removing elements, attributes, and other types of nodes.</span></span>  
  
 <span data-ttu-id="28b6e-104">從 XML 文件移除單一項目或單一屬性很直接。</span><span class="sxs-lookup"><span data-stu-id="28b6e-104">Removing a single element or a single attribute from an XML document is straightforward.</span></span> <span data-ttu-id="28b6e-105">不過，移除項目或屬性的集合時，您應該先將集合具體化到清單中，然後從清單中刪除項目或屬性。</span><span class="sxs-lookup"><span data-stu-id="28b6e-105">However, when removing collections of elements or attributes, you should first materialize a collection into a list, and then delete the elements or attributes from the list.</span></span> <span data-ttu-id="28b6e-106">最好的方法是，使用 <xref:System.Xml.Linq.Extensions.Remove%2A> 擴充方法替您執行。</span><span class="sxs-lookup"><span data-stu-id="28b6e-106">The best approach is to use the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method, which will do this for you.</span></span>  
  
 <span data-ttu-id="28b6e-107">這麼做的主要原因是因為您從 XML 樹狀結構中擷取的大部分集合都是使用延後執行產生的。</span><span class="sxs-lookup"><span data-stu-id="28b6e-107">The main reason for doing this is that most of the collections you retrieve from an XML tree are yielded using deferred execution.</span></span> <span data-ttu-id="28b6e-108">如果您沒有先將這些集合具體化到清單中，或沒有使用擴充方法，則可能發生特定類別的 Bug。</span><span class="sxs-lookup"><span data-stu-id="28b6e-108">If you do not first materialize them into a list, or if you do not use the extension methods, it is possible to encounter a certain class of bugs.</span></span> <span data-ttu-id="28b6e-109">如需詳細資訊，請參閱[混合宣告式程式碼/命令式程式碼 Bug (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="28b6e-109">For more information, see [Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="28b6e-110">下列方法會從 XML 樹狀移除節點和屬性。</span><span class="sxs-lookup"><span data-stu-id="28b6e-110">The following methods remove nodes and attributes from an XML tree.</span></span>  
  
|<span data-ttu-id="28b6e-111">方法</span><span class="sxs-lookup"><span data-stu-id="28b6e-111">Method</span></span>|<span data-ttu-id="28b6e-112">描述</span><span class="sxs-lookup"><span data-stu-id="28b6e-112">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="28b6e-113">從其父代移除 <xref:System.Xml.Linq.XAttribute>。</span><span class="sxs-lookup"><span data-stu-id="28b6e-113">Removes an <xref:System.Xml.Linq.XAttribute> from its parent.</span></span>|  
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="28b6e-114">從 <xref:System.Xml.Linq.XContainer> 移除子節點。</span><span class="sxs-lookup"><span data-stu-id="28b6e-114">Removes the child nodes from an <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="28b6e-115">從 <xref:System.Xml.Linq.XElement> 移除內容和屬性。</span><span class="sxs-lookup"><span data-stu-id="28b6e-115">Removes content and attributes from an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="28b6e-116">移除 <xref:System.Xml.Linq.XElement> 的屬性。</span><span class="sxs-lookup"><span data-stu-id="28b6e-116">Removes the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="28b6e-117">如果您針對值傳遞 `null`，則會移除屬性。</span><span class="sxs-lookup"><span data-stu-id="28b6e-117">If you pass `null` for value, then removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="28b6e-118">如果您針對值傳遞 `null`，則會移除子項目。</span><span class="sxs-lookup"><span data-stu-id="28b6e-118">If you pass `null` for value, then removes the child element.</span></span>|  
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="28b6e-119">從其父代移除 <xref:System.Xml.Linq.XNode>。</span><span class="sxs-lookup"><span data-stu-id="28b6e-119">Removes an <xref:System.Xml.Linq.XNode> from its parent.</span></span>|  
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="28b6e-120">從其父項目移除來源集合中的每個屬性或項目。</span><span class="sxs-lookup"><span data-stu-id="28b6e-120">Removes every attribute or element in the source collection from its parent element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="28b6e-121">範例</span><span class="sxs-lookup"><span data-stu-id="28b6e-121">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="28b6e-122">描述</span><span class="sxs-lookup"><span data-stu-id="28b6e-122">Description</span></span>  
 <span data-ttu-id="28b6e-123">這個範例會示範三種移除項目的方法。</span><span class="sxs-lookup"><span data-stu-id="28b6e-123">This example demonstrates three approaches to removing elements.</span></span> <span data-ttu-id="28b6e-124">首先，它會移除單一項目。</span><span class="sxs-lookup"><span data-stu-id="28b6e-124">First, it removes a single element.</span></span> <span data-ttu-id="28b6e-125">接著，它會反覆運算項目的集合，使用 <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> 運算子具體化它們，然後移除集合。</span><span class="sxs-lookup"><span data-stu-id="28b6e-125">Second, it retrieves a collection of elements, materializes them using the <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> operator, and removes the collection.</span></span> <span data-ttu-id="28b6e-126">最後，它會擷取項目的集合，並使用 <xref:System.Xml.Linq.Extensions.Remove%2A> 擴充方法加以移除。</span><span class="sxs-lookup"><span data-stu-id="28b6e-126">Finally, it retrieves a collection of elements and removes them using the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method.</span></span>  
  
 <span data-ttu-id="28b6e-127">如需有關<xref:System.Linq.Enumerable.ToList%2A>運算子，請參閱[轉換資料類型 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="28b6e-127">For more information on the <xref:System.Linq.Enumerable.ToList%2A> operator, see [Converting Data Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md).</span></span>  
  
### <a name="code"></a><span data-ttu-id="28b6e-128">程式碼</span><span class="sxs-lookup"><span data-stu-id="28b6e-128">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="28b6e-129">註解</span><span class="sxs-lookup"><span data-stu-id="28b6e-129">Comments</span></span>  
 <span data-ttu-id="28b6e-130">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="28b6e-130">This code produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="28b6e-131">請注意，第一個後代子項目已從 `Child1` 移除。</span><span class="sxs-lookup"><span data-stu-id="28b6e-131">Notice that the first grandchild element has been removed from `Child1`.</span></span> <span data-ttu-id="28b6e-132">所有後代子項目都已經從 `Child2` 和 `Child3` 移除。</span><span class="sxs-lookup"><span data-stu-id="28b6e-132">All grandchildren elements have been removed from `Child2` and from `Child3`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28b6e-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28b6e-133">See Also</span></span>  
 [<span data-ttu-id="28b6e-134">修改 XML 樹狀 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="28b6e-134">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
