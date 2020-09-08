---
title: 如何尋找具有特定屬性的元素-LINQ to XML
description: 瞭解如何尋找具有特定屬性 (的所有元素，不論) 值為何。 顯示兩種方法：一個使用 XPathEvaluate，另一個使用 LINQ to XML 查詢。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: daed00dd-923a-43be-8a90-eee406f6f574
ms.openlocfilehash: fc9f5acdda457eea1790f76695a71afe5fefa070
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552085"
---
# <a name="how-to-find-elements-with-a-specific-attribute-linq-to-xml"></a>如何尋找具有特定屬性 (LINQ to XML) 的元素

本文說明如何使用 <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> 來尋找具有特定屬性的所有專案 (無論) 的值為何，以及如何使用 LINQ to XML 查詢來執行相同的動作。

## <a name="example-find-all-elements-that-have-the-select-attribute"></a>範例：尋找所有具有屬性的元素 `Select`

下列範例會建立 XML 樹狀結構，然後尋找具有該屬性的元素 `Select` 。

XPath 運算式為 `./*[@Select]`。

```csharp
XElement doc = XElement.Parse(
@"<Root>
    <Child1>1</Child1>
    <Child2 Select='true'>2</Child2>
    <Child3>3</Child3>
    <Child4 Select='true'>4</Child4>
    <Child5>5</Child5>
</Root>");

// LINQ to XML query
IEnumerable<XElement> list1 =
    from el in doc.Elements()
    where el.Attribute("Select") != null
    select el;

// XPath expression
IEnumerable<XElement> list2 =
    ((IEnumerable)doc.XPathEvaluate("./*[@Select]")).Cast<XElement>();

if (list1.Count() == list2.Count() &&
        list1.Intersect(list2).Count() == list1.Count())
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
foreach (XElement el in list1)
    Console.WriteLine(el);
```

```vb
Dim doc As XElement = _
    <Root>
        <Child1>1</Child1>
        <Child2 Select='true'>2</Child2>
        <Child3>3</Child3>
        <Child4 Select='true'>4</Child4>
        <Child5>5</Child5>
    </Root>

' LINQ to XML query
Dim list1 As IEnumerable(Of XElement) = _
    From el In doc.Elements() _
    Where el.@Select <> Nothing _
    Select el

' XPath expression
Dim list2 As IEnumerable(Of XElement) = DirectCast(doc.XPathEvaluate _
    ("./*[@Select]"), IEnumerable).Cast(Of XElement)()

If list1.Count() = list2.Count() And _
    list1.Intersect(list2).Count() = list1.Count() Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If

For Each el As XElement In list1
    Console.WriteLine(el)
Next
```

這個範例會產生下列輸出：

```output
Results are identical
<Child2 Select="true">2</Child2>
<Child4 Select="true">4</Child4>
```

## <a name="see-also"></a>另請參閱

- [XPath 使用者的 LINQ to XML (Visual Basic) ](../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
