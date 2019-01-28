---
title: 使用 XSLT 轉換 XML 樹狀結構 (C#)
ms.date: 07/20/2015
ms.assetid: 373a2699-d4c5-471b-9bda-c1f0ab73b477
ms.openlocfilehash: cbba118be31a852420616a667660cef25cb9fd88
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54692307"
---
# <a name="using-xslt-to-transform-an-xml-tree-c"></a><span data-ttu-id="99ea1-102">使用 XSLT 轉換 XML 樹狀結構 (C#)</span><span class="sxs-lookup"><span data-stu-id="99ea1-102">Using XSLT to Transform an XML Tree (C#)</span></span>
<span data-ttu-id="99ea1-103">您可以建立 XML 樹狀結構、從 XML 樹狀結構建立 <xref:System.Xml.XmlReader>、建立新文件，然後建立將寫入新文件中的 <xref:System.Xml.XmlWriter>。</span><span class="sxs-lookup"><span data-stu-id="99ea1-103">You can create an XML tree, create an <xref:System.Xml.XmlReader> from the XML tree, create a new document, and create an <xref:System.Xml.XmlWriter> that will write into the new document.</span></span> <span data-ttu-id="99ea1-104">然後，您可以叫用 (Invoke) XSLT 轉換，將 <xref:System.Xml.XmlReader> 和 <xref:System.Xml.XmlWriter> 傳遞至轉換。</span><span class="sxs-lookup"><span data-stu-id="99ea1-104">Then, you can invoke the XSLT transformation, passing the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> to the transformation.</span></span> <span data-ttu-id="99ea1-105">轉換成功完成後，系統會使用轉換的結果填入新的 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="99ea1-105">After the transformation successfully completes, the new XML tree is populated with the results of the transform.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99ea1-106">範例</span><span class="sxs-lookup"><span data-stu-id="99ea1-106">Example</span></span>  
  
```csharp  
string xslMarkup = @"<?xml version='1.0'?>  
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
</xsl:stylesheet>";  
  
XDocument xmlTree = new XDocument(  
    new XElement("Parent",  
        new XElement("Child1", "Child1 data"),  
        new XElement("Child2", "Child2 data")  
    )  
);  
  
XDocument newTree = new XDocument();  
using (XmlWriter writer = newTree.CreateWriter()) {  
    // Load the style sheet.  
    XslCompiledTransform xslt = new XslCompiledTransform();  
    xslt.Load(XmlReader.Create(new StringReader(xslMarkup)));  
  
    // Execute the transform and output the results to a writer.  
    xslt.Transform(xmlTree.CreateReader(), writer);  
}  
  
Console.WriteLine(newTree);  
```  
  
 <span data-ttu-id="99ea1-107">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="99ea1-107">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="99ea1-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99ea1-108">See also</span></span>

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.CreateReader%2A?displayProperty=nameWithType>
- [<span data-ttu-id="99ea1-109">進階 LINQ to XML 程式設計 (C#)</span><span class="sxs-lookup"><span data-stu-id="99ea1-109">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
