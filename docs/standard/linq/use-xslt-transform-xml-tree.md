---
title: 使用 XSLT 轉換 XML 樹狀結構-LINQ to XML
description: 瞭解如何使用 XSLT 來轉換 XML 樹狀結構，並使用 XmlReader 來讀取和 XmlWriter 以進行寫入。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 373a2699-d4c5-471b-9bda-c1f0ab73b477
ms.openlocfilehash: 9a8f85b4f563d177d00d41feeac6fd8cd61375a2
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552177"
---
# <a name="use-xslt-to-transform-an-xml-tree-linq-to-xml"></a>使用 XSLT 轉換 XML 樹狀結構 (LINQ to XML) 

您可以使用 XSLT 來轉換 XML 樹狀結構， <xref:System.Xml.XmlReader> 並使用讀取和 <xref:System.Xml.XmlWriter> 寫入。

## <a name="example-use-xslt-to-transform-an-xml-tree-using-xmlreader-to-read-and-xmlwriter-to-write"></a>範例：使用 XSLT 轉換 XML 樹狀結構，並使用 `XMLReader` 讀取和 `XMLWriter` 寫入

這個範例會建立 XML 樹狀結構，並使用 XSLT 來轉換它。 它會利用 <xref:System.Xml.XmlReader> 來讀取原始樹狀結構，並使用 <xref:System.Xml.XmlWriter> 來寫入轉換的版本。

首先，它會建立：

- XML 樹狀結構。
- <xref:System.Xml.XmlReader>XML 樹狀結構的。
- 用來保存 XSLT 輸出的新檔。
- <xref:System.Xml.XmlWriter>要將轉換的樹狀結構寫入新檔的。

然後，它會叫用使用的 XSLT 轉換 <xref:System.Xml.XmlReader> 來讀取原始的 XML 樹狀結構，並叫用 <xref:System.Xml.XmlWriter> 來將轉換的樹狀結構寫入新檔。

```csharp
string xslt = @"<?xml version='1.0'?>
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

var oldDocument = new XDocument(
    new XElement("Parent",
        new XElement("Child1", "Child1 data"),
        new XElement("Child2", "Child2 data")
    )
);

var newDocument = new XDocument();

using (var stringReader = new StringReader(xslt))
{
    using (XmlReader xsltReader = XmlReader.Create(stringReader))
    {
        var transformer = new XslCompiledTransform();
        transformer.Load(xsltReader);
        using (XmlReader oldDocumentReader = oldDocument.CreateReader())
        {
            using (XmlWriter newDocumentWriter = newDocument.CreateWriter())
            {
                transformer.Transform(oldDocumentReader, newDocumentWriter);
            }
        }
    }
}

string result = newDocument.ToString();
Console.WriteLine(result);
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

Dim xmlTree As XElement = _
    <Parent>
        <Child1>Child1 data</Child1>
        <Child2>Child2 data</Child2>
    </Parent>

Dim newTree As XDocument = New XDocument()

Using writer As XmlWriter = newTree.CreateWriter()
    ' Load the style sheet.
    Dim xslt As XslCompiledTransform = _
        New XslCompiledTransform()
    xslt.Load(xslMarkup.CreateReader())

    ' Execute the transform and output the results to a writer.
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

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.CreateReader%2A?displayProperty=nameWithType>
