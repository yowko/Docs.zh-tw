---
title: HOW TO：使用註釋轉換 LINQ to XML 樹狀結構的 XSLT 樣式 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 08e91fa2-dac2-4463-9ef1-87b1ac3fa890
ms.openlocfilehash: 9ebff2276fc9f574989530fdb07a0d0875ff74a3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648805"
---
# <a name="how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style-visual-basic"></a>HOW TO：使用註釋轉換 LINQ to XML 樹狀結構的 XSLT 樣式 (Visual Basic)
附註可用於簡化 XML 樹狀的轉換。  
  
 有些 XML 文件為「中央具有混合內容的文件」。 使用這類文件時，您不一定要知道項目子節點的組織結構。 例如，包含文字的節點類似如下：  
  
```xml  
<text>A phrase with <b>bold</b> and <i>italic</i> text.</text>  
```  
  
 針對任何指定的文字節點，可能會有任何數目的 `<b>` 和 `<i>` 子項目。 這個方法會延伸到數個其他情況： 例如，可以包含各種不同的子元素，例如一般段落、 分項段落與點陣圖的頁面。 資料表中的儲存格可能包含文字、下拉式清單或點陣圖。 文件中心 XML 的其中一個主要特性為，您不知道任何特定項目將會有哪個子項目。  
  
 如果您要在樹狀結構中，轉換您不一定了解太多您要轉換之項目子系的項目，則使用附註的這個方法是一個有效的方法。  
  
 方法的摘要如下：  
  
- 首先，在樹狀結構中，以替代項目附註項目。  
  
- 接著，逐一查看整個樹狀結構，建立您以其附註取代每個項目的新樹狀結構。 這個範本會在名稱為 `XForm` 的函式中，實作反覆運算並建立新的樹狀結構。  
  
 就細節而言，此方法包含：  
  
- 執行一或多個 LINQ to XML 查詢，這些查詢會傳回您要從一個組織結構轉換為另一個組織結構的項目集。 針對查詢中的每個項目，加入新的 <xref:System.Xml.Linq.XElement> 物件做為項目的附註。 這個新項目將會取代已轉換之新樹狀結構中的附註項目。 如本範例的示範，這是容易撰寫的簡單程式碼。  
  
- 加入為附註的新項目可以包含新的子節點；它可以形成具有任何所需組織結構的子樹狀結構。  
  
- 有一個特殊規則：如果新項目的子節點位於不同的命名空間中，也就是針對此目的所形成的命名空間 (在此範例中，命名空間為 `http://www.microsoft.com/LinqToXmlTransform/2007`)，則不會將該子項目複製到新的樹狀結構中。 但是，如果命名空間為上述的特殊命名空間，而且該項目的區域名稱為 `ApplyTransforms`，則會反覆運算來源樹狀結構中項目的子節點，並複製到新的樹狀結構 (除非附註的子項目會根據這些規則自我轉換) 中。  
  
- 這有點類似於 XSL 中的轉換規格。 選取一組節點的查詢類似於範本的 XPath 運算式。 建立另存為附註之新 <xref:System.Xml.Linq.XElement> 的程式碼類似於 XSL 中的序列建構函式，而 `ApplyTransforms` 項目在功能上則類似於 XSL 中的 `xsl:apply-templates` 項目。  
  
- 採取此種方法的其中一個優點是，當您編寫查詢時，您永遠都是在未修改的來源樹狀結構上撰寫查詢。 您不必擔心樹狀結構的修改會如何影響您要撰寫的查詢。  
  
## <a name="transforming-a-tree"></a>轉換樹狀結構  
 這個第一個範例會將所有 `Paragraph` 節點重新命名為 `para`。  
  
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
  
 這個範例會產生下列輸出：  
  
```xml  
<Root>  
  <para>This is a sentence with <b>bold</b> and <i>italic</i> text.</para>  
  <para>More text.</para>  
</Root>  
```  
  
## <a name="a-more-complicated-transform"></a>更複雜的轉換  
 下列範例會查詢樹狀結構並計算 `Data` 項目的平均值和總和，然後將它們加入為樹狀結構中的新項目。  
  
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
  
 這個範例會產生下列輸出：  
  
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
  
## <a name="effecting-the-transform"></a>實行轉換  
 `XForm` 這個小函式會從原始的附註樹狀結構建立轉換的新樹狀結構。  
  
- 函式的虛擬程式碼相當簡單：  
  
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
  
 以下是此函式的實作：  
  
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
  
## <a name="complete-example"></a>完整範例  
 下列程式碼是包含 `XForm` 函式的完整範例。 此範例包含一些此類型轉換的一般用法：  
  
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
  
 這個範例會產生下列輸出：  
  
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
  
## <a name="see-also"></a>另請參閱

- [進階的 LINQ to XML 程式設計 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
