---
title: 如何使用 XmlWriter 填入 XML 樹狀結構-LINQ to XML
description: '若要以 c # 和 Visual Basic 填入 XML 樹狀結構，請使用 System.xml.linq.xcontainer.createwriter 建立 XMLWriter，然後寫入 XmlWriter。'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: cd5674d1-5c54-4efc-ba68-e23b2875295f
ms.openlocfilehash: 3f8005eca009ae5f2102444a5494336d2caa2450
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552262"
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml"></a><span data-ttu-id="71c9a-103">如何使用 XmlWriter 填入 XML 樹狀結構 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="71c9a-103">How to populate an XML tree with an XmlWriter (LINQ to XML)</span></span>

<span data-ttu-id="71c9a-104">填入 XML 樹狀的其中一種方式是使用 <xref:System.Xml.Linq.XContainer.CreateWriter%2A> 來建立 <xref:System.Xml.XmlWriter>，然後寫入到 <xref:System.Xml.XmlWriter> 中。</span><span class="sxs-lookup"><span data-stu-id="71c9a-104">One way to populate an XML tree is to use <xref:System.Xml.Linq.XContainer.CreateWriter%2A> to create an <xref:System.Xml.XmlWriter>, and then write to the <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="71c9a-105">XML 樹狀會以寫入到 <xref:System.Xml.XmlWriter> 的所有節點填入。</span><span class="sxs-lookup"><span data-stu-id="71c9a-105">The XML tree is populated with all nodes that are written to the <xref:System.Xml.XmlWriter>.</span></span>

<span data-ttu-id="71c9a-106">當您使用 LINQ to XML 與另一個預期要寫入的類別（例如）時，通常會使用這個方法 <xref:System.Xml.XmlWriter> <xref:System.Xml.Xsl.XslCompiledTransform> 。</span><span class="sxs-lookup"><span data-stu-id="71c9a-106">You'd typically use this method when you use LINQ to XML with another class that expects to write to an <xref:System.Xml.XmlWriter>, such as <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>

## <a name="example-create-an-xmlwriter-to-accept-the-output-of-an-xslt-transformation"></a><span data-ttu-id="71c9a-107">範例：建立 XmlWriter 以接受 XSLT 轉換的輸出</span><span class="sxs-lookup"><span data-stu-id="71c9a-107">Example: Create an XmlWriter to accept the output of an XSLT transformation</span></span>

<span data-ttu-id="71c9a-108">您可以使用 <xref:System.Xml.Linq.XContainer.CreateWriter%2A> 建立 <xref:System.Xml.XmlWriter> 來接受 XSLT 轉換的輸出。</span><span class="sxs-lookup"><span data-stu-id="71c9a-108">You can use <xref:System.Xml.Linq.XContainer.CreateWriter%2A> to create an <xref:System.Xml.XmlWriter> to accept the output of an XSLT transformation.</span></span> <span data-ttu-id="71c9a-109">下列範例會顯示下列內容：</span><span class="sxs-lookup"><span data-stu-id="71c9a-109">This is shown in the following example, which does the following:</span></span>

- <span data-ttu-id="71c9a-110">建立 XML 樹狀結構和 <xref:System.Xml.XmlReader> 以從中讀取。</span><span class="sxs-lookup"><span data-stu-id="71c9a-110">Creates an XML tree and an <xref:System.Xml.XmlReader> to read from it.</span></span>
- <span data-ttu-id="71c9a-111">建立新的樹狀結構，以及要寫入的樹狀結構 <xref:System.Xml.XmlWriter> 。</span><span class="sxs-lookup"><span data-stu-id="71c9a-111">Creates a new tree and an <xref:System.Xml.XmlWriter> to write to it.</span></span>
- <span data-ttu-id="71c9a-112">叫用 XSLT 轉換，並為其提供  <xref:System.Xml.XmlReader> 和 <xref:System.Xml.XmlWriter> 。</span><span class="sxs-lookup"><span data-stu-id="71c9a-112">Invokes the XSLT transformation, providing it with the  <xref:System.Xml.XmlReader> and the <xref:System.Xml.XmlWriter>.</span></span>

<span data-ttu-id="71c9a-113">接著，轉換會填入新的樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="71c9a-113">The transformation then populates the new tree.</span></span>

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

<span data-ttu-id="71c9a-114">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="71c9a-114">This example produces the following output:</span></span>

```xml
<Root>
  <C1>Child1 data</C1>
  <C2>Child2 data</C2>
</Root>
```

## <a name="see-also"></a><span data-ttu-id="71c9a-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71c9a-115">See also</span></span>

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A>
- <xref:System.Xml.XmlWriter>
- <xref:System.Xml.Xsl.XslCompiledTransform>
- [<span data-ttu-id="71c9a-116">XML 樹狀結構</span><span class="sxs-lookup"><span data-stu-id="71c9a-116">XML trees</span></span>](functional-construction.md)
