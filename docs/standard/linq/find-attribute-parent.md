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
# <a name="how-to-find-an-attribute-of-the-parent-linq-to-xml"></a>如何尋找父 (LINQ to XML 的屬性) 

本文說明如何使用 <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> 來尋找父元素的屬性，以及如何使用 LINQ to XML 查詢來執行相同的動作。

## <a name="example-find-the-author-element-and-then-find-the-id-attribute-of-its-parent"></a>範例：尋找 `Author` 元素，然後尋找 `id` 其父系的屬性

這個範例會先尋找 `Author` xml [檔範例 xml 檔：書籍](sample-xml-file-books.md)中的元素，然後尋找 `id` 其父元素的屬性。

XPath 運算式為 `../@id`。

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

這個範例會產生下列輸出：

```output
Results are identical
id="bk101"
```

## <a name="see-also"></a>另請參閱

- [XPath 使用者的 LINQ to XML (Visual Basic) ](../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
