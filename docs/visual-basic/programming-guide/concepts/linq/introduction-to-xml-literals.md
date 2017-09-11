---
title: "XML 常值的視覺 Basic2 簡介 |Microsoft 文件"
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
ms.assetid: 94fc0e03-978e-4c08-ab6c-0dc3c1e64f10
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: a3aff4755c23664153ce1dc0ec2df58a96d29c66
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="introduction-to-xml-literals-in-visual-basic"></a><span data-ttu-id="85342-102">Visual Basic 中的 XML 常值簡介</span><span class="sxs-lookup"><span data-stu-id="85342-102">Introduction to XML Literals in Visual Basic</span></span>
<span data-ttu-id="85342-103">本節提供在 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 中建立 XML 樹狀結構的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="85342-103">This section provides information about creating XML trees in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
 <span data-ttu-id="85342-104">使用 LINQ 查詢的結果做為內容，XML 樹狀結構的相關資訊，請參閱[功能建構 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="85342-104">For information about using the results of LINQ queries as the content for an XML tree, see [Functional Construction (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="85342-105">如需有關 XML 常值的[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]，請參閱[概觀的 LINQ to XML 在 Visual Basic 中](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="85342-105">For more information on XML literals in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], see [Overview of LINQ to XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md).</span></span>  
  
## <a name="creating-xml-trees"></a><span data-ttu-id="85342-106">建立 XML 樹狀</span><span class="sxs-lookup"><span data-stu-id="85342-106">Creating XML Trees</span></span>  
 <span data-ttu-id="85342-107">下列範例示範如何建立<xref:System.Xml.Linq.XElement>，在此情況下`contacts`:</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="85342-107">The following example shows how to create an <xref:System.Xml.Linq.XElement>, in this case `contacts`:</span></span>  
  
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
  
### <a name="creating-an-xelement-with-simple-content"></a><span data-ttu-id="85342-108">建立包含簡單內容的 XElement</span><span class="sxs-lookup"><span data-stu-id="85342-108">Creating an XElement with Simple Content</span></span>  
 <span data-ttu-id="85342-109">您可以建立<xref:System.Xml.Linq.XElement>，其中包含簡單內容，如下所示︰</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="85342-109">You can create an <xref:System.Xml.Linq.XElement> that contains simple content, as follows:</span></span>  
  
```vb  
Dim n as XElement = <Customer>Adventure Works</Customer>  
Console.WriteLine(n)   
```  
  
 <span data-ttu-id="85342-110">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="85342-110">This example produces the following output:</span></span>  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
### <a name="creating-an-empty-element"></a><span data-ttu-id="85342-111">建立空項目</span><span class="sxs-lookup"><span data-stu-id="85342-111">Creating an Empty Element</span></span>  
 <span data-ttu-id="85342-112">您可以建立空白<xref:System.Xml.Linq.XElement>，如下︰</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="85342-112">You can create an empty <xref:System.Xml.Linq.XElement>, as follows:</span></span>  
  
```vb  
Dim n As XElement = <Customer/>  
Console.WriteLine(n)  
```  
  
 <span data-ttu-id="85342-113">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="85342-113">This example produces the following output:</span></span>  
  
```xml  
<Customer />  
```  
  
### <a name="using-embedded-expressions"></a><span data-ttu-id="85342-114">使用內嵌的運算式</span><span class="sxs-lookup"><span data-stu-id="85342-114">Using Embedded Expressions</span></span>  
 <span data-ttu-id="85342-115">XML 常值的其中一個重要功能是，這些 XML 常值允許內嵌的運算式。</span><span class="sxs-lookup"><span data-stu-id="85342-115">An important feature of XML literals is that they allow embedded expressions.</span></span> <span data-ttu-id="85342-116">內嵌的運算式可讓您評估運算式，並將運算式的結果插入到 XML 樹狀中。</span><span class="sxs-lookup"><span data-stu-id="85342-116">Embedded expressions enable you to evaluate an expression and insert the results of the expression into the XML tree.</span></span> <span data-ttu-id="85342-117">如果運算式評估為一種<xref:System.Xml.Linq.XElement>，項目插入到樹狀結構。</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="85342-117">If the expression evaluates to a type of <xref:System.Xml.Linq.XElement>, an element is inserted into the tree.</span></span> <span data-ttu-id="85342-118">如果運算式評估為一種<xref:System.Xml.Linq.XAttribute>，將屬性插入到樹狀結構。</xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="85342-118">If the expression evaluates to a type of <xref:System.Xml.Linq.XAttribute>, an attribute is inserted into the tree.</span></span> <span data-ttu-id="85342-119">您可以將項目和屬性僅插入到有效的樹狀中。</span><span class="sxs-lookup"><span data-stu-id="85342-119">You can insert elements and attributes into the tree only where they are valid.</span></span>  
  
 <span data-ttu-id="85342-120">請注意，只有單一運算式可以插入到內嵌的運算式中，這點很重要。</span><span class="sxs-lookup"><span data-stu-id="85342-120">It is important to note that only a single expression can go into an embedded expression.</span></span> <span data-ttu-id="85342-121">您無法內嵌多個陳述式。</span><span class="sxs-lookup"><span data-stu-id="85342-121">You cannot embed multiple statements.</span></span> <span data-ttu-id="85342-122">如果運算式的延伸超過單一行，您必須使用行接續字元。</span><span class="sxs-lookup"><span data-stu-id="85342-122">If an expression extends beyond a single line, you must use the line continuation character.</span></span>  
  
 <span data-ttu-id="85342-123">如果您使用內嵌的運算式，將現有的節點 (包括項目) 和屬性加入到新的 XML 樹狀結構，而且如果現有的節點已經成為父代，這些節點就會遭到複製。</span><span class="sxs-lookup"><span data-stu-id="85342-123">If you use an embedded expression to add existing nodes (including elements) and attributes to a new XML tree and if the existing nodes are already parented, the nodes are cloned.</span></span> <span data-ttu-id="85342-124">新複製的節點會附加到新的 XML 樹狀結構中。</span><span class="sxs-lookup"><span data-stu-id="85342-124">The newly cloned nodes are attached to the new XML tree.</span></span> <span data-ttu-id="85342-125">如果現有的節點沒有成為父代，這些節點只會附加到新的 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="85342-125">If the existing nodes are not parented, the nodes are simply attached to the new XML tree.</span></span> <span data-ttu-id="85342-126">本主題中的最後一個範例會示範這個情況。</span><span class="sxs-lookup"><span data-stu-id="85342-126">The last example in this topic demonstrates this.</span></span>  
  
 <span data-ttu-id="85342-127">下列範例使用內嵌的運算式，將項目插入到樹狀結構中：</span><span class="sxs-lookup"><span data-stu-id="85342-127">The following example uses an embedded expression to insert an element into the tree:</span></span>  
  
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
  
 <span data-ttu-id="85342-128">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="85342-128">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>Contents</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-content"></a><span data-ttu-id="85342-129">將內嵌的運算式用於內容</span><span class="sxs-lookup"><span data-stu-id="85342-129">Using Embedded Expressions for Content</span></span>  
 <span data-ttu-id="85342-130">您可以使用內嵌的運算式提供項目的內容：</span><span class="sxs-lookup"><span data-stu-id="85342-130">You can use an embedded expression to supply the content of an element:</span></span>  
  
```vb  
Dim str As String  
str = "Some content"  
Dim root As XElement = <Root><%= str %></Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="85342-131">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="85342-131">This example produces the following output:</span></span>  
  
```xml  
<Root>Some content</Root>  
```  
  
### <a name="using-a-linq-query-in-an-embedded-expression"></a><span data-ttu-id="85342-132">在內嵌的運算式中使用 LINQ 查詢</span><span class="sxs-lookup"><span data-stu-id="85342-132">Using a LINQ Query in an Embedded Expression</span></span>  
 <span data-ttu-id="85342-133">您可以將 LINQ 查詢的結果用於項目的內容：</span><span class="sxs-lookup"><span data-stu-id="85342-133">You can use the results of a LINQ query for the content of an element:</span></span>  
  
```vb  
Dim arr As Integer() = {1, 2, 3}  
  
Dim n As XElement = _  
    <Root>  
        <%= From i In arr Select <Child><%= i %></Child> %>  
    </Root>  
  
Console.WriteLine(n)  
```  
  
 <span data-ttu-id="85342-134">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="85342-134">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Child>3</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-node-names"></a><span data-ttu-id="85342-135">將內嵌的運算式用於節點名稱</span><span class="sxs-lookup"><span data-stu-id="85342-135">Using Embedded Expressions for Node Names</span></span>  
 <span data-ttu-id="85342-136">您也可以使用內嵌的運算式來計算屬性名稱、屬性值、項目名稱與項目值：</span><span class="sxs-lookup"><span data-stu-id="85342-136">You can also use embedded expressions to calculate attribute names, attribute values, element names, and element values:</span></span>  
  
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
  
 <span data-ttu-id="85342-137">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="85342-137">This example produces the following output:</span></span>  
  
```xml  
<Root att="aValue">  
  <ele>eValue</ele>  
</Root>  
```  
  
### <a name="cloning-vs-attaching"></a><span data-ttu-id="85342-138">複製與附加之比較</span><span class="sxs-lookup"><span data-stu-id="85342-138">Cloning vs. Attaching</span></span>  
 <span data-ttu-id="85342-139">如先前所述，如果您使用內嵌的運算式，將現有的節點 (包括項目) 和屬性加入到新的 XML 樹狀結構，而且如果現有的節點已經成為父代，這些節點就會遭到複製，而新複製的節點會附加到新的 XML 樹狀結構中。</span><span class="sxs-lookup"><span data-stu-id="85342-139">As mentioned earlier, if you use an embedded expression to add existing nodes (including elements) and attributes to a new XML tree, if the existing nodes are already parented, the nodes are cloned and the newly cloned nodes are attached to the new XML tree.</span></span> <span data-ttu-id="85342-140">如果現有的節點沒有成為父代，這些節點只會附加到新的 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="85342-140">If the existing nodes are not parented, they are simply attached to the new XML tree.</span></span>  
  
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
  
 <span data-ttu-id="85342-141">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="85342-141">This example produces the following output:</span></span>  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a><span data-ttu-id="85342-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85342-142">See Also</span></span>  
 [<span data-ttu-id="85342-143">建立 XML 樹狀結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="85342-143">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
