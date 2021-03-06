---
title: 如何排序元素-LINQ to XML
description: 瞭解如何撰寫排序其結果的查詢。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: aee6fbbc-81fd-4b3e-b40f-6ed7b3bd3fee
ms.openlocfilehash: 0e93add12e39c71c7312036917d42dd53450b712
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550066"
---
# <a name="how-to-sort-elements-linq-to-xml"></a>如何排序元素 (LINQ to XML) 

您可以在查詢 XML 時排序結果。 本文提供兩個範例：第一個會排序 *不* 在命名空間中之 xml 的結果，而第二個則會執行相同的排序，但針對命名 *空間中的* xml。

## <a name="example-write-a-query-that-sorts-its-results"></a>範例：撰寫排序其結果的查詢

此範例顯示如何撰寫排序其結果的查詢。 它使用 XML [檔範例 xml 檔：數值資料](sample-xml-file-numerical-data.md)。

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

這個範例會產生下列輸出：

```output
0.99
4.95
6.99
24.50
29.00
66.00
89.99
```

## <a name="example-write-a-query-in-a-namespace-that-sorts-its-results"></a>範例：在命名空間中撰寫排序其結果的查詢

下列範例顯示命名空間中的相同 XML 查詢。 它使用 XML [檔範例 xml 檔：命名空間中的數值資料](sample-xml-file-numerical-data-namespace.md)。

如需詳細資訊，請參閱 [命名空間總覽](namespaces-overview.md)。

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

這個範例會產生下列輸出：

```output
0.99
4.95
6.99
24.50
29.00
66.00
89.99
```

## <a name="see-also"></a>另請參閱

- [排序資料 (C#)](../../csharp/programming-guide/concepts/linq/sorting-data.md)
- [排序資料 (Visual Basic) ](../../visual-basic/programming-guide/concepts/linq/sorting-data.md)
- [基本查詢 (LINQ to XML)  (Visual Basic) ](./find-element-specific-attribute.md)
