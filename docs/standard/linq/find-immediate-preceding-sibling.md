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
# <a name="how-to-find-the-immediate-preceding-sibling-linq-to-xml"></a><span data-ttu-id="fd529-104">如何尋找立即的先前的同級 (LINQ to XML) </span><span class="sxs-lookup"><span data-stu-id="fd529-104">How to find the immediate preceding sibling (LINQ to XML)</span></span>

<span data-ttu-id="fd529-105">本文說明如何使用找出 <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> 緊接在節點之前的同級，以及如何使用 LINQ to XML 查詢來執行相同的動作。</span><span class="sxs-lookup"><span data-stu-id="fd529-105">This article shows how to use <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> to find the sibling that immediately precedes a node, and how to use LINQ to XML query to do the same thing.</span></span> <span data-ttu-id="fd529-106">由於 XPath 中先前同級軸的位置述詞之語義差異差異，而不是 LINQ to XML，這是比較有趣的比較。</span><span class="sxs-lookup"><span data-stu-id="fd529-106">Due to the difference in the semantics of positional predicates for the preceding sibling axes in XPath as opposed to LINQ to XML, this is one of the more interesting comparisons.</span></span>

## <a name="example-find-the-next-to-last-element"></a><span data-ttu-id="fd529-107">範例：尋找最後一個元素的旁邊</span><span class="sxs-lookup"><span data-stu-id="fd529-107">Example: Find the next to last element</span></span>

<span data-ttu-id="fd529-108">在此範例中，LINQ to XML 查詢會使用 <xref:System.Linq.Enumerable.Last%2A> 運算子來尋找所傳回之集合中的最後一個節點 <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A> 。</span><span class="sxs-lookup"><span data-stu-id="fd529-108">In this example, the LINQ to XML query uses the <xref:System.Linq.Enumerable.Last%2A> operator to find the last node in the collection returned by <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span></span> <span data-ttu-id="fd529-109">相較之下，XPath 運算式會使用述詞搭配 1 這個值來尋找正前面的項目。</span><span class="sxs-lookup"><span data-stu-id="fd529-109">By contrast, the XPath expression uses a predicate with a value of 1 to find the immediately preceding element.</span></span>

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

<span data-ttu-id="fd529-110">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="fd529-110">This example produces the following output:</span></span>

```output
Results are identical
<Child3 />
```

## <a name="see-also"></a><span data-ttu-id="fd529-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd529-111">See also</span></span>

- [<span data-ttu-id="fd529-112">XPath 使用者的 LINQ to XML (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="fd529-112">LINQ to XML for XPath Users (Visual Basic)</span></span>](./comparison-xpath-linq-xml.md)
