---
title: 如何從檔案載入 XML-LINQ to XML
description: '您可以使用 c # 和 Visual Basic 中的 System.xml.linq.xelement> 載入方法，從檔案載入 XML 檔。'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 3ed38487-8028-4209-9872-c8dce0ed4dfe
ms.openlocfilehash: 7ac77205eb1f7637982e8f40d31df0a422ecba22
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552223"
---
# <a name="how-to-load-xml-from-a-file-linq-to-xml"></a><span data-ttu-id="7555b-103">如何從檔案載入 XML (LINQ to XML) </span><span class="sxs-lookup"><span data-stu-id="7555b-103">How to load XML from a file (LINQ to XML)</span></span>

<span data-ttu-id="7555b-104">本文說明如何使用方法，以 c # 和 Visual Basic 從檔案載入 XML <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="7555b-104">This article shows how to load XML from a file in C# and Visual Basic using the <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> method.</span></span>

## <a name="example-load-xml-document-from-a-file"></a><span data-ttu-id="7555b-105">範例：從檔案載入 XML 檔</span><span class="sxs-lookup"><span data-stu-id="7555b-105">Example: Load XML document from a file</span></span>

<span data-ttu-id="7555b-106">下列範例示範如何藉由提供 <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> 參考檔案的 URI，從檔案載入 XML 檔。</span><span class="sxs-lookup"><span data-stu-id="7555b-106">The following example shows how to load an XML document from a file by providing <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> with the URI that references the file.</span></span> <span data-ttu-id="7555b-107">此範例會載入 books.xml，並將 XML 樹狀結構輸出到主控台。</span><span class="sxs-lookup"><span data-stu-id="7555b-107">The example loads books.xml and outputs the XML tree to the console.</span></span>

<span data-ttu-id="7555b-108">books.xml 的內容會顯示在 [範例 XML 檔：書籍](sample-xml-file-books.md)中。</span><span class="sxs-lookup"><span data-stu-id="7555b-108">The contents of books.xml are shown in [Sample XML file: Books](sample-xml-file-books.md).</span></span>

```csharp
XElement booksFromFile = XElement.Load(@"books.xml");
Console.WriteLine(booksFromFile);
```

```vb
Dim booksFromFile As XElement = XElement.Load("books.xml")
Console.WriteLine(booksFromFile)
```

<span data-ttu-id="7555b-109">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="7555b-109">This example produces the following output:</span></span>

```xml
<Catalog>
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
</Catalog>
```
