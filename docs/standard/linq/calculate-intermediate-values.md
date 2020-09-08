---
title: 如何計算中繼值-LINQ to XML
description: 計算用來排序、篩選和選取的中繼值。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 7fd3001f-f8f9-4bce-879f-d4c7af8a04fe
ms.openlocfilehash: aa5b83e9bf359481773db673fd3de9c4dcff6af2
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552141"
---
# <a name="how-to-calculate-intermediate-values-linq-to-xml"></a>如何計算 (LINQ to XML) 的中繼值

本文說明如何計算在 c # 和 Visual Basic 中排序、篩選和選取使用的中繼值。

## <a name="example-use-the-let-clause-to-calculate-based-on-element-data"></a>範例：使用 `let` 子句根據元素資料進行計算

下列範例會使用 `let` 子句來計算元素中數值的乘積。 它使用 XML [檔範例 xml 檔：數值資料](sample-xml-file-numerical-data.md)。

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

這個範例會產生下列輸出：

```output
55.92
73.50
89.99
198.00
435.00
```

## <a name="example-calculate-from-xml-thats-in-a-namespace"></a>範例：從命名空間中的 XML 計算

下列範例顯示與之前相同的查詢，但針對命名空間中的 XML。 它會使用 XML [檔範例 xml 檔：命名空間中的數值資料](sample-xml-file-numerical-data-namespace.md)。

如需詳細資訊，請參閱 [命名空間總覽](namespaces-overview.md)。

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

這個範例會產生下列輸出：

```output
55.92
73.50
89.99
198.00
435.00
```

## <a name="see-also"></a>另請參閱

- [基本查詢 (LINQ to XML)  (Visual Basic) ](../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
