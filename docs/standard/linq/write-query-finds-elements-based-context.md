---
title: 如何撰寫可根據內容 LINQ to XML 尋找元素的查詢
description: 撰寫可根據內容選取元素的查詢;例如，根據先前或後面的同級元素來篩選結果。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 3ff79ef0-fc8b-42fe-8cc0-10dc32b06b4e
ms.openlocfilehash: 2c51a790a2a8adef565f186992a6a3faa5f102ad
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550457"
---
# <a name="how-to-write-a-query-that-finds-elements-based-on-context-linq-to-xml"></a>如何撰寫可根據內容 (LINQ to XML 尋找元素的查詢) 

有時候您可能必須撰寫會依其內容選取項目的查詢。 例如，您可能想要根據先前或之後的同級元素，或在子系或上階元素進行篩選。

您僅能撰寫查詢並使用 `where` 子句中的查詢結果來達到這個目的。 如果您必須先針對 null 進行測試，然後再測試值，在子句中執行查詢比較方便，然後在 `let` 子句中使用結果 `where` 。

## <a name="example-select-p-elements-that-are-immediately-followed-by-a-ul-element"></a>範例：選取 `p` 緊接在元素後面的元素 `ul`

下列範例會選取緊跟著 `p` 項目後面的所有 `ul` 項目。

```csharp
XElement doc = XElement.Parse(@"<Root>
    <p id=""1""/>
    <ul>abc</ul>
    <Child>
        <p id=""2""/>
        <notul/>
        <p id=""3""/>
        <ul>def</ul>
        <p id=""4""/>
    </Child>
    <Child>
        <p id=""5""/>
        <notul/>
        <p id=""6""/>
        <ul>abc</ul>
        <p id=""7""/>
    </Child>
</Root>");

IEnumerable<XElement> items =
    from e in doc.Descendants("p")
    let z = e.ElementsAfterSelf().FirstOrDefault()
    where z != null && z.Name.LocalName == "ul"
    select e;

foreach (XElement e in items)
    Console.WriteLine("id = {0}", (string)e.Attribute("id"));
```

```vb
Dim doc As XElement = _
    <Root>
        <p id='1'/>
        <ul>abc</ul>
        <Child>
            <p id='2'/>
            <notul/>
            <p id='3'/>
            <ul>def</ul>
            <p id='4'/>
        </Child>
        <Child>
            <p id='5'/>
            <notul/>
            <p id='6'/>
            <ul>abc</ul>
            <p id='7'/>
        </Child>
    </Root>

Dim items As IEnumerable(Of XElement) = _
    From e In doc...<p> _
    Let z = e.ElementsAfterSelf().FirstOrDefault() _
    Where z IsNot Nothing AndAlso z.Name.LocalName = "ul" _
    Select e

For Each e As XElement In items
    Console.WriteLine("id = {0}", e.@<id>)
Next
```

這個範例會產生下列輸出：

```output
id = 1
id = 3
id = 6
```

## <a name="example-in-a-namespace-select-p-elements-that-are-immediately-followed-by-a-ul-element"></a>範例：在命名空間中 `p` ，選取緊接在元素後面的 `ul` 元素

下列範例顯示與上述相同的查詢，但針對命名空間中的 XML。 如需詳細資訊，請參閱 [命名空間總覽](namespaces-overview.md)。

```csharp
XElement doc = XElement.Parse(@"<Root xmlns='http://www.adatum.com'>
    <p id=""1""/>
    <ul>abc</ul>
    <Child>
        <p id=""2""/>
        <notul/>
        <p id=""3""/>
        <ul>def</ul>
        <p id=""4""/>
    </Child>
    <Child>
        <p id=""5""/>
        <notul/>
        <p id=""6""/>
        <ul>abc</ul>
        <p id=""7""/>
    </Child>
</Root>");

XNamespace ad = "http://www.adatum.com";

IEnumerable<XElement> items =
    from e in doc.Descendants(ad + "p")
    let z = e.ElementsAfterSelf().FirstOrDefault()
    where z != null && z.Name == ad.GetName("ul")
    select e;

foreach (XElement e in items)
    Console.WriteLine("id = {0}", (string)e.Attribute("id"));
```

```vb
Imports <xmlns='http://www.adatum.com'>

Module Module1
    Sub Main()
        Dim doc As XElement = _
            <Root>
                <p id='1'/>
                <ul>abc</ul>
                <Child>
                    <p id='2'/>
                    <notul/>
                    <p id='3'/>
                    <ul>def</ul>
                    <p id='4'/>
                </Child>
                <Child>
                    <p id='5'/>
                    <notul/>
                    <p id='6'/>
                    <ul>abc</ul>
                    <p id='7'/>
                </Child>
            </Root>

        Dim items As IEnumerable(Of XElement) = _
            From e In doc...<p> _
            Let z = e.ElementsAfterSelf().FirstOrDefault() _
            Where z IsNot Nothing AndAlso z.Name = GetXmlNamespace().GetName("ul") _
            Select e

        For Each e As XElement In items
            Console.WriteLine("id = {0}", e.@<id>)
        Next
    End Sub
End Module
```

這個範例會產生下列輸出：

```output
id = 1
id = 3
id = 6
```

## <a name="see-also"></a>另請參閱

- <xref:System.Xml.Linq.XElement.Parse%2A>
- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>
- <xref:System.Linq.Enumerable.FirstOrDefault%2A>
- [基本查詢 (LINQ to XML)  (Visual Basic) ](./find-element-specific-attribute.md)
