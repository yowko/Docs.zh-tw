---
title: 如何：使用 XmlWriter 填入 XML 樹狀結構 (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: cd5674d1-5c54-4efc-ba68-e23b2875295f
ms.openlocfilehash: cc3aeb8e8fbef3b109c9bc591084f0d033f5f476
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323670"
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-c"></a><span data-ttu-id="d8207-102">如何：使用 XmlWriter 填入 XML 樹狀結構 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d8207-102">How to: Populate an XML Tree with an XmlWriter (LINQ to XML) (C#)</span></span>
<span data-ttu-id="d8207-103">填入 XML 樹狀結構的其中一種方式是使用 <xref:System.Xml.Linq.XContainer.CreateWriter%2A> 來建立 <xref:System.Xml.XmlWriter>，然後寫入到 <xref:System.Xml.XmlWriter> 中。</span><span class="sxs-lookup"><span data-stu-id="d8207-103">One way to populate an XML tree is to use <xref:System.Xml.Linq.XContainer.CreateWriter%2A> to create an <xref:System.Xml.XmlWriter>, and then write to the <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="d8207-104">XML 樹狀結構會以寫入到 <xref:System.Xml.XmlWriter> 的所有節點填入。</span><span class="sxs-lookup"><span data-stu-id="d8207-104">The XML tree is populated with all nodes that are written to the <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="d8207-105">當您使用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 搭配預期寫入 <xref:System.Xml.XmlWriter> 的其他類別 (例如，<xref:System.Xml.Xsl.XslCompiledTransform>) 時，您通常會使用這個方法。</span><span class="sxs-lookup"><span data-stu-id="d8207-105">You would typically use this method when you use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] with another class that expects to write to an <xref:System.Xml.XmlWriter>, such as <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8207-106">範例</span><span class="sxs-lookup"><span data-stu-id="d8207-106">Example</span></span>  
 <span data-ttu-id="d8207-107"><xref:System.Xml.Linq.XContainer.CreateWriter%2A> 的其中一個可能的使用時機為叫用 XSLT 轉換時。</span><span class="sxs-lookup"><span data-stu-id="d8207-107">One possible use for <xref:System.Xml.Linq.XContainer.CreateWriter%2A> is when invoking an XSLT transformation.</span></span> <span data-ttu-id="d8207-108">這個範例會建立 XML 樹狀結構、從 XML 樹狀結構建立 <xref:System.Xml.XmlReader>、建立新文件，然後建立 <xref:System.Xml.XmlWriter> 來寫入新文件。</span><span class="sxs-lookup"><span data-stu-id="d8207-108">This example creates an XML tree, creates an <xref:System.Xml.XmlReader> from the XML tree, creates a new document, and then creates an <xref:System.Xml.XmlWriter> to write into the new document.</span></span> <span data-ttu-id="d8207-109">接著，它會叫用 XSLT 轉換，以傳入至 <xref:System.Xml.XmlReader> 和 <xref:System.Xml.XmlWriter>。</span><span class="sxs-lookup"><span data-stu-id="d8207-109">It then invokes the XSLT transformation, passing in <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="d8207-110">轉換成功完成後，系統會使用轉換的結果填入新的 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="d8207-110">After the transformation successfully completes, the new XML tree is populated with the results of the transformation.</span></span>  
  
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
using (XmlWriter writer = newTree.CreateWriter())  
{  
    // Load the style sheet.  
    XslCompiledTransform xslt = new XslCompiledTransform();  
    xslt.Load(XmlReader.Create(new StringReader(xslMarkup)));  
  
    // Execute the transformation and output the results to a writer.  
    xslt.Transform(xmlTree.CreateReader(), writer);  
}  
  
Console.WriteLine(newTree);  
```  
  
 <span data-ttu-id="d8207-111">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="d8207-111">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d8207-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="d8207-112">See Also</span></span>  
 <xref:System.Xml.Linq.XContainer.CreateWriter%2A>  
 <xref:System.Xml.XmlWriter>  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 [<span data-ttu-id="d8207-113">建立 XML 樹狀結構 (C#)</span><span class="sxs-lookup"><span data-stu-id="d8207-113">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
