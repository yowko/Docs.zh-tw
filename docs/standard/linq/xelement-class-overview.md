---
title: System.xml.linq.xelement> 類別總覽
description: System.xml.linq.xelement> 類別表示 XML 元素。 您可以使用它來建立和變更元素、新增屬性和子系，以及進行序列化。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 2b9f0cd8-a1d1-4037-accf-0f38a410fa11
ms.openlocfilehash: 325afd09661532fe44aecf89fe9784520274638e
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552175"
---
# <a name="xelement-class-overview"></a>System.xml.linq.xelement> 類別總覽

<xref:System.Xml.Linq.XElement>類別是 LINQ to XML 中的其中一個基礎類別。 它代表 XML 項目。 下列清單顯示您可以使用此類別的內容：

- 建立元素。
- 變更元素的內容。
- 加入、變更或刪除子項目。
- 將屬性加入至元素。
- 以文字格式序列化元素的內容。

您也可以與 <xref:System.Xml?displayProperty=nameWithType> 中的其他類別相互溝通，例如，<xref:System.Xml.XmlReader>、<xref:System.Xml.XmlWriter> 和 <xref:System.Xml.Xsl.XslCompiledTransform>。

本文描述類別所提供的功能 <xref:System.Xml.Linq.XElement> 。

## <a name="construct-xml-trees"></a>結構 XML 樹狀結構

您可以用不同的方式來建立 XML 樹狀結構，包括下列各項：

- 您可以在程式碼中建構 XML 樹狀結構。 如需詳細資訊，請參閱 [XML 樹狀](functional-construction.md)結構。
- 您可以剖析來自各種來源的 XML，包括 <xref:System.IO.TextReader>、文字檔或網路位址 (URL)。 如需詳細資訊，請參閱 [剖析 XML](parse-string.md)。
- 您可以使用 <xref:System.Xml.XmlReader> 來填入樹狀結構。 如需詳細資訊，請參閱<xref:System.Xml.Linq.XNode.ReadFrom%2A>。
- 如果您有可將內容寫入至的模組， <xref:System.Xml.XmlWriter> 您可以使用 <xref:System.Xml.Linq.XContainer.CreateWriter%2A> 方法來建立寫入器、將寫入器傳遞至模組，然後使用寫入的內容 <xref:System.Xml.XmlWriter> 來填入 XML 樹狀結構。

下列範例會建立一個樹狀結構。 C # 版本會使用 nested 元素建立。 您可以在 Visual Basic 中使用相同的技術，但此範例會使用 XML 常值。

```csharp
XElement contacts =
    new XElement("Contacts",
        new XElement("Contact",
            new XElement("Name", "Patrick Hines"),
            new XElement("Phone", "206-555-0144"),
            new XElement("Address",
                new XElement("Street1", "123 Main St"),
                new XElement("City", "Mercer Island"),
                new XElement("State", "WA"),
                new XElement("Postal", "68042")
            )
        )
    );
```

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

您也可以使用 LINQ to XML 查詢來填入 XML 樹狀結構，如下列範例所示：

```csharp
XElement srcTree = new XElement("Root",
    new XElement("Element", 1),
    new XElement("Element", 2),
    new XElement("Element", 3),
    new XElement("Element", 4),
    new XElement("Element", 5)
);
XElement xmlTree = new XElement("Root",
    new XElement("Child", 1),
    new XElement("Child", 2),
    from el in srcTree.Elements()
    where (int)el > 2
    select el
);
Console.WriteLine(xmlTree);
```

```vb
Dim srcTree As XElement = _
    <Root>
        <Element>1</Element>
        <Element>2</Element>
        <Element>3</Element>
        <Element>4</Element>
        <Element>5</Element>
    </Root>
Dim xmlTree As XElement = _
    <Root>
        <Child>1</Child>
        <Child>2</Child>
        <%= From el In srcTree.Elements() _
            Where el.Value > 2 _
            Select el %>
    </Root>
Console.WriteLine(xmlTree)
```

這個範例會產生下列輸出：

```xml
<Root>
  <Child>1</Child>
  <Child>2</Child>
  <Element>3</Element>
  <Element>4</Element>
  <Element>5</Element>
</Root>
```

## <a name="serialize-xml-trees"></a>序列化 XML 樹狀結構

您可以將 XML 樹狀結構序列化至 <xref:System.IO.File>、<xref:System.IO.TextWriter> 或 <xref:System.Xml.XmlWriter>。

如需詳細資訊，請參閱 [序列化 XML 樹狀](preserve-white-space-serializing.md)結構。

## <a name="retrieve-xml-data-via-axis-methods"></a>透過軸方法取得 XML 資料

您可以使用座標軸方法來擷取屬性、子項目、子系項目以及祖系項目。 LINQ to XML 的查詢會在座標軸方法上操作，並提供數個具彈性且功能強大的方式來流覽和處理 XML 樹狀結構。

如需詳細資訊，請參閱 [LINQ to XML 軸總覽](linq-xml-axes-overview.md)。

## <a name="query-xml-trees"></a>查詢 XML 樹狀結構

您可以撰寫從 XML 樹狀結構中解壓縮資料的 LINQ to XML 查詢。

如需詳細資訊，請參閱 [查詢 XML 樹狀結構總覽](query-xml-trees-overview.md)。

## <a name="modify-xml-trees"></a>修改 XML 樹狀結構

您可以用不同的方式修改元素，包括變更其內容或屬性。 您也可以從其父代移除項目。

如需詳細資訊，請參閱 [修改 XML 樹狀](in-memory-xml-tree-modification-vs-functional-construction.md)結構。

## <a name="see-also"></a>另請參閱

- [LINQ to XML 程式設計總覽](functional-vs-procedural-programming.md)
