---
title: 如何尋找兩個位置路徑的聯集-LINQ to XML
description: 瞭解如何尋找兩個 XPath 位置路徑之結果的聯集。 顯示兩個方法：一個使用 System.xml.xpath.extensions.xpathselectelements，另一個則使用 Concat 標準查詢運算子。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 069622d3-2b58-4919-8903-710a564c0788
ms.openlocfilehash: 13d1a22d933d789f28efa2d196fc0106986caa90
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555004"
---
# <a name="how-to-find-a-union-of-two-location-paths-linq-to-xml"></a><span data-ttu-id="cfacf-104">如何尋找兩個位置路徑的聯集 (LINQ to XML) </span><span class="sxs-lookup"><span data-stu-id="cfacf-104">How to find a union of two location paths (LINQ to XML)</span></span>

<span data-ttu-id="cfacf-105">本文說明如何使用 <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> 來尋找兩個 XPath 位置路徑之結果的聯集，以及如何使用 <xref:System.Linq.Enumerable.Concat%2A> 標準查詢運算子來執行相同的動作。</span><span class="sxs-lookup"><span data-stu-id="cfacf-105">This article shows how to use <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> to find the union of the results of two XPath location paths, and how to use the <xref:System.Linq.Enumerable.Concat%2A> standard query operator to do the same thing.</span></span>

## <a name="example-find-all-category-and-price-elements-and-concatenate-them"></a><span data-ttu-id="cfacf-106">範例：尋找所有 `Category` 和 `Price` 元素並串連它們</span><span class="sxs-lookup"><span data-stu-id="cfacf-106">Example: Find all `Category` and `Price` elements and concatenate them</span></span>

<span data-ttu-id="cfacf-107">這個範例會尋找 `Category` xml 檔中的所有專案和所有 `Price` 元素的 [範例 Xml 檔：數值資料](sample-xml-file-numerical-data.md)，然後將它們串連成單一集合。</span><span class="sxs-lookup"><span data-stu-id="cfacf-107">This example finds all of the `Category` elements and all of the `Price` elements in XML document [Sample XML file: Numerical data](sample-xml-file-numerical-data.md), and concatenates them into a single collection.</span></span> <span data-ttu-id="cfacf-108">XPath 運算式為 `//Category|//Price`。</span><span class="sxs-lookup"><span data-stu-id="cfacf-108">The XPath expression is `//Category|//Price`.</span></span>

> [!NOTE]
> <span data-ttu-id="cfacf-109">LINQ to XML 查詢會呼叫 <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> ，以檔順序來放置結果。</span><span class="sxs-lookup"><span data-stu-id="cfacf-109">The LINQ to XML query calls <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> to put the results in document order.</span></span> <span data-ttu-id="cfacf-110">XPath 運算式結果也會以檔順序排列。</span><span class="sxs-lookup"><span data-stu-id="cfacf-110">The XPath expression results are also in document order.</span></span>

```csharp
XDocument data = XDocument.Load("Data.xml");

// LINQ to XML query
IEnumerable<XElement> list1 =
    data
    .Descendants("Category")
    .Concat(
        data
        .Descendants("Price")
    )
    .InDocumentOrder();

// XPath expression
IEnumerable<XElement> list2 = data.XPathSelectElements("//Category|//Price");

if (list1.Count() == list2.Count() &&
        list1.Intersect(list2).Count() == list1.Count())
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
foreach (XElement el in list1)
    Console.WriteLine(el);
```

```vb
Dim data As XDocument = XDocument.Load("Data.xml")

' LINQ to XML query
Dim list1 As IEnumerable(Of XElement) = _
    data...<Category>.Concat(data...<Price>).InDocumentOrder()

' XPath expression
Dim list2 As IEnumerable(Of XElement) = _
    data.XPathSelectElements("//Category|//Price")

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

<span data-ttu-id="cfacf-111">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="cfacf-111">This example produces the following output:</span></span>

```output
Results are identical
<Category>A</Category>
<Price>24.50</Price>
<Category>B</Category>
<Price>89.99</Price>
<Category>A</Category>
<Price>4.95</Price>
<Category>A</Category>
<Price>66.00</Price>
<Category>B</Category>
<Price>.99</Price>
<Category>A</Category>
<Price>29.00</Price>
<Category>B</Category>
<Price>6.99</Price>
```

## <a name="see-also"></a><span data-ttu-id="cfacf-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cfacf-112">See also</span></span>

- [<span data-ttu-id="cfacf-113">XPath 使用者的 LINQ to XML (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="cfacf-113">LINQ to XML for XPath Users (Visual Basic)</span></span>](./comparison-xpath-linq-xml.md)
