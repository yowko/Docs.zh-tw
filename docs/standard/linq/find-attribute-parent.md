---
title: 如何尋找父系 LINQ to XML 的屬性
description: 瞭解如何流覽至元素，並尋找其父系的屬性。 顯示兩種方法：一個使用 XPathEvaluate，另一個使用 LINQ to XML 查詢。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: dbef9d89-a5c4-431f-80cc-7a2ebf323f86
ms.openlocfilehash: 811766ecfdf2f080f29f21ae08981483f75a7e44
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552841"
---
# <a name="how-to-find-an-attribute-of-the-parent-linq-to-xml"></a><span data-ttu-id="f5dc6-104">如何尋找父 (LINQ to XML 的屬性) </span><span class="sxs-lookup"><span data-stu-id="f5dc6-104">How to find an attribute of the parent (LINQ to XML)</span></span>

<span data-ttu-id="f5dc6-105">本文說明如何使用 <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> 來尋找父元素的屬性，以及如何使用 LINQ to XML 查詢來執行相同的動作。</span><span class="sxs-lookup"><span data-stu-id="f5dc6-105">This article shows how to use <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> to find an attribute of a parent element, and how to use LINQ to XML query to do the same thing.</span></span>

## <a name="example-find-the-author-element-and-then-find-the-id-attribute-of-its-parent"></a><span data-ttu-id="f5dc6-106">範例：尋找 `Author` 元素，然後尋找 `id` 其父系的屬性</span><span class="sxs-lookup"><span data-stu-id="f5dc6-106">Example: Find the `Author` element, and then find the `id` attribute of its parent</span></span>

<span data-ttu-id="f5dc6-107">這個範例會先尋找 `Author` xml [檔範例 xml 檔：書籍](sample-xml-file-books.md)中的元素，然後尋找 `id` 其父元素的屬性。</span><span class="sxs-lookup"><span data-stu-id="f5dc6-107">This example first finds an `Author` element in XML document [Sample XML file: Books](sample-xml-file-books.md), and then finds the `id` attribute of its parent element.</span></span>

<span data-ttu-id="f5dc6-108">XPath 運算式為 `../@id`。</span><span class="sxs-lookup"><span data-stu-id="f5dc6-108">The XPath expression is `../@id`.</span></span>

```csharp
XDocument books = XDocument.Load("Books.xml");

XElement author =
    books
    .Root
    .Element("Book")
    .Element("Author");

// LINQ to XML query
XAttribute att1 =
    author
    .Parent
    .Attribute("id");

// XPath expression
XAttribute att2 = ((IEnumerable)author.XPathEvaluate("../@id")).Cast<XAttribute>().First();

if (att1 == att2)
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
Console.WriteLine(att1);
```

```vb
Dim books As XDocument = XDocument.Load("Books.xml")
Dim author As XElement = books.Root.<Book>.<Author>.FirstOrDefault()

' LINQ to XML query
Dim att1 As XAttribute = author.Parent.Attribute("id")

' XPath expression
Dim att2 As XAttribute = DirectCast(author.XPathEvaluate("../@id"),  _
    IEnumerable).Cast(Of XAttribute)().First()

If att1 Is att2 Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If
Console.WriteLine(att1)
```

<span data-ttu-id="f5dc6-109">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="f5dc6-109">This example produces the following output:</span></span>

```output
Results are identical
id="bk101"
```

## <a name="see-also"></a><span data-ttu-id="f5dc6-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5dc6-110">See also</span></span>

- [<span data-ttu-id="f5dc6-111">XPath 使用者的 LINQ to XML (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="f5dc6-111">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
