---
title: 如何查找父屬性（XPath-LINQ 到 XML）（C#）
ms.date: 07/20/2015
ms.assetid: dbef9d89-a5c4-431f-80cc-7a2ebf323f86
ms.openlocfilehash: bfe7554a5c767adde5e7170c8e1ea0537155f6df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141171"
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-c"></a><span data-ttu-id="e71ce-102">如何查找父屬性（XPath-LINQ 到 XML）（C#）</span><span class="sxs-lookup"><span data-stu-id="e71ce-102">How to find an attribute of the parent (XPath-LINQ to XML) (C#)</span></span>

<span data-ttu-id="e71ce-103">這個主題顯示如何導覽到父項目並尋找其屬性。</span><span class="sxs-lookup"><span data-stu-id="e71ce-103">This topic shows how to navigate to the parent element and find an attribute of it.</span></span>

<span data-ttu-id="e71ce-104">XPath 運算式為：</span><span class="sxs-lookup"><span data-stu-id="e71ce-104">The XPath expression is:</span></span>

`../@id`

## <a name="example"></a><span data-ttu-id="e71ce-105">範例</span><span class="sxs-lookup"><span data-stu-id="e71ce-105">Example</span></span>

<span data-ttu-id="e71ce-106">這個範例會先尋找 `Author` 項目。</span><span class="sxs-lookup"><span data-stu-id="e71ce-106">This example first finds an `Author` element.</span></span> <span data-ttu-id="e71ce-107">接著，它會尋找父項目的 `id` 屬性。</span><span class="sxs-lookup"><span data-stu-id="e71ce-107">It then finds the `id` attribute of the parent element.</span></span>

<span data-ttu-id="e71ce-108">此範例使用下列 XML 文件︰[範例 XML 檔：書籍 (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="e71ce-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>

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

<span data-ttu-id="e71ce-109">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="e71ce-109">This example produces the following output:</span></span>

```output
Results are identical
id="bk101"
```
