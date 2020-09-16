---
title: 如何尋找子專案的子代-LINQ to XML
description: 瞭解如何尋找子專案的子系或子項目的序列。 顯示兩種方法：一個使用 XPathEvaluate，另一個使用 LINQ to XML 查詢。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 505b7512-bb8b-4f85-abbf-491f039c961e
ms.openlocfilehash: 2ac023ddc797f27f5f00eaf86ff6357096f333c8
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559312"
---
# <a name="how-to-find-descendants-of-a-child-element-linq-to-xml"></a><span data-ttu-id="334f4-104">如何尋找子專案的子代 (LINQ to XML) </span><span class="sxs-lookup"><span data-stu-id="334f4-104">How to find descendants of a child element (LINQ to XML)</span></span>

<span data-ttu-id="334f4-105">本文說明如何使用 <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> 來尋找子專案序列的下階元素，以及如何使用 LINQ to XML 查詢來尋找相同的專案。</span><span class="sxs-lookup"><span data-stu-id="334f4-105">This article shows how to use <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> to find the descendant elements of a sequence of child elements, and how to use LINQ to XML query to find the same elements.</span></span>

## <a name="example-find-all-the-text-descendant-elements-of-all-the-paragraph-elements"></a><span data-ttu-id="334f4-106">範例：尋找 `Text` 所有元素的所有子代元素 `Paragraph`</span><span class="sxs-lookup"><span data-stu-id="334f4-106">Example: Find all the `Text` descendant elements of all the `Paragraph` elements</span></span>

<span data-ttu-id="334f4-107">此範例會從簡單的文字處理檔的 XML 標記法解壓縮文字。</span><span class="sxs-lookup"><span data-stu-id="334f4-107">This example extracts text from an XML representation of a simple word processing document.</span></span> <span data-ttu-id="334f4-108">它會先選取所有 `Paragraph` 元素，忽略 `Comment` 元素，然後選取每個專案的所有 `Text` 子代元素 `Paragraph` 。</span><span class="sxs-lookup"><span data-stu-id="334f4-108">It first selects all `Paragraph` elements, ignoring the `Comment` element, and then it selects all the `Text` descendant elements of each `Paragraph` element.</span></span> <span data-ttu-id="334f4-109">它會以兩種方式執行這項工作：使用 <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> 和搭配 LINQ to XML 查詢。</span><span class="sxs-lookup"><span data-stu-id="334f4-109">It does this task in two ways: with <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> and with LINQ to XML query.</span></span> <span data-ttu-id="334f4-110">然後，它會比較結果並尋找相同的結果。</span><span class="sxs-lookup"><span data-stu-id="334f4-110">It then compares the results and finds them identical.</span></span>

<span data-ttu-id="334f4-111">XPath 運算式為  `./Paragraph//Text/text()` 。</span><span class="sxs-lookup"><span data-stu-id="334f4-111">The XPath expression is  `./Paragraph//Text/text()`.</span></span>

```csharp
XElement root = XElement.Parse(
@"<Root>
  <Paragraph>
    <Text>This is the start of</Text>
  </Paragraph>
  <Comment>
    <Text>This comment isn't part of the paragraph text.</Text>
  </Comment>
  <Paragraph>
    <Annotation Emphasis='true'>
      <Text> a sentence.</Text>
    </Annotation>
  </Paragraph>
  <Paragraph>
    <Text>  This is the second sentence.</Text>
  </Paragraph>
</Root>");

// LINQ to XML query
string str1 =
    root
    .Elements("Paragraph")
    .Descendants("Text")
    .Select(s => s.Value)
    .Aggregate(
        new StringBuilder(),
        (s, i) => s.Append(i),
        s => s.ToString()
    );

// XPath expression
string str2 =
    ((IEnumerable)root.XPathEvaluate("./Paragraph//Text/text()"))
    .Cast<XText>()
    .Select(s => s.Value)
    .Aggregate(
        new StringBuilder(),
        (s, i) => s.Append(i),
        s => s.ToString()
    );

if (str1 == str2)
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
Console.WriteLine(str2);
```

```vb
Dim root As XElement = _
    <Root>
        <Paragraph>
            <Text>This is the start of</Text>
        </Paragraph>
        <Comment>
            <Text>This comment isn't part of the paragraph text.</Text>
        </Comment>
        <Paragraph>
            <Annotation Emphasis='true'>
                <Text> a sentence.</Text>
            </Annotation>
        </Paragraph>
        <Paragraph>
            <Text>This is the second sentence.</Text>
        </Paragraph>
    </Root>

' LINQ to XML query
Dim str1 As String = _
    root.<Paragraph>...<Text>.Select(Function(ByVal s) s.Value). _
    Aggregate( _
        New StringBuilder(), _
        Function(ByVal s, ByVal i) s.Append(i), _
        Function(ByVal s) s.ToString())

' XPath expression
Dim str2 As String = DirectCast(root.XPathEvaluate("./Paragraph//Text/text()"), IEnumerable) _
    .Cast(Of XText)().Select(Function(ByVal s) s.Value) _
    .Aggregate( _
        New StringBuilder(), _
        Function(ByVal s, ByVal i) s.Append(i), _
        Function(ByVal s) s.ToString())

If str1 = str2 Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If
Console.WriteLine(str2)
```

<span data-ttu-id="334f4-112">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="334f4-112">This example produces the following output:</span></span>

```output
Results are identical
This is the start of a sentence.  This is the second sentence.
```

## <a name="see-also"></a><span data-ttu-id="334f4-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="334f4-113">See also</span></span>

- [<span data-ttu-id="334f4-114">XPath 使用者的 LINQ to XML (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="334f4-114">LINQ to XML for XPath Users (Visual Basic)</span></span>](./comparison-xpath-linq-xml.md)
