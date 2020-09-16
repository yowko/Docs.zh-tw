---
title: 如何尋找具有特定名稱的同級屬性-LINQ to XML
description: 瞭解如何尋找具有特定名稱的每個屬性，且該屬性也屬於內容節點的同級。 顯示兩種方法：一個使用 XPathEvaluate，另一個使用 LINQ to XML 查詢。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: c3133d64-523f-422d-8838-73d36b945ca0
ms.openlocfilehash: 869c63f26c14bedc8d9911915b8974aa530685fa
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557132"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-linq-to-xml"></a>如何尋找具有特定名稱的同級屬性 (LINQ to XML) 

本文說明如何使用 <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> 來尋找每個具有特定名稱的屬性，且該屬性也屬於內容節點的同級。 本文也會示範如何使用 LINQ to XML 查詢來執行相同的動作。

## <a name="example-find-all-sibling-elements-named-book-and-then-find-all-attributes-named-id"></a>範例：尋找所有名為的同級元素 `Book` ，然後尋找名為 `id`

此範例會 `Book` 在 xml [檔範例 xml 檔：書籍](sample-xml-file-books.md)中尋找元素。 然後，它會尋找名為 `Book` 的所有同一個專案，以及這些專案命名的所有屬性 `id` 。 結果為屬性的集合。

XPath 運算式為 `../Book/@id`。

```csharp
XDocument books = XDocument.Load("Books.xml");

XElement book =
    books
    .Root
    .Element("Book");

// LINQ to XML query
IEnumerable<XAttribute> list1 =
    from el in book.Parent.Elements("Book")
    select el.Attribute("id");

// XPath expression
IEnumerable<XAttribute> list2 =
  ((IEnumerable)book.XPathEvaluate("../Book/@id")).Cast<XAttribute>();

if (list1.Count() == list2.Count() &&
        list1.Intersect(list2).Count() == list1.Count())
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
foreach (XAttribute el in list1)
    Console.WriteLine(el);
```

```vb
Dim books as XDocument = XDocument.Load("Books.xml")
Dim book As XElement = books.Root.<Book>(0)

' LINQ to XML query
Dim list1 As IEnumerable(Of XAttribute) = _
    From el In book.Parent.<Book> _
    Select el.Attribute("id")

' XPath expression
Dim list2 As IEnumerable(Of XAttribute) = DirectCast(book. _
    XPathEvaluate("../Book/@id"), IEnumerable).Cast(Of XAttribute)()

If list1.Count() = list2.Count() And _
        (list1.Intersect(list2)).Count() = list1.Count() Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If

For Each el As XAttribute In list1
    Console.WriteLine(el)
Next
```

這個範例會產生下列輸出：

```output
Results are identical
id="bk101"
id="bk102"
```

## <a name="see-also"></a>另請參閱

- [XPath 使用者的 LINQ to XML (Visual Basic) ](./comparison-xpath-linq-xml.md)
