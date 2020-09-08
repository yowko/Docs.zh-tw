---
title: 如何尋找同級節點-LINQ to XML
description: 瞭解如何尋找具有特定名稱之節點的所有同級。 顯示兩種方法：一個使用 System.xml.xpath.extensions.xpathselectelements，另一個使用 LINQ to XML 查詢。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: e2c73d10-a8ca-4e11-b5aa-d055de285874
ms.openlocfilehash: 3c764cec818cf788282bb616cc123e9be8d62c08
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552183"
---
# <a name="how-to-find-sibling-nodes-linq-to-xml"></a>如何尋找 (LINQ to XML) 的同級節點

本文說明如何使用 <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> 來尋找具有特定名稱之節點的所有同級，以及如何使用 LINQ to XML 查詢來執行相同的動作。

> [!NOTE]
> 如果所產生的集合也有特定的名稱，則會包含內容節點。

## <a name="example-find-an-element-named-book-and-all-sibling-elements-named-book"></a>範例：尋找名為的元素 `Book` ，以及名為 `Book`

此範例會先尋找 `Book` xml 檔中的專案 [範例 xml 檔：書籍](sample-xml-file-books.md)，然後尋找名為的所有同一個元素 `Book` 。 所產生的集合包含內容節點。

XPath 運算式為 `../Book`

```csharp
XDocument books = XDocument.Load("Books.xml");

XElement book =
    books
    .Root
    .Elements("Book")
    .Skip(1)
    .First();

// LINQ to XML query
IEnumerable<XElement> list1 =
    book
    .Parent
    .Elements("Book");

// XPath expression
IEnumerable<XElement> list2 = book.XPathSelectElements("../Book");

if (list1.Count() == list2.Count() &&
        list1.Intersect(list2).Count() == list1.Count())
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
foreach (XElement el in list1)
    Console.WriteLine(el);
```

```vb
Dim books As XDocument = XDocument.Load("Books.xml")
Dim book As XElement = books.Root.<Book>.Skip(1).First()

' LINQ to XML query
Dim list1 As IEnumerable(Of XElement) = book.Parent.<Book>

' XPath expression
Dim list2 As IEnumerable(Of XElement) = book.XPathSelectElements("../Book")

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
<Book id="bk101">
  <Author>Garghentini, Davide</Author>
  <Title>XML Developer's Guide</Title>
  <Genre>Computer</Genre>
  <Price>44.95</Price>
  <PublishDate>2000-10-01</PublishDate>
  <Description>An in-depth look at creating applications
      with XML.</Description>
</Book>
<Book id="bk102">
  <Author>Garcia, Debra</Author>
  <Title>Midnight Rain</Title>
  <Genre>Fantasy</Genre>
  <Price>5.95</Price>
  <PublishDate>2000-12-16</PublishDate>
  <Description>A former architect battles corporate zombies,
      an evil sorceress, and her own childhood to become queen
      of the world.</Description>
</Book>
```

## <a name="see-also"></a>另請參閱

- [XPath 使用者的 LINQ to XML (Visual Basic) ](../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
