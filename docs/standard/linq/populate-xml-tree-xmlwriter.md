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
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml"></a>如何使用 XmlWriter 填入 XML 樹狀結構 (LINQ to XML)

填入 XML 樹狀的其中一種方式是使用 <xref:System.Xml.Linq.XContainer.CreateWriter%2A> 來建立 <xref:System.Xml.XmlWriter>，然後寫入到 <xref:System.Xml.XmlWriter> 中。 XML 樹狀會以寫入到 <xref:System.Xml.XmlWriter> 的所有節點填入。

當您使用 LINQ to XML 與另一個預期要寫入的類別（例如）時，通常會使用這個方法 <xref:System.Xml.XmlWriter> <xref:System.Xml.Xsl.XslCompiledTransform> 。

## <a name="example-create-an-xmlwriter-to-accept-the-output-of-an-xslt-transformation"></a>範例：建立 XmlWriter 以接受 XSLT 轉換的輸出

您可以使用 <xref:System.Xml.Linq.XContainer.CreateWriter%2A> 建立 <xref:System.Xml.XmlWriter> 來接受 XSLT 轉換的輸出。 下列範例會顯示下列內容：

- 建立 XML 樹狀結構和 <xref:System.Xml.XmlReader> 以從中讀取。
- 建立新的樹狀結構，以及要寫入的樹狀結構 <xref:System.Xml.XmlWriter> 。
- 叫用 XSLT 轉換，並為其提供  <xref:System.Xml.XmlReader> 和 <xref:System.Xml.XmlWriter> 。

接著，轉換會填入新的樹狀結構。

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

這個範例會產生下列輸出：

```xml
<Root>
  <C1>Child1 data</C1>
  <C2>Child2 data</C2>
</Root>
```

## <a name="see-also"></a>另請參閱

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A>
- <xref:System.Xml.XmlWriter>
- <xref:System.Xml.Xsl.XslCompiledTransform>
- [XML 樹狀結構](functional-construction.md)
