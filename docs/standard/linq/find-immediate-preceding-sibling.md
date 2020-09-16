---
title: 如何尋找緊接在前面的同級 LINQ to XML
description: 瞭解如何尋找緊接在節點之前的同級。 顯示兩種方法：一個使用 XPathEvaluate，另一個使用 LINQ to XML 查詢。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 74c06201-0b1b-4b5e-b3ac-0092980614e6
ms.openlocfilehash: 9be39c20a99920482899efa934003957ffc696b7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90545612"
---
# <a name="how-to-find-the-immediate-preceding-sibling-linq-to-xml"></a>如何尋找立即的先前的同級 (LINQ to XML) 

本文說明如何使用找出 <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> 緊接在節點之前的同級，以及如何使用 LINQ to XML 查詢來執行相同的動作。 由於 XPath 中先前同級軸的位置述詞之語義差異差異，而不是 LINQ to XML，這是比較有趣的比較。

## <a name="example-find-the-next-to-last-element"></a>範例：尋找最後一個元素的旁邊

在此範例中，LINQ to XML 查詢會使用 <xref:System.Linq.Enumerable.Last%2A> 運算子來尋找所傳回之集合中的最後一個節點 <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A> 。 相較之下，XPath 運算式會使用述詞搭配 1 這個值來尋找正前面的項目。

```csharp
XElement root = XElement.Parse(
    @"<Root>
    <Child1/>
    <Child2/>
    <Child3/>
    <Child4/>
</Root>");
XElement child4 = root.Element("Child4");

// LINQ to XML query
XElement el1 =
    child4
    .ElementsBeforeSelf()
    .Last();

// XPath expression
XElement el2 =
    ((IEnumerable)child4
                 .XPathEvaluate("preceding-sibling::*[1]"))
                 .Cast<XElement>()
                 .First();

if (el1 == el2)
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
Console.WriteLine(el1);
```

```vb
Dim root As XElement = _
    <Root>
        <Child1/>
        <Child2/>
        <Child3/>
        <Child4/>
    </Root>
Dim child4 As XElement = root.Element("Child4")

' LINQ to XML query
Dim el1 As XElement = child4.ElementsBeforeSelf().Last()

' XPath expression
Dim el2 As XElement = _
    DirectCast(child4.XPathEvaluate("preceding-sibling::*[1]"),  _
    IEnumerable).Cast(Of XElement)().First()

If el1 Is el2 Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If
Console.WriteLine(el1)
```

這個範例會產生下列輸出：

```output
Results are identical
<Child3 />
```

## <a name="see-also"></a>另請參閱

- [XPath 使用者的 LINQ to XML (Visual Basic) ](./comparison-xpath-linq-xml.md)
