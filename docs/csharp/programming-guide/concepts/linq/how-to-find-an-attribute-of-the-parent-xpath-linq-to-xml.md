---
title: '如何尋找父系的屬性（XPath-LINQ to XML）（c #）'
description: 瞭解如何尋找父元素的屬性。 請參閱使用範例 XML 檔的程式碼範例。
ms.date: 07/20/2015
ms.assetid: dbef9d89-a5c4-431f-80cc-7a2ebf323f86
ms.openlocfilehash: 03344bb66f617970d9598c91366eb7d69514397a
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303292"
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-c"></a><span data-ttu-id="37820-104">如何尋找父系的屬性（XPath-LINQ to XML）（c #）</span><span class="sxs-lookup"><span data-stu-id="37820-104">How to find an attribute of the parent (XPath-LINQ to XML) (C#)</span></span>

<span data-ttu-id="37820-105">這個主題顯示如何導覽到父項目並尋找其屬性。</span><span class="sxs-lookup"><span data-stu-id="37820-105">This topic shows how to navigate to the parent element and find an attribute of it.</span></span>

<span data-ttu-id="37820-106">XPath 運算式為：</span><span class="sxs-lookup"><span data-stu-id="37820-106">The XPath expression is:</span></span>

`../@id`

## <a name="example"></a><span data-ttu-id="37820-107">範例</span><span class="sxs-lookup"><span data-stu-id="37820-107">Example</span></span>

<span data-ttu-id="37820-108">這個範例會先尋找 `Author` 項目。</span><span class="sxs-lookup"><span data-stu-id="37820-108">This example first finds an `Author` element.</span></span> <span data-ttu-id="37820-109">接著，它會尋找父項目的 `id` 屬性。</span><span class="sxs-lookup"><span data-stu-id="37820-109">It then finds the `id` attribute of the parent element.</span></span>

<span data-ttu-id="37820-110">此範例使用下列 XML 文件︰[範例 XML 檔：書籍 (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="37820-110">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>

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

<span data-ttu-id="37820-111">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="37820-111">This example produces the following output:</span></span>

```output
Results are identical
id="bk101"
```
