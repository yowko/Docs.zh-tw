---
title: HOW TO：填入 XML 樹狀結構使用 XmlWriter (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 5792a0eb-94ee-440d-b601-58cca8c0ee0b
ms.openlocfilehash: de020444950695e27b9d840dac41fab74b9c7eba
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58835423"
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-visual-basic"></a><span data-ttu-id="76bd4-102">HOW TO：填入 XML 樹狀結構使用 XmlWriter (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="76bd4-102">How to: Populate an XML Tree with an XmlWriter (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="76bd4-103">填入 XML 樹狀的其中一種方式是使用 <xref:System.Xml.Linq.XContainer.CreateWriter%2A> 來建立 <xref:System.Xml.XmlWriter>，然後寫入到 <xref:System.Xml.XmlWriter> 中。</span><span class="sxs-lookup"><span data-stu-id="76bd4-103">One way to populate an XML tree is to use <xref:System.Xml.Linq.XContainer.CreateWriter%2A> to create an <xref:System.Xml.XmlWriter>, and then write to the <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="76bd4-104">XML 樹狀會以寫入到 <xref:System.Xml.XmlWriter> 的所有節點填入。</span><span class="sxs-lookup"><span data-stu-id="76bd4-104">The XML tree is populated with all nodes that are written to the <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="76bd4-105">當您使用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 搭配預期寫入 <xref:System.Xml.XmlWriter> 的其他類別 (例如，<xref:System.Xml.Xsl.XslCompiledTransform>) 時，您通常會使用這個方法。</span><span class="sxs-lookup"><span data-stu-id="76bd4-105">You would typically use this method when you use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] with another class that expects to write to an <xref:System.Xml.XmlWriter>, such as <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76bd4-106">範例</span><span class="sxs-lookup"><span data-stu-id="76bd4-106">Example</span></span>  
 <span data-ttu-id="76bd4-107"><xref:System.Xml.Linq.XContainer.CreateWriter%2A> 的其中一個可能的使用時機為叫用 XSLT 轉換時。</span><span class="sxs-lookup"><span data-stu-id="76bd4-107">One possible use for <xref:System.Xml.Linq.XContainer.CreateWriter%2A> is when invoking an XSLT transformation.</span></span> <span data-ttu-id="76bd4-108">這個範例會建立 XML 樹狀結構、從 XML 樹狀結構建立 <xref:System.Xml.XmlReader>、建立新文件，然後建立 <xref:System.Xml.XmlWriter> 來寫入新文件。</span><span class="sxs-lookup"><span data-stu-id="76bd4-108">This example creates an XML tree, creates an <xref:System.Xml.XmlReader> from the XML tree, creates a new document, and then creates an <xref:System.Xml.XmlWriter> to write into the new document.</span></span> <span data-ttu-id="76bd4-109">接著，它會叫用 XSLT 轉換，以傳入至 <xref:System.Xml.XmlReader> 和 <xref:System.Xml.XmlWriter>。</span><span class="sxs-lookup"><span data-stu-id="76bd4-109">It then invokes the XSLT transformation, passing in <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="76bd4-110">轉換成功完成後，系統會使用轉換的結果填入新的 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="76bd4-110">After the transformation successfully completes, the new XML tree is populated with the results of the transformation.</span></span>  
  
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
  
 <span data-ttu-id="76bd4-111">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="76bd4-111">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="76bd4-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76bd4-112">See also</span></span>

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A>
- <xref:System.Xml.XmlWriter>
- <xref:System.Xml.Xsl.XslCompiledTransform>
- [<span data-ttu-id="76bd4-113">建立 XML 樹狀結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="76bd4-113">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
