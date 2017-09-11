---
title: "序列化至 XmlReader (叫用 XSLT) (Visual Basic) |Microsoft 文件"
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
ms.assetid: 8b64f95a-e8f6-40f7-99f9-a8002c63af96
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
ms.openlocfilehash: 7e1af87fceb9f3f7eae6af6f917037ba80908827
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="serializing-to-an-xmlreader-invoking-xslt-visual-basic"></a><span data-ttu-id="fc8e5-102">序列化至 XmlReader (叫用 XSLT) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fc8e5-102">Serializing to an XmlReader (Invoking XSLT) (Visual Basic)</span></span>
<span data-ttu-id="fc8e5-103">當您使用<xref:System.Xml?displayProperty=fullName>的互通性功能[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]，可用<xref:System.Xml.Linq.XNode.CreateReader%2A>來建立<xref:System.Xml.XmlReader>.</xref:System.Xml.XmlReader> </xref:System.Xml.Linq.XNode.CreateReader%2A> </xref:System.Xml?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="fc8e5-103">When you use the <xref:System.Xml?displayProperty=fullName> interoperability capabilities of [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], you can use <xref:System.Xml.Linq.XNode.CreateReader%2A> to create an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="fc8e5-104">這可讀取的模組<xref:System.Xml.XmlReader>讀取 XML 樹狀結構的節點，並加以處理。</xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="fc8e5-104">The module that reads from this <xref:System.Xml.XmlReader> reads the nodes from the XML tree and processes them accordingly.</span></span>  
  
## <a name="invoking-an-xslt-transformation"></a><span data-ttu-id="fc8e5-105">叫用 XSLT 轉換</span><span class="sxs-lookup"><span data-stu-id="fc8e5-105">Invoking an XSLT Transformation</span></span>  
 <span data-ttu-id="fc8e5-106">此方法的其中一個可能的使用時機為叫用 XSLT 轉換時。</span><span class="sxs-lookup"><span data-stu-id="fc8e5-106">One possible use for this method is when invoking an XSLT transformation.</span></span> <span data-ttu-id="fc8e5-107">您可以建立 XML 樹狀結構、 建立<xref:System.Xml.XmlReader>從 XML 樹狀結構中，建立新的文件，然後再建立<xref:System.Xml.XmlWriter>來寫入新文件。</xref:System.Xml.XmlWriter> </xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="fc8e5-107">You can create an XML tree, create an <xref:System.Xml.XmlReader> from the XML tree, create a new document, and then create an <xref:System.Xml.XmlWriter> to write into the new document.</span></span> <span data-ttu-id="fc8e5-108">然後，您可以叫用 XSLT 轉換，以傳遞<xref:System.Xml.XmlReader>和<xref:System.Xml.XmlWriter>。</xref:System.Xml.XmlWriter> </xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="fc8e5-108">Then, you can invoke the XSLT transformation, passing in <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="fc8e5-109">轉換成功完成後，系統會使用轉換的結果填入新的 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="fc8e5-109">After the transformation successfully completes, the new XML tree is populated with the results of the transformation.</span></span>  
  
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
  
 <span data-ttu-id="fc8e5-110">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="fc8e5-110">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fc8e5-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc8e5-111">See Also</span></span>  
 [<span data-ttu-id="fc8e5-112">序列化 XML 樹狀結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fc8e5-112">Serializing XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
