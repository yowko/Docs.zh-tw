---
title: HOW TO：尋找父系的屬性 (XPath-LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: dbef9d89-a5c4-431f-80cc-7a2ebf323f86
ms.openlocfilehash: aa602f6876b014c48a73dea9b2ff42eb953e5c4c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253765"
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-c"></a><span data-ttu-id="5b42b-102">作法：尋找父系的屬性 (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="5b42b-102">How to: Find an Attribute of the Parent (XPath-LINQ to XML) (C#)</span></span>

<span data-ttu-id="5b42b-103">這個主題顯示如何導覽到父項目並尋找其屬性。</span><span class="sxs-lookup"><span data-stu-id="5b42b-103">This topic shows how to navigate to the parent element and find an attribute of it.</span></span>

<span data-ttu-id="5b42b-104">XPath 運算式為：</span><span class="sxs-lookup"><span data-stu-id="5b42b-104">The XPath expression is:</span></span>

`../@id`

## <a name="example"></a><span data-ttu-id="5b42b-105">範例</span><span class="sxs-lookup"><span data-stu-id="5b42b-105">Example</span></span>

<span data-ttu-id="5b42b-106">這個範例會先尋找 `Author` 項目。</span><span class="sxs-lookup"><span data-stu-id="5b42b-106">This example first finds an `Author` element.</span></span> <span data-ttu-id="5b42b-107">接著，它會尋找父項目的 `id` 屬性。</span><span class="sxs-lookup"><span data-stu-id="5b42b-107">It then finds the `id` attribute of the parent element.</span></span>

<span data-ttu-id="5b42b-108">此範例使用下列 XML 文件：[XML 範例檔：書籍 (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="5b42b-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>

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

<span data-ttu-id="5b42b-109">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="5b42b-109">This example produces the following output:</span></span>

```output
Results are identical
id="bk101"
```
