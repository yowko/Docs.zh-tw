---
title: "如何︰ 使用註釋將 LINQ to XML 樹狀結構中的 XSLT 樣式 (Visual Basic) 轉換 |Microsoft 文件"
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
ms.assetid: 08e91fa2-dac2-4463-9ef1-87b1ac3fa890
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
ms.openlocfilehash: e2ccb8e6880d7836ee2aae2b7f3c3799c9ff2835
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style-visual-basic"></a><span data-ttu-id="caf7c-102">如何︰ 使用註釋將 LINQ to XML 樹狀結構中的 XSLT 樣式 (Visual Basic) 轉換</span><span class="sxs-lookup"><span data-stu-id="caf7c-102">How to: Use Annotations to Transform LINQ to XML Trees in an XSLT Style (Visual Basic)</span></span>
<span data-ttu-id="caf7c-103">附註可用於簡化 XML 樹狀的轉換。</span><span class="sxs-lookup"><span data-stu-id="caf7c-103">Annotations can be used to facilitate transforms of an XML tree.</span></span>  
  
 <span data-ttu-id="caf7c-104">有些 XML 文件為「中央具有混合內容的文件」。</span><span class="sxs-lookup"><span data-stu-id="caf7c-104">Some XML documents are "document centric with mixed content."</span></span> <span data-ttu-id="caf7c-105">使用這類文件時，您不一定要知道項目子節點的組織結構。</span><span class="sxs-lookup"><span data-stu-id="caf7c-105">With such documents, you don't necessarily know the shape of child nodes of an element.</span></span> <span data-ttu-id="caf7c-106">例如，包含文字的節點類似如下：</span><span class="sxs-lookup"><span data-stu-id="caf7c-106">For instance, a node that contains text may look like this:</span></span>  
  
```xml  
<text>A phrase with <b>bold</b> and <i>italic</i> text.</text>  
```  
  
 <span data-ttu-id="caf7c-107">針對任何指定的文字節點，可能會有任何數目的 `<b>` 和 `<i>` 子項目。</span><span class="sxs-lookup"><span data-stu-id="caf7c-107">For any given text node, there may be any number of child `<b>` and `<i>` elements.</span></span> <span data-ttu-id="caf7c-108">這個方法會延伸到數個其他情況︰ 例如，可以包含各種子項目，例如一般段落、 分項段落與點陣圖的頁面。</span><span class="sxs-lookup"><span data-stu-id="caf7c-108">This approach extends to a number of other situations: such as, pages that can contain a variety of child elements, such as regular paragraphs, bulleted paragraphs, and bitmaps.</span></span> <span data-ttu-id="caf7c-109">資料表中的儲存格可能包含文字、下拉式清單或點陣圖。</span><span class="sxs-lookup"><span data-stu-id="caf7c-109">Cells in a table may contain text, drop down lists, or bitmaps.</span></span> <span data-ttu-id="caf7c-110">文件中心 XML 的其中一個主要特性為，您不知道任何特定項目將會有哪個子項目。</span><span class="sxs-lookup"><span data-stu-id="caf7c-110">One of the primary characteristics of document centric XML is that you do not know which child element any particular element will have.</span></span>  
  
 <span data-ttu-id="caf7c-111">如果您要在樹狀結構中，轉換您不一定了解太多您要轉換之項目子系的項目，則使用附註的這個方法是一個有效的方法。</span><span class="sxs-lookup"><span data-stu-id="caf7c-111">If you want to transform elements in a tree where you don't necessarily know much about the children of the elements that you want to transform, then this approach that uses annotations is an effective approach.</span></span>  
  
 <span data-ttu-id="caf7c-112">方法的摘要如下：</span><span class="sxs-lookup"><span data-stu-id="caf7c-112">The summary of the approach is:</span></span>  
  
-   <span data-ttu-id="caf7c-113">首先，在樹狀結構中，以替代項目附註項目。</span><span class="sxs-lookup"><span data-stu-id="caf7c-113">First, annotate elements in the tree with a replacement element.</span></span>  
  
-   <span data-ttu-id="caf7c-114">接著，逐一查看整個樹狀結構，建立您以其附註取代每個項目的新樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="caf7c-114">Second, iterate through the entire tree, creating a new tree where you replace each element with its annotation.</span></span> <span data-ttu-id="caf7c-115">這個範本會在名稱為 `XForm` 的函式中，實作反覆運算並建立新的樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="caf7c-115">This example implements the iteration and creation of the new tree in a function named `XForm`.</span></span>  
  
 <span data-ttu-id="caf7c-116">就細節而言，此方法包含：</span><span class="sxs-lookup"><span data-stu-id="caf7c-116">In detail, the approach consists of:</span></span>  
  
-   <span data-ttu-id="caf7c-117">執行一或多個 LINQ to XML 查詢，這些查詢會傳回您要從一個組織結構轉換為另一個組織結構的項目集。</span><span class="sxs-lookup"><span data-stu-id="caf7c-117">Execute one or more LINQ to XML queries that return the set of elements that you want to transform from one shape to another.</span></span> <span data-ttu-id="caf7c-118">針對每個項目查詢中，加入新<xref:System.Xml.Linq.XElement>物件做為項目附註。</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="caf7c-118">For each element in the query, add a new <xref:System.Xml.Linq.XElement> object as an annotation to the element.</span></span> <span data-ttu-id="caf7c-119">這個新項目將會取代已轉換之新樹狀中的標註項目。</span><span class="sxs-lookup"><span data-stu-id="caf7c-119">This new element will replace the annotated element in the new, transformed tree.</span></span> <span data-ttu-id="caf7c-120">如本範例的示範，這是容易撰寫的簡單程式碼。</span><span class="sxs-lookup"><span data-stu-id="caf7c-120">This is simple code to write, as demonstrated by the example.</span></span>  
  
-   <span data-ttu-id="caf7c-121">加入為附註的新項目可以包含新的子節點；它可以形成具有任何所需組織結構的子樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="caf7c-121">The new element that is added as an annotation can contain new child nodes; it can form a sub-tree with any desired shape.</span></span>  
  
-   <span data-ttu-id="caf7c-122">有一個特殊規則：如果新項目的子節點位於不同的命名空間中，也就是針對此目的所形成的命名空間 (在此範例中，命名空間為 `http://www.microsoft.com/LinqToXmlTransform/2007`)，則不會將該子項目複製到新的樹狀結構中。</span><span class="sxs-lookup"><span data-stu-id="caf7c-122">There is a special rule: If a child node of the new element is in a different namespace, a namespace that is made up for this purpose (in this example, the namespace is `http://www.microsoft.com/LinqToXmlTransform/2007`), then that child element is not copied to the new tree.</span></span> <span data-ttu-id="caf7c-123">但是，如果命名空間為上述的特殊命名空間，而且該項目的區域名稱為 `ApplyTransforms`，則會反覆運算來源樹狀結構中項目的子節點，並複製到新的樹狀結構 (除非附註的子項目會根據這些規則自我轉換) 中。</span><span class="sxs-lookup"><span data-stu-id="caf7c-123">Instead, if the namespace is the above mentioned special namespace, and the local name of the element is `ApplyTransforms`, then the child nodes of the element in the source tree are iterated, and copied to the new tree (with the exception that annotated child elements are themselves transformed according to these rules).</span></span>  
  
-   <span data-ttu-id="caf7c-124">這有點類似於 XSL 中的轉換規格。</span><span class="sxs-lookup"><span data-stu-id="caf7c-124">This is somewhat analogous to the specification of transforms in XSL.</span></span> <span data-ttu-id="caf7c-125">選取一組節點的查詢類似於範本的 XPath 運算式。</span><span class="sxs-lookup"><span data-stu-id="caf7c-125">The query that selects a set of nodes is analogous to the XPath expression for a template.</span></span> <span data-ttu-id="caf7c-126">若要建立新的程式碼<xref:System.Xml.Linq.XElement>會另存為附註是類似於 XSL 中的序列建構函式和`ApplyTransforms`函式中的項目相當`xsl:apply-templates`XSL 中的項目。</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="caf7c-126">The code to create the new <xref:System.Xml.Linq.XElement> that is saved as an annotation is analogous to the sequence constructor in XSL, and the `ApplyTransforms` element is analogous in function to the `xsl:apply-templates` element in XSL.</span></span>  
  
-   <span data-ttu-id="caf7c-127">採取此種方法的其中一個優點是，當您編寫查詢時，您永遠都是在未修改的來源樹狀上撰寫查詢。</span><span class="sxs-lookup"><span data-stu-id="caf7c-127">One advantage to taking this approach - as you formulate queries, you are always writing queries on the unmodified source tree.</span></span> <span data-ttu-id="caf7c-128">您不必擔心樹狀結構的修改會如何影響您要撰寫的查詢。</span><span class="sxs-lookup"><span data-stu-id="caf7c-128">You need not worry about how modifications to the tree affect the queries that you are writing.</span></span>  
  
## <a name="transforming-a-tree"></a><span data-ttu-id="caf7c-129">轉換樹狀結構</span><span class="sxs-lookup"><span data-stu-id="caf7c-129">Transforming a Tree</span></span>  
 <span data-ttu-id="caf7c-130">這個第一個範例會將所有 `Paragraph` 節點重新命名為 `para`。</span><span class="sxs-lookup"><span data-stu-id="caf7c-130">This first example renames all `Paragraph` nodes to `para`.</span></span>  
  
```vb  
Imports <xmlns:xf="http://www.microsoft.com/LinqToXmlTransform/2007">  
  
Module Module1  
    Dim at As XName = GetXmlNamespace(xf) + "ApplyTransforms"  
  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Paragraph>This is a sentence with <b>bold</b> and <i>italic</i> text.</Paragraph>  
                <Paragraph>More text.</Paragraph>  
            </Root>  
  
        ' Replace Paragraph with p.  
        For Each el In root...<Paragraph>  
            ' same idea as xsl:apply-templates  
            el.AddAnnotation( _  
                <para>  
                    <<%= at %>></>  
                </para>)  
        Next  
  
        ' The XForm function, shown later in this topic, accomplishes the transform  
        Dim newRoot As XElement = XForm(root)  
        Console.WriteLine(newRoot)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="caf7c-131">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="caf7c-131">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <para>This is a sentence with <b>bold</b> and <i>italic</i> text.</para>  
  <para>More text.</para>  
</Root>  
```  
  
## <a name="a-more-complicated-transform"></a><span data-ttu-id="caf7c-132">更複雜的轉換</span><span class="sxs-lookup"><span data-stu-id="caf7c-132">A More Complicated Transform</span></span>  
 <span data-ttu-id="caf7c-133">下列範例會查詢樹狀結構並計算 `Data` 項目的平均值和總和，然後將它們加入為樹狀結構中的新項目。</span><span class="sxs-lookup"><span data-stu-id="caf7c-133">The following example queries the tree and calculates the average and sum of the `Data` elements, and adds them as new elements to the tree.</span></span>  
  
```vb  
Imports <xmlns:xf="http://www.microsoft.com/LinqToXmlTransform/2007">  
  
Module Module1  
    Dim at As XName = GetXmlNamespace(xf) + "ApplyTransforms"  
  
    Sub Main()  
        Dim data As XElement = _  
            <Root>  
                <Data>20</Data>  
                <Data>10</Data>  
                <Data>3</Data>  
            </Root>  
  
        ' While adding annotations, you can query the source tree all you want,  
        ' as the tree is not mutated while annotating.  
        data.AddAnnotation( _  
            <Root>  
                <<%= at %>/>  
                <Average>  
                    <%= _  
                        String.Format("{0:F4}", _  
                        data.Elements("Data") _  
                        .Select(Function(z) CDec(z)).Average()) _  
                    %>  
                </Average>  
                <Sum>  
                    <%= _  
                        data.Elements("Data").Select(Function(z) CInt(z)).Sum() _  
                    %>  
                </Sum>  
            </Root> _  
        )  
  
        Console.WriteLine("Before Transform")  
        Console.WriteLine("----------------")  
        Console.WriteLine(data)  
        Console.WriteLine(vbNewLine)  
  
        ' The XForm function, shown later in this topic, accomplishes the transform  
        Dim newData As XElement = XForm(data)  
  
        Console.WriteLine("After Transform")  
        Console.WriteLine("----------------")  
        Console.WriteLine(newData)  
    End Sub  
End Module   
```  
  
 <span data-ttu-id="caf7c-134">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="caf7c-134">This example produces the following output:</span></span>  
  
```  
Before Transform  
----------------  
<Root>  
  <Data>20</Data>  
  <Data>10</Data>  
  <Data>3</Data>  
</Root>  
  
After Transform  
----------------  
<Root>  
  <Data>20</Data>  
  <Data>10</Data>  
  <Data>3</Data>  
  <Average>11.0000</Average>  
  <Sum>33</Sum>  
</Root>  
```  
  
## <a name="effecting-the-transform"></a><span data-ttu-id="caf7c-135">實行轉換</span><span class="sxs-lookup"><span data-stu-id="caf7c-135">Effecting the Transform</span></span>  
 <span data-ttu-id="caf7c-136">`XForm` 這個小函式會從原始的附註樹狀結構建立轉換的新樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="caf7c-136">A small function, `XForm`, creates a new transformed tree from the original, annotated tree.</span></span>  
  
-   <span data-ttu-id="caf7c-137">函式的虛擬程式碼相當簡單：</span><span class="sxs-lookup"><span data-stu-id="caf7c-137">The pseudo code for the function is quite simple:</span></span>  
  
```  
The function takes an XElement as an argument and returns an XElement.   
If an element has an XElement annotation, then  
    Return a new XElement  
        The name of the new XElement is the annotation element's name.  
        All attributes are copied from the annotation to the new node.  
        All child nodes are copied from the annotation, with the  
            exception that the special node xf:ApplyTransforms is  
            recognized, and the source element's child nodes are  
            iterated. If the source child node is not an XElement, it  
            is copied to the new tree. If the source child is an  
            XElement, then it is transformed by calling this function  
            recursively.  
If an element is not annotated  
    Return a new XElement  
        The name of the new XElement is the source element's name  
        All attributes are copied from the source element to the  
            destination's element.  
        All child nodes are copied from the source element.  
        If the source child node is not an XElement, it is copied to  
            the new tree. If the source child is an XElement, then it  
            is transformed by calling this function recursively.  
```  
  
 <span data-ttu-id="caf7c-138">以下是此函式的實作：</span><span class="sxs-lookup"><span data-stu-id="caf7c-138">Following is the implementation of this function:</span></span>  
  
```vb  
' Build a transformed XML tree per the annotations.  
Function XForm(ByVal source As XElement) As XElement  
    If source.Annotation(Of XElement)() IsNot Nothing Then  
        Dim anno As XElement = source.Annotation(Of XElement)()  
        Return _  
            <<%= anno.Name.ToString() %>>  
                <%= anno.Attributes() %>  
                <%= anno.Nodes().Select(Function(n As XNode) _  
                    GetSubNodes(n, source)) %>  
            </>  
    Else  
        Return _  
            <<%= source.Name %>>  
                <%= source.Attributes() %>  
                <%= source.Nodes().Select(Function(n) GetExpandedNodes(n)) %>  
            </>  
    End If  
End Function  
  
Private Function GetSubNodes(ByVal n As XNode, ByVal s As XElement) As Object  
    Dim annoEl As XElement = TryCast(n, XElement)  
    If annoEl IsNot Nothing Then  
        If annoEl.Name = at Then  
            Return s.Nodes().Select(Function(n2 As XNode) GetExpandedNodes(n2))  
        End If  
    End If  
    Return n  
End Function  
  
Private Function GetExpandedNodes(ByVal n2 As XNode) As XNode  
    Dim e2 As XElement = TryCast(n2, XElement)  
    If e2 Is Nothing Then  
        Return n2  
    Else  
        Return XForm(e2)  
    End If  
End Function  
```  
  
## <a name="complete-example"></a><span data-ttu-id="caf7c-139">完整範例</span><span class="sxs-lookup"><span data-stu-id="caf7c-139">Complete Example</span></span>  
 <span data-ttu-id="caf7c-140">下列程式碼是包含 `XForm` 函式的完整範例。</span><span class="sxs-lookup"><span data-stu-id="caf7c-140">The following code is a complete example that includes the `XForm` function.</span></span> <span data-ttu-id="caf7c-141">此範例包含一些此類型轉換的一般用法：</span><span class="sxs-lookup"><span data-stu-id="caf7c-141">It includes a few of the typical uses of this type of transform:</span></span>  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.Linq  
Imports System.Text  
Imports System.Xml  
Imports System.Xml.Linq  
  
Imports <xmlns:xf="http://www.microsoft.com/LinqToXmlTransform/2007">  
  
Module Module1  
    Dim at As XName = GetXmlNamespace(xf) + "ApplyTransforms"  
  
    ' Build a transformed XML tree per the annotations.  
    Function XForm(ByVal source As XElement) As XElement  
        If source.Annotation(Of XElement)() IsNot Nothing Then  
            Dim anno As XElement = source.Annotation(Of XElement)()  
            Return _  
                <<%= anno.Name.ToString() %>>  
                    <%= anno.Attributes() %>  
                    <%= anno.Nodes().Select(Function(n As XNode) _  
                        GetSubNodes(n, source)) %>  
                </>  
        Else  
            Return _  
                <<%= source.Name %>>  
                    <%= source.Attributes() %>  
                    <%= source.Nodes().Select(Function(n) GetExpandedNodes(n)) %>  
                </>  
        End If  
    End Function  
  
    Private Function GetSubNodes(ByVal n As XNode, ByVal s As XElement) As Object  
        Dim annoEl As XElement = TryCast(n, XElement)  
        If annoEl IsNot Nothing Then  
            If annoEl.Name = at Then  
                Return s.Nodes().Select(Function(n2 As XNode) GetExpandedNodes(n2))  
            End If  
        End If  
        Return n  
    End Function  
  
    Private Function GetExpandedNodes(ByVal n2 As XNode) As XNode  
        Dim e2 As XElement = TryCast(n2, XElement)  
        If e2 Is Nothing Then  
            Return n2  
        Else  
            Return XForm(e2)  
        End If  
    End Function  
  
    Sub Main()  
        Dim root As XElement = _  
<Root Att1='123'>  
    <!--A comment-->  
    <Child>1</Child>  
    <Child>2</Child>  
    <Other>  
        <GC>3</GC>  
        <GC>4</GC>  
    </Other>  
    <SomeMixedContent>This is <i>an</i> element that <b>has</b> some mixed content</SomeMixedContent>  
    <AnUnchangedElement>42</AnUnchangedElement>  
</Root>  
  
        ' Each of the following serves the same semantic purpose as  
        ' XSLT templates and sequence constructors.  
  
        ' Replace Child with NewChild.  
        For Each el In root.<Child>  
            el.AddAnnotation(<NewChild><%= CStr(el) %></NewChild>)  
        Next  
  
        ' Replace first GC with GrandChild, add an attribute.  
        For Each el In root...<GC>.Take(1)  
            el.AddAnnotation(<GrandChild ANewAttribute='999'><%= CStr(el) %></GrandChild>)  
        Next  
  
        ' Replace Other with NewOther, add new child elements around original content.  
        For Each el In root.<Other>  
            el.AddAnnotation( _  
                <NewOther>  
                    <MyNewChild>1</MyNewChild>  
                    <<%= at %>></>  
                    <ChildThatComesAfter/>  
                </NewOther>)  
        Next  
  
        ' Change name of element that has mixed content.  
        root...<SomeMixedContent>(0).AddAnnotation( _  
                <MixedContent><<%= at %>></></MixedContent>)  
  
        ' Replace <b> with <Bold>.  
        For Each el In root...<b>  
            el.AddAnnotation(<Bold><<%= at %>></></Bold>)  
        Next  
  
        ' Replace <i> with <Italic>.  
        For Each el In root...<i>  
            el.AddAnnotation(<Italic><<%= at %>></></Italic>)  
        Next  
  
        Console.WriteLine("Before Transform")  
        Console.WriteLine("----------------")  
        Console.WriteLine(root)  
        Console.WriteLine(vbNewLine)  
        Dim newRoot As XElement = XForm(root)  
  
        Console.WriteLine("After Transform")  
        Console.WriteLine("----------------")  
        Console.WriteLine(newRoot)  
    End Sub  
End Module   
```  
  
 <span data-ttu-id="caf7c-142">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="caf7c-142">This example produces the following output:</span></span>  
  
```  
Before Transform  
----------------  
<Root Att1="123">  
  <!--A comment-->  
  <Child>1</Child>  
  <Child>2</Child>  
  <Other>  
    <GC>3</GC>  
    <GC>4</GC>  
  </Other>  
  <SomeMixedContent>This is <i>an</i> element that <b>has</b> some mixed content</SomeMixedContent>  
  <AnUnchangedElement>42</AnUnchangedElement>  
</Root>  
  
After Transform  
----------------  
<Root Att1="123">  
  <!--A comment-->  
  <NewChild>1</NewChild>  
  <NewChild>2</NewChild>  
  <NewOther>  
    <MyNewChild>1</MyNewChild>  
    <GrandChild ANewAttribute="999">3</GrandChild>  
    <GC>4</GC>  
    <ChildThatComesAfter />  
  </NewOther>  
  <MixedContent>This is <Italic>an</Italic> element that <Bold>has</Bold> some mixed content</MixedContent>  
  <AnUnchangedElement>42</AnUnchangedElement>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="caf7c-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="caf7c-143">See Also</span></span>  
 [<span data-ttu-id="caf7c-144">進階的 LINQ to XML 程式設計 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="caf7c-144">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
