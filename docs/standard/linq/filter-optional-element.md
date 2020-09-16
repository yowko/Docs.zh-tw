---
title: 如何篩選選擇性元素-LINQ to XML
description: 您可以在專案不存在時，以搜尋不會觸發例外狀況的方式，撰寫子項目的搜尋。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: f99e2f93-fca5-403f-8a0c-770761d4905a
ms.openlocfilehash: 0bf4a2f2c1db420492939351795e3b66b9e0b6b7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90547305"
---
# <a name="how-to-filter-on-an-optional-element-linq-to-xml"></a>如何篩選 (LINQ to XML) 的選擇性元素

有時候您會想要篩選項目，即使您不確定它是否存在於 XML 檔中也是一樣。 您可以撰寫搜尋，如此一來，即使特定元素沒有子專案，您也不會藉由篩選來觸發 null 參考例外狀況。

## <a name="example-search-that-doesnt-trigger-an-exception-when-the-target-element-doesnt-exist"></a>範例：當目標元素不存在時，不會觸發例外狀況的搜尋

在下列範例中，專案 `Child5` 沒有 `Type` 子專案，但是查詢仍會正確執行。 此範例使用 <xref:System.Xml.Linq.Extensions.Elements%2A> 擴充方法。

```csharp
XElement root = XElement.Parse(@"<Root>
  <Child1>
    <Text>Child One Text</Text>
    <Type Value=""Yes""/>
  </Child1>
  <Child2>
    <Text>Child Two Text</Text>
    <Type Value=""Yes""/>
  </Child2>
  <Child3>
    <Text>Child Three Text</Text>
    <Type Value=""No""/>
  </Child3>
  <Child4>
    <Text>Child Four Text</Text>
    <Type Value=""Yes""/>
  </Child4>
  <Child5>
    <Text>Child Five Text</Text>
  </Child5>
</Root>");
var cList =
    from typeElement in root.Elements().Elements("Type")
    where (string)typeElement.Attribute("Value") == "Yes"
    select (string)typeElement.Parent.Element("Text");
foreach(string str in cList)
    Console.WriteLine(str);
```

```vb
Dim root As XElement = _
    <Root>
        <Child1>
            <Text>Child One Text</Text>
            <Type Value="Yes"/>
        </Child1>
        <Child2>
            <Text>Child Two Text</Text>
            <Type Value="Yes"/>
        </Child2>
        <Child3>
            <Text>Child Three Text</Text>
            <Type Value="No"/>
        </Child3>
        <Child4>
            <Text>Child Four Text</Text>
            <Type Value="Yes"/>
        </Child4>
        <Child5>
            <Text>Child Five Text</Text>
        </Child5>
    </Root>
Dim cList As IEnumerable(Of String) = _
    From typeElement In root.Elements().<Type> _
    Where typeElement.@Value = "Yes" _
    Select typeElement.Parent.<Text>.Value
Dim str As String
For Each str In cList
    Console.WriteLine(str)
Next
```

這個範例會產生下列輸出：

```output
Child One Text
Child Two Text
Child Four Text
```

## <a name="example-same-search-but-for-xml-in-a-namespace"></a>範例：相同的搜尋，但命名空間中的 XML

下列範例是與命名空間中的 XML 相同的查詢。 如需詳細資訊，請參閱 [命名空間總覽](namespaces-overview.md)。

```csharp
XElement root = XElement.Parse(@"<Root xmlns='http://www.adatum.com'>
  <Child1>
    <Text>Child One Text</Text>
    <Type Value=""Yes""/>
  </Child1>
  <Child2>
    <Text>Child Two Text</Text>
    <Type Value=""Yes""/>
  </Child2>
  <Child3>
    <Text>Child Three Text</Text>
    <Type Value=""No""/>
  </Child3>
  <Child4>
    <Text>Child Four Text</Text>
    <Type Value=""Yes""/>
  </Child4>
  <Child5>
    <Text>Child Five Text</Text>
  </Child5>
</Root>");
XNamespace ad = "http://www.adatum.com";
var cList =
    from typeElement in root.Elements().Elements(ad + "Type")
    where (string)typeElement.Attribute("Value") == "Yes"
    select (string)typeElement.Parent.Element(ad + "Text");
foreach (string str in cList)
    Console.WriteLine(str);
```

```vb
Imports <xmlns='http://www.adatum.com'>

Module Module1
    Sub Main()
        Dim root As XElement = _
            <Root>
                <Child1>
                    <Text>Child One Text</Text>
                    <Type Value="Yes"/>
                </Child1>
                <Child2>
                    <Text>Child Two Text</Text>
                    <Type Value="Yes"/>
                </Child2>
                <Child3>
                    <Text>Child Three Text</Text>
                    <Type Value="No"/>
                </Child3>
                <Child4>
                    <Text>Child Four Text</Text>
                    <Type Value="Yes"/>
                </Child4>
                <Child5>
                    <Text>Child Five Text</Text>
                </Child5>
            </Root>
        Dim cList As IEnumerable(Of String) = _
            From typeElement In root.Elements().<Type> _
            Where typeElement.@Value = "Yes" _
            Select typeElement.Parent.<Text>.Value
        Dim str As String
        For Each str In cList
            Console.WriteLine(str)
        Next
    End Sub
End Module
```

這個範例會產生下列輸出：

```output
Child One Text
Child Two Text
Child Four Text
```

## <a name="see-also"></a>另請參閱

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType>
- [標準查詢運算子概觀 (C#)](../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [投射作業 (C#)](../../csharp/programming-guide/concepts/linq/projection-operations.md)
- [基本查詢 (LINQ to XML)  (Visual Basic) ](./find-element-specific-attribute.md)
- [XML 子代軸屬性 (Visual Basic)](../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [XML 屬性軸屬性 (Visual Basic)](../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
- [XML 值屬性](../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [標準查詢運算子概觀 (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [投影作業 (Visual Basic) ](../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
