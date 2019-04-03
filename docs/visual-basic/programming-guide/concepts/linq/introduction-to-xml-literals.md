---
title: 在 Visual Basic2 XML 常值簡介
ms.date: 07/20/2015
ms.assetid: 94fc0e03-978e-4c08-ab6c-0dc3c1e64f10
ms.openlocfilehash: 68ba1e018d4ad9501532745a88090f0f756b5c17
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841270"
---
# <a name="introduction-to-xml-literals-in-visual-basic"></a><span data-ttu-id="2df4a-102">Visual Basic 中的 XML 常值簡介</span><span class="sxs-lookup"><span data-stu-id="2df4a-102">Introduction to XML Literals in Visual Basic</span></span>
<span data-ttu-id="2df4a-103">本節提供在 Visual Basic 中建立 XML 樹狀結構的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="2df4a-103">This section provides information about creating XML trees in Visual Basic.</span></span>  
  
 <span data-ttu-id="2df4a-104">如需使用 LINQ 查詢的結果做為內容，XML 樹狀結構的資訊，請參閱[函數式建構 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="2df4a-104">For information about using the results of LINQ queries as the content for an XML tree, see [Functional Construction (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="2df4a-105">如需有關在 Visual Basic 中的 XML 常值的詳細資訊，請參閱 <<c0> [ 概觀的 LINQ to XML，在 Visual Basic 中](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="2df4a-105">For more information on XML literals in Visual Basic, see [Overview of LINQ to XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md).</span></span>  
  
## <a name="creating-xml-trees"></a><span data-ttu-id="2df4a-106">建立 XML 樹狀結構</span><span class="sxs-lookup"><span data-stu-id="2df4a-106">Creating XML Trees</span></span>  
 <span data-ttu-id="2df4a-107">下列範例顯示如何在此案例 <xref:System.Xml.Linq.XElement> 中建立 `contacts`：</span><span class="sxs-lookup"><span data-stu-id="2df4a-107">The following example shows how to create an <xref:System.Xml.Linq.XElement>, in this case `contacts`:</span></span>  
  
```vb  
Dim contacts As XElement = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone>206-555-0144</Phone>  
            <Address>  
                <Street1>123 Main St</Street1>  
                <City>Mercer Island</City>  
                <State>WA</State>  
                <Postal>68042</Postal>  
            </Address>  
        </Contact>  
    </Contacts>  
```  
  
### <a name="creating-an-xelement-with-simple-content"></a><span data-ttu-id="2df4a-108">建立包含簡單內容的 XElement</span><span class="sxs-lookup"><span data-stu-id="2df4a-108">Creating an XElement with Simple Content</span></span>  
 <span data-ttu-id="2df4a-109">您可以建立包含簡單內容的 <xref:System.Xml.Linq.XElement>，如下所示：</span><span class="sxs-lookup"><span data-stu-id="2df4a-109">You can create an <xref:System.Xml.Linq.XElement> that contains simple content, as follows:</span></span>  
  
```vb  
Dim n as XElement = <Customer>Adventure Works</Customer>  
Console.WriteLine(n)   
```  
  
 <span data-ttu-id="2df4a-110">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="2df4a-110">This example produces the following output:</span></span>  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
### <a name="creating-an-empty-element"></a><span data-ttu-id="2df4a-111">建立空項目</span><span class="sxs-lookup"><span data-stu-id="2df4a-111">Creating an Empty Element</span></span>  
 <span data-ttu-id="2df4a-112">您可以建立空的 <xref:System.Xml.Linq.XElement>，如下所示：</span><span class="sxs-lookup"><span data-stu-id="2df4a-112">You can create an empty <xref:System.Xml.Linq.XElement>, as follows:</span></span>  
  
```vb  
Dim n As XElement = <Customer/>  
Console.WriteLine(n)  
```  
  
 <span data-ttu-id="2df4a-113">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="2df4a-113">This example produces the following output:</span></span>  
  
```xml  
<Customer />  
```  
  
### <a name="using-embedded-expressions"></a><span data-ttu-id="2df4a-114">使用內嵌的運算式</span><span class="sxs-lookup"><span data-stu-id="2df4a-114">Using Embedded Expressions</span></span>  
 <span data-ttu-id="2df4a-115">XML 常值的其中一個重要功能是，這些 XML 常值允許內嵌的運算式。</span><span class="sxs-lookup"><span data-stu-id="2df4a-115">An important feature of XML literals is that they allow embedded expressions.</span></span> <span data-ttu-id="2df4a-116">內嵌的運算式可讓您評估運算式，並將運算式的結果插入到 XML 樹狀中。</span><span class="sxs-lookup"><span data-stu-id="2df4a-116">Embedded expressions enable you to evaluate an expression and insert the results of the expression into the XML tree.</span></span> <span data-ttu-id="2df4a-117">如果運算式評估 <xref:System.Xml.Linq.XElement> 的型別，會將項目插入到樹狀中。</span><span class="sxs-lookup"><span data-stu-id="2df4a-117">If the expression evaluates to a type of <xref:System.Xml.Linq.XElement>, an element is inserted into the tree.</span></span> <span data-ttu-id="2df4a-118">如果運算式評估 <xref:System.Xml.Linq.XAttribute> 的型別，會將屬性插入到樹狀結構中。</span><span class="sxs-lookup"><span data-stu-id="2df4a-118">If the expression evaluates to a type of <xref:System.Xml.Linq.XAttribute>, an attribute is inserted into the tree.</span></span> <span data-ttu-id="2df4a-119">您可以將項目和屬性僅插入到有效的樹狀結構中。</span><span class="sxs-lookup"><span data-stu-id="2df4a-119">You can insert elements and attributes into the tree only where they are valid.</span></span>  
  
 <span data-ttu-id="2df4a-120">請注意，只有單一運算式可以插入到內嵌的運算式中，這點很重要。</span><span class="sxs-lookup"><span data-stu-id="2df4a-120">It is important to note that only a single expression can go into an embedded expression.</span></span> <span data-ttu-id="2df4a-121">您無法內嵌多個陳述式。</span><span class="sxs-lookup"><span data-stu-id="2df4a-121">You cannot embed multiple statements.</span></span> <span data-ttu-id="2df4a-122">如果運算式的延伸超過單一行，您必須使用行接續字元。</span><span class="sxs-lookup"><span data-stu-id="2df4a-122">If an expression extends beyond a single line, you must use the line continuation character.</span></span>  
  
 <span data-ttu-id="2df4a-123">如果您使用內嵌的運算式，將現有的節點 (包括項目) 和屬性加入到新的 XML 樹狀結構，而且如果現有的節點已經成為父代，這些節點就會遭到複製。</span><span class="sxs-lookup"><span data-stu-id="2df4a-123">If you use an embedded expression to add existing nodes (including elements) and attributes to a new XML tree and if the existing nodes are already parented, the nodes are cloned.</span></span> <span data-ttu-id="2df4a-124">新複製的節點會附加到新的 XML 樹狀結構中。</span><span class="sxs-lookup"><span data-stu-id="2df4a-124">The newly cloned nodes are attached to the new XML tree.</span></span> <span data-ttu-id="2df4a-125">如果現有的節點沒有成為父代，這些節點只會附加到新的 XML 樹狀。</span><span class="sxs-lookup"><span data-stu-id="2df4a-125">If the existing nodes are not parented, the nodes are simply attached to the new XML tree.</span></span> <span data-ttu-id="2df4a-126">本主題中的最後一個範例會示範這個情況。</span><span class="sxs-lookup"><span data-stu-id="2df4a-126">The last example in this topic demonstrates this.</span></span>  
  
 <span data-ttu-id="2df4a-127">下列範例使用內嵌的運算式，將項目插入到樹狀中：</span><span class="sxs-lookup"><span data-stu-id="2df4a-127">The following example uses an embedded expression to insert an element into the tree:</span></span>  
  
```vb  
xmlTree1 As XElement = _  
    <Root>  
        <Child>Contents</Child>  
    </Root>  
Dim xmlTree2 As XElement = _  
    <Root>  
        <%= xmlTree1.<Child> %>  
    </Root>  
Console.WriteLine(xmlTree2)  
```  
  
 <span data-ttu-id="2df4a-128">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="2df4a-128">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>Contents</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-content"></a><span data-ttu-id="2df4a-129">將內嵌的運算式用於內容</span><span class="sxs-lookup"><span data-stu-id="2df4a-129">Using Embedded Expressions for Content</span></span>  
 <span data-ttu-id="2df4a-130">您可以使用內嵌的運算式提供項目的內容：</span><span class="sxs-lookup"><span data-stu-id="2df4a-130">You can use an embedded expression to supply the content of an element:</span></span>  
  
```vb  
Dim str As String  
str = "Some content"  
Dim root As XElement = <Root><%= str %></Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="2df4a-131">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="2df4a-131">This example produces the following output:</span></span>  
  
```xml  
<Root>Some content</Root>  
```  
  
### <a name="using-a-linq-query-in-an-embedded-expression"></a><span data-ttu-id="2df4a-132">在內嵌的運算式中使用 LINQ 查詢</span><span class="sxs-lookup"><span data-stu-id="2df4a-132">Using a LINQ Query in an Embedded Expression</span></span>  
 <span data-ttu-id="2df4a-133">您可以將 LINQ 查詢的結果用於項目的內容：</span><span class="sxs-lookup"><span data-stu-id="2df4a-133">You can use the results of a LINQ query for the content of an element:</span></span>  
  
```vb  
Dim arr As Integer() = {1, 2, 3}  
  
Dim n As XElement = _  
    <Root>  
        <%= From i In arr Select <Child><%= i %></Child> %>  
    </Root>  
  
Console.WriteLine(n)  
```  
  
 <span data-ttu-id="2df4a-134">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="2df4a-134">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Child>3</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-node-names"></a><span data-ttu-id="2df4a-135">將內嵌的運算式用於節點名稱</span><span class="sxs-lookup"><span data-stu-id="2df4a-135">Using Embedded Expressions for Node Names</span></span>  
 <span data-ttu-id="2df4a-136">您也可以使用內嵌的運算式來計算屬性名稱、屬性值、項目名稱與項目值：</span><span class="sxs-lookup"><span data-stu-id="2df4a-136">You can also use embedded expressions to calculate attribute names, attribute values, element names, and element values:</span></span>  
  
```vb  
Dim eleName As String = "ele"  
Dim attName As String = "att"  
Dim attValue As String = "aValue"  
Dim eleValue As String = "eValue"  
Dim n As XElement = _  
    <Root <%= attName %>=<%= attValue %>>  
        <<%= eleName %>>  
            <%= eleValue %>  
        </>  
    </Root>  
Console.WriteLine(n)  
```  
  
 <span data-ttu-id="2df4a-137">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="2df4a-137">This example produces the following output:</span></span>  
  
```xml  
<Root att="aValue">  
  <ele>eValue</ele>  
</Root>  
```  
  
### <a name="cloning-vs-attaching"></a><span data-ttu-id="2df4a-138">複製與附加之比較</span><span class="sxs-lookup"><span data-stu-id="2df4a-138">Cloning vs. Attaching</span></span>  
 <span data-ttu-id="2df4a-139">如先前所述，如果您使用內嵌的運算式，將現有的節點 (包括項目) 和屬性加入到新的 XML 樹狀，而且如果現有的節點已經成為父代，這些節點就會遭到複製，而新複製的節點會附加到新的 XML 樹狀中。</span><span class="sxs-lookup"><span data-stu-id="2df4a-139">As mentioned earlier, if you use an embedded expression to add existing nodes (including elements) and attributes to a new XML tree, if the existing nodes are already parented, the nodes are cloned and the newly cloned nodes are attached to the new XML tree.</span></span> <span data-ttu-id="2df4a-140">如果現有的節點沒有成為父代，這些節點只會附加到新的 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="2df4a-140">If the existing nodes are not parented, they are simply attached to the new XML tree.</span></span>  
  
```vb  
' Create a tree with a child element.  
Dim xmlTree1 As XElement = _  
    <Root>  
        <Child1>1</Child1>  
    </Root>  
  
' Create an element that is not parented.  
Dim child2 As XElement = <Child2>2</Child2>  
  
' Create a tree and add Child1 and Child2 to it.  
Dim xmlTree2 As XElement = _  
    <Root>  
        <%= xmlTree1.<Child1>(0) %>  
        <%= child2 %>  
    </Root>  
  
' Compare Child1 identity.  
Console.WriteLine("Child1 was {0}", _  
    IIf(xmlTree1.Element("Child1") Is xmlTree2.Element("Child1"), _  
    "attached", "cloned"))  
  
' Compare Child2 identity.  
Console.WriteLine("Child2 was {0}", _  
    IIf(child2 Is xmlTree2.Element("Child2"), _  
    "attached", "cloned"))  
```  
  
 <span data-ttu-id="2df4a-141">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="2df4a-141">This example produces the following output:</span></span>  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a><span data-ttu-id="2df4a-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2df4a-142">See also</span></span>

- [<span data-ttu-id="2df4a-143">建立 XML 樹狀結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2df4a-143">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
