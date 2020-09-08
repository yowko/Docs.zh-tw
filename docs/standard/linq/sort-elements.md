---
title: 如何排序元素-LINQ to XML
description: 瞭解如何撰寫排序其結果的查詢。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: aee6fbbc-81fd-4b3e-b40f-6ed7b3bd3fee
ms.openlocfilehash: c2d7915aacf0c41e99581fa8b5cc397bcaf5c612
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552253"
---
# <a name="how-to-sort-elements-linq-to-xml"></a><span data-ttu-id="bb64f-103">如何排序元素 (LINQ to XML) </span><span class="sxs-lookup"><span data-stu-id="bb64f-103">How to sort elements (LINQ to XML)</span></span>

<span data-ttu-id="bb64f-104">您可以在查詢 XML 時排序結果。</span><span class="sxs-lookup"><span data-stu-id="bb64f-104">You can sort your results when you query XML.</span></span> <span data-ttu-id="bb64f-105">本文提供兩個範例：第一個會排序 *不* 在命名空間中之 xml 的結果，而第二個則會執行相同的排序，但針對命名 *空間中的* xml。</span><span class="sxs-lookup"><span data-stu-id="bb64f-105">This article provides two examples: the first sorts results for XML that *isn't* in a namespace, and the second does the same sort, but for XML that *is* in a namespace.</span></span>

## <a name="example-write-a-query-that-sorts-its-results"></a><span data-ttu-id="bb64f-106">範例：撰寫排序其結果的查詢</span><span class="sxs-lookup"><span data-stu-id="bb64f-106">Example: Write a query that sorts its results</span></span>

<span data-ttu-id="bb64f-107">此範例顯示如何撰寫排序其結果的查詢。</span><span class="sxs-lookup"><span data-stu-id="bb64f-107">This example shows how to write a query that sorts its results.</span></span> <span data-ttu-id="bb64f-108">它使用 XML [檔範例 xml 檔：數值資料](sample-xml-file-numerical-data.md)。</span><span class="sxs-lookup"><span data-stu-id="bb64f-108">It uses XML document [Sample XML file: Numerical data](sample-xml-file-numerical-data.md).</span></span>

```csharp
XElement root = XElement.Load("Data.xml");
IEnumerable<decimal> prices =
    from el in root.Elements("Data")
    let price = (decimal)el.Element("Price")
    orderby price
    select price;
foreach (decimal el in prices)
    Console.WriteLine(el);
```

```vb
Dim root As XElement = XElement.Load("Data.xml")
Dim prices As IEnumerable(Of Decimal) = _
    From el In root.<Data> _
    Let price = Convert.ToDecimal(el.<Price>.Value) _
    Order By (price) _
    Select price
For Each el As Decimal In prices
    Console.WriteLine(el)
Next
```

<span data-ttu-id="bb64f-109">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="bb64f-109">This example produces the following output:</span></span>

```output
0.99
4.95
6.99
24.50
29.00
66.00
89.99
```

## <a name="example-write-a-query-in-a-namespace-that-sorts-its-results"></a><span data-ttu-id="bb64f-110">範例：在命名空間中撰寫排序其結果的查詢</span><span class="sxs-lookup"><span data-stu-id="bb64f-110">Example: Write a query in a namespace that sorts its results</span></span>

<span data-ttu-id="bb64f-111">下列範例顯示命名空間中的相同 XML 查詢。</span><span class="sxs-lookup"><span data-stu-id="bb64f-111">The following example shows the same query for XML that's in a namespace.</span></span> <span data-ttu-id="bb64f-112">它使用 XML [檔範例 xml 檔：命名空間中的數值資料](sample-xml-file-numerical-data-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="bb64f-112">It uses XML document [Sample XML file: Numerical data in a namespace](sample-xml-file-numerical-data-namespace.md).</span></span>

<span data-ttu-id="bb64f-113">如需詳細資訊，請參閱 [命名空間總覽](namespaces-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="bb64f-113">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

```csharp
XElement root = XElement.Load("DataInNamespace.xml");
XNamespace aw = "http://www.adatum.com";
IEnumerable<decimal> prices =
    from el in root.Elements(aw + "Data")
    let price = (decimal)el.Element(aw + "Price")
    orderby price
    select price;
foreach (decimal el in prices)
    Console.WriteLine(el);
```

```vb
Imports <xmlns='http://www.adatum.com'>

Module Module1
    Sub Main()
        Dim root As XElement = XElement.Load("DataInNamespace.xml")
        Dim prices As IEnumerable(Of Decimal) = _
            From el In root.<Data> _
            Let price = Convert.ToDecimal(el.<Price>.Value) _
            Order By (price) _
            Select price
        For Each el As Decimal In prices
            Console.WriteLine(el)
        Next
    End Sub
End Module
```

<span data-ttu-id="bb64f-114">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="bb64f-114">This example produces the following output:</span></span>

```output
0.99
4.95
6.99
24.50
29.00
66.00
89.99
```

## <a name="see-also"></a><span data-ttu-id="bb64f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb64f-115">See also</span></span>

- [<span data-ttu-id="bb64f-116">排序資料 (C#)</span><span class="sxs-lookup"><span data-stu-id="bb64f-116">Sorting Data (C#)</span></span>](../../csharp/programming-guide/concepts/linq/sorting-data.md)
- [<span data-ttu-id="bb64f-117">排序資料 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="bb64f-117">Sorting Data (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/sorting-data.md)
- [<span data-ttu-id="bb64f-118">基本查詢 (LINQ to XML)  (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="bb64f-118">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
