---
title: "如何︰ 填入 XML 樹狀結構使用 XmlWriter (LINQ to XML) (Visual Basic) |Microsoft 文件"
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
ms.assetid: 5792a0eb-94ee-440d-b601-58cca8c0ee0b
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
ms.openlocfilehash: dfd10ec04e7293d90929d6f629201868028819ad
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-visual-basic"></a>如何︰ 填入 XML 樹狀結構使用 XmlWriter (LINQ to XML) (Visual Basic)
填入 XML 樹狀結構的一個方式是使用<xref:System.Xml.Linq.XContainer.CreateWriter%2A>建立<xref:System.Xml.XmlWriter>，然後寫入到<xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter> </xref:System.Xml.XmlWriter> </xref:System.Xml.Linq.XContainer.CreateWriter%2A> 寫入至<xref:System.Xml.XmlWriter>。</xref:System.Xml.XmlWriter>的所有節點都填入 XML 樹狀結構  
  
 您通常會使用此方法，當您使用[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]的預期寫入的另一個類別<xref:System.Xml.XmlWriter>，例如<xref:System.Xml.Xsl.XslCompiledTransform>。</xref:System.Xml.Xsl.XslCompiledTransform> </xref:System.Xml.XmlWriter>  
  
## <a name="example"></a>範例  
 可能的用法之一<xref:System.Xml.Linq.XContainer.CreateWriter%2A>時機為叫用 XSLT 轉換。</xref:System.Xml.Linq.XContainer.CreateWriter%2A> 這個範例會建立 XML 樹狀結構，然後建立<xref:System.Xml.XmlReader>從 XML 樹狀結構中，會建立新的文件，並接著會建立<xref:System.Xml.XmlWriter>來寫入新文件。</xref:System.Xml.XmlWriter> </xref:System.Xml.XmlReader> 然後它叫用 XSLT 轉換，以傳遞<xref:System.Xml.XmlReader>和<xref:System.Xml.XmlWriter>。</xref:System.Xml.XmlWriter> </xref:System.Xml.XmlReader> 轉換成功完成後，系統會使用轉換的結果填入新的 XML 樹狀結構。  
  
```vb  
Dim xslMarkup As XDocument = _  
    <?xml version='1.0'?>   
    <xsl:stylesheet xmlns:xsl='http://www.w3.org/1999/XSL/Transform' version='1.0'>  
        <xsl:template match='/Parent'>  
            <Root>  
                <C1>  
                    <xsl:value-of select='Child1'/>  
                </C1>  
                <C2>  
                    <xsl:value-of select='Child2'/>  
                </C2>  
            </Root>  
        </xsl:template>  
    </xsl:stylesheet>  
  
Dim xmlTree As XDocument = _  
    <?xml version='1.0'?>  
    <Parent>  
        <Child1>Child1 data</Child1>  
        <Child2>Child2 data</Child2>  
    </Parent>  
  
Dim newTree As XDocument = New XDocument()  
Using writer As XmlWriter = newTree.CreateWriter()  
    ' Load the style sheet.  
    Dim xslt As XslCompiledTransform = New XslCompiledTransform()  
    xslt.Load(xslMarkup.CreateReader())  
  
    ' Execute the transformation and output the results to a writer.  
    xslt.Transform(xmlTree.CreateReader(), writer)  
End Using  
  
Console.WriteLine(newTree)  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Xml.Linq.XContainer.CreateWriter%2A></xref:System.Xml.Linq.XContainer.CreateWriter%2A>   
 <xref:System.Xml.XmlWriter></xref:System.Xml.XmlWriter>   
 <xref:System.Xml.Xsl.XslCompiledTransform></xref:System.Xml.Xsl.XslCompiledTransform>   
 [建立 XML 樹狀結構 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
