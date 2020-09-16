---
title: 如何尋找具有特定屬性的元素-LINQ to XML
description: 瞭解如何尋找具有特定屬性 (的所有元素，不論) 值為何。 顯示兩種方法：一個使用 XPathEvaluate，另一個使用 LINQ to XML 查詢。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: daed00dd-923a-43be-8a90-eee406f6f574
ms.openlocfilehash: 2a747e7609e2b130249a7635d8448577d035f939
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90545646"
---
# <a name="how-to-find-elements-with-a-specific-attribute-linq-to-xml"></a><span data-ttu-id="9f40f-104">如何尋找具有特定屬性 (LINQ to XML) 的元素</span><span class="sxs-lookup"><span data-stu-id="9f40f-104">How to find elements with a specific attribute (LINQ to XML)</span></span>

<span data-ttu-id="9f40f-105">本文說明如何使用 <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> 來尋找具有特定屬性的所有專案 (無論) 的值為何，以及如何使用 LINQ to XML 查詢來執行相同的動作。</span><span class="sxs-lookup"><span data-stu-id="9f40f-105">This article shows how to use <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> to find all elements that have a specific attribute (regardless of value), and how to use LINQ to XML query to do the same thing.</span></span>

## <a name="example-find-all-elements-that-have-the-select-attribute"></a><span data-ttu-id="9f40f-106">範例：尋找所有具有屬性的元素 `Select`</span><span class="sxs-lookup"><span data-stu-id="9f40f-106">Example: Find all elements that have the `Select` attribute</span></span>

<span data-ttu-id="9f40f-107">下列範例會建立 XML 樹狀結構，然後尋找具有該屬性的元素 `Select` 。</span><span class="sxs-lookup"><span data-stu-id="9f40f-107">The following example creates an XML tree and then finds the elements that have the `Select` attribute.</span></span>

<span data-ttu-id="9f40f-108">XPath 運算式為 `./*[@Select]`。</span><span class="sxs-lookup"><span data-stu-id="9f40f-108">The XPath expression is `./*[@Select]`.</span></span>

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

<span data-ttu-id="9f40f-109">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="9f40f-109">This example produces the following output:</span></span>

```output
Results are identical
<Child2 Select="true">2</Child2>
<Child4 Select="true">4</Child4>
```

## <a name="see-also"></a><span data-ttu-id="9f40f-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f40f-110">See also</span></span>

- [<span data-ttu-id="9f40f-111">XPath 使用者的 LINQ to XML (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="9f40f-111">LINQ to XML for XPath Users (Visual Basic)</span></span>](./comparison-xpath-linq-xml.md)
