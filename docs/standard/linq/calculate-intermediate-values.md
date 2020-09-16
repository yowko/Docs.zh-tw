---
title: 如何計算中繼值-LINQ to XML
description: 計算用來排序、篩選和選取的中繼值。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 7fd3001f-f8f9-4bce-879f-d4c7af8a04fe
ms.openlocfilehash: c37926b93e0dc11255fd27c312679f6286fa7e5d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558115"
---
# <a name="how-to-calculate-intermediate-values-linq-to-xml"></a><span data-ttu-id="aa805-103">如何計算 (LINQ to XML) 的中繼值</span><span class="sxs-lookup"><span data-stu-id="aa805-103">How to calculate intermediate values (LINQ to XML)</span></span>

<span data-ttu-id="aa805-104">本文說明如何計算在 c # 和 Visual Basic 中排序、篩選和選取使用的中繼值。</span><span class="sxs-lookup"><span data-stu-id="aa805-104">This article shows how to calculate intermediate values for use in sorting, filtering, and selecting in C# and Visual Basic.</span></span>

## <a name="example-use-the-let-clause-to-calculate-based-on-element-data"></a><span data-ttu-id="aa805-105">範例：使用 `let` 子句根據元素資料進行計算</span><span class="sxs-lookup"><span data-stu-id="aa805-105">Example: Use the `let` clause to calculate based on element data</span></span>

<span data-ttu-id="aa805-106">下列範例會使用 `let` 子句來計算元素中數值的乘積。</span><span class="sxs-lookup"><span data-stu-id="aa805-106">The following example uses the `let` clause to calculate products of numerical values from elements.</span></span> <span data-ttu-id="aa805-107">它使用 XML [檔範例 xml 檔：數值資料](sample-xml-file-numerical-data.md)。</span><span class="sxs-lookup"><span data-stu-id="aa805-107">It uses XML document [Sample XML file: Numerical data](sample-xml-file-numerical-data.md).</span></span>

```csharp
XElement root = XElement.Load("Data.xml");
IEnumerable<decimal> extensions =
    from el in root.Elements("Data")
    let extension = (decimal)el.Element("Quantity") * (decimal)el.Element("Price")
    where extension >= 25
    orderby extension
    select extension;
foreach (decimal ex in extensions)
    Console.WriteLine(ex);
```

```vb
Dim root As XElement = XElement.Load("Data.xml")
Dim extensions As IEnumerable(Of Decimal) = _
    From el In root.<Data> _
    Let extension = CDec(el.<Quantity>.Value) * CDec(el.<Price>.Value) _
    Where extension > 25 _
    Order By extension _
    Select extension
For Each ex As Decimal In extensions
    Console.WriteLine(ex)
Next
```

<span data-ttu-id="aa805-108">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="aa805-108">This example produces the following output:</span></span>

```output
55.92
73.50
89.99
198.00
435.00
```

## <a name="example-calculate-from-xml-thats-in-a-namespace"></a><span data-ttu-id="aa805-109">範例：從命名空間中的 XML 計算</span><span class="sxs-lookup"><span data-stu-id="aa805-109">Example: Calculate from XML that's in a namespace</span></span>

<span data-ttu-id="aa805-110">下列範例顯示與之前相同的查詢，但針對命名空間中的 XML。</span><span class="sxs-lookup"><span data-stu-id="aa805-110">The following example shows the same query as before, but for XML that's in a namespace.</span></span> <span data-ttu-id="aa805-111">它會使用 XML [檔範例 xml 檔：命名空間中的數值資料](sample-xml-file-numerical-data-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="aa805-111">It uses the XML document [Sample XML file: Numerical data in a namespace](sample-xml-file-numerical-data-namespace.md).</span></span>

<span data-ttu-id="aa805-112">如需詳細資訊，請參閱 [命名空間總覽](namespaces-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="aa805-112">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

```csharp
XElement root = XElement.Load("DataInNamespace.xml");
XNamespace ad = "http://www.adatum.com";
IEnumerable<decimal> extensions =
    from el in root.Elements(ad + "Data")
    let extension = (decimal)el.Element(ad + "Quantity") * (decimal)el.Element(ad + "Price")
    where extension >= 25
    orderby extension
    select extension;
foreach (decimal ex in extensions)
    Console.WriteLine(ex);
```

```vb
Imports <xmlns="http://www.adatum.com">

Module Module1
    Sub Main()
        Dim root As XElement = XElement.Load("DataInNamespace.xml")
        Dim extensions As IEnumerable(Of Decimal) = _
            From el In root.<Data> _
            Let extension = CDec(el.<Quantity>.Value) * CDec(el.<Price>.Value) _
            Where extension > 25 _
            Order By extension _
            Select extension
        For Each ex As Decimal In extensions
            Console.WriteLine(ex)
        Next
    End Sub
End Module
```

<span data-ttu-id="aa805-113">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="aa805-113">This example produces the following output:</span></span>

```output
55.92
73.50
89.99
198.00
435.00
```

## <a name="see-also"></a><span data-ttu-id="aa805-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aa805-114">See also</span></span>

- [<span data-ttu-id="aa805-115">基本查詢 (LINQ to XML)  (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="aa805-115">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](./find-element-specific-attribute.md)
