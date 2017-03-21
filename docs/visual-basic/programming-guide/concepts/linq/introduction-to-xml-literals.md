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
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 391dd14f971f91d4d128841a7ebd24981266846a
ms.lasthandoff: 03/13/2017

---
# <a name="introduction-to-xml-literals-in-visual-basic"></a>Visual Basic 中的 XML 常值簡介
本節提供在 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 中建立 XML 樹狀結構的相關資訊。  
  
 使用 LINQ 查詢的結果做為內容，XML 樹狀結構的相關資訊，請參閱[功能建構 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md)。  
  
 如需有關 XML 常值的[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]，請參閱[概觀的 LINQ to XML 在 Visual Basic 中](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)。  
  
## <a name="creating-xml-trees"></a>建立 XML 樹狀  
 下列範例示範如何建立<xref:System.Xml.Linq.XElement>，在此情況下`contacts`:</xref:System.Xml.Linq.XElement>  
  
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
  
### <a name="creating-an-xelement-with-simple-content"></a>建立包含簡單內容的 XElement  
 您可以建立<xref:System.Xml.Linq.XElement>，其中包含簡單內容，如下所示︰</xref:System.Xml.Linq.XElement>  
  
```vb  
Dim n as XElement = <Customer>Adventure Works</Customer>  
Console.WriteLine(n)   
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
### <a name="creating-an-empty-element"></a>建立空項目  
 您可以建立空白<xref:System.Xml.Linq.XElement>，如下︰</xref:System.Xml.Linq.XElement>  
  
```vb  
Dim n As XElement = <Customer/>  
Console.WriteLine(n)  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<Customer />  
```  
  
### <a name="using-embedded-expressions"></a>使用內嵌的運算式  
 XML 常值的其中一個重要功能是，這些 XML 常值允許內嵌的運算式。 內嵌的運算式可讓您評估運算式，並將運算式的結果插入到 XML 樹狀中。 如果運算式評估為一種<xref:System.Xml.Linq.XElement>，項目插入到樹狀結構。</xref:System.Xml.Linq.XElement> 如果運算式評估為一種<xref:System.Xml.Linq.XAttribute>，將屬性插入到樹狀結構。</xref:System.Xml.Linq.XAttribute> 您可以將項目和屬性僅插入到有效的樹狀中。  
  
 請注意，只有單一運算式可以插入到內嵌的運算式中，這點很重要。 您無法內嵌多個陳述式。 如果運算式的延伸超過單一行，您必須使用行接續字元。  
  
 如果您使用內嵌的運算式，將現有的節點 (包括項目) 和屬性加入到新的 XML 樹狀結構，而且如果現有的節點已經成為父代，這些節點就會遭到複製。 新複製的節點會附加到新的 XML 樹狀結構中。 如果現有的節點沒有成為父代，這些節點只會附加到新的 XML 樹狀結構。 本主題中的最後一個範例會示範這個情況。  
  
 下列範例使用內嵌的運算式，將項目插入到樹狀結構中：  
  
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
  
 這個範例會產生下列輸出：  
  
```xml  
<Root>  
  <Child>Contents</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-content"></a>將內嵌的運算式用於內容  
 您可以使用內嵌的運算式提供項目的內容：  
  
```vb  
Dim str As String  
str = "Some content"  
Dim root As XElement = <Root><%= str %></Root>  
Console.WriteLine(root)  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<Root>Some content</Root>  
```  
  
### <a name="using-a-linq-query-in-an-embedded-expression"></a>在內嵌的運算式中使用 LINQ 查詢  
 您可以將 LINQ 查詢的結果用於項目的內容：  
  
```vb  
Dim arr As Integer() = {1, 2, 3}  
  
Dim n As XElement = _  
    <Root>  
        <%= From i In arr Select <Child><%= i %></Child> %>  
    </Root>  
  
Console.WriteLine(n)  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Child>3</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-node-names"></a>將內嵌的運算式用於節點名稱  
 您也可以使用內嵌的運算式來計算屬性名稱、屬性值、項目名稱與項目值：  
  
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
  
 這個範例會產生下列輸出：  
  
```xml  
<Root att="aValue">  
  <ele>eValue</ele>  
</Root>  
```  
  
### <a name="cloning-vs-attaching"></a>複製與附加之比較  
 如先前所述，如果您使用內嵌的運算式，將現有的節點 (包括項目) 和屬性加入到新的 XML 樹狀結構，而且如果現有的節點已經成為父代，這些節點就會遭到複製，而新複製的節點會附加到新的 XML 樹狀結構中。 如果現有的節點沒有成為父代，這些節點只會附加到新的 XML 樹狀結構。  
  
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
  
 這個範例會產生下列輸出：  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a>另請參閱  
 [建立 XML 樹狀結構 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
