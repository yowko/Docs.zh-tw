---
title: 如何撰寫具有複雜篩選的查詢-LINQ to XML
description: 有時候您會想要利用複雜篩選撰寫 LINQ to XML 查詢。 例如，您可能必須尋找其子項目包含特定名稱和值的所有項目。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 4065d901-cf89-4e47-8bf9-abb65acfb003
ms.openlocfilehash: c5e7f812364e7e96e3a4b8f5515d07a3524ec979
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552808"
---
# <a name="how-to-write-queries-with-complex-filtering-linq-to-xml"></a>如何使用複雜的篩選撰寫查詢 (LINQ to XML) 

有時候您會想要利用複雜篩選撰寫 LINQ to XML 查詢。 例如，您可能必須尋找其子項目包含特定名稱和值的所有項目。 本文提供撰寫複雜篩選查詢的範例。

## <a name="example-find-with-a-nested-query-in-the-where-clause"></a>範例：在子句中使用巢狀查詢來尋找 `Where`

這個範例示範如何尋找 `PurchaseOrder` 具有下列專案的所有元素：

- `Address`其屬性等於「出貨」的子專案 `Type` 。
- `State`等於 "NY" 的子項目。

它會在 `Where` 子句中使用巢狀查詢，而且如果集合在其中有任何項目，`Any` 運算子會傳回 `true`。 此範例會使用 XML [檔範例 xml 檔：多份採購訂單](sample-xml-file-multiple-purchase-orders.md)。

如需有關運算子的詳細資訊 `Any` ，請參閱 [數量詞作業 (c # ) ](../../../docs/csharp/programming-guide/concepts/linq/quantifier-operations.md) 和 [數量詞作業 (Visual Basic) ](../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)。

```csharp
XElement root = XElement.Load("PurchaseOrders.xml");
IEnumerable<XElement> purchaseOrders =
    from el in root.Elements("PurchaseOrder")
    where
        (from add in el.Elements("Address")
        where
            (string)add.Attribute("Type") == "Shipping" &&
            (string)add.Element("State") == "NY"
        select add)
        .Any()
    select el;
foreach (XElement el in purchaseOrders)
    Console.WriteLine((string)el.Attribute("PurchaseOrderNumber"));
```

```vb
Dim root As XElement = XElement.Load("PurchaseOrders.xml")
Dim purchaseOrders As IEnumerable(Of XElement) = _
    From el In root.<PurchaseOrder> _
    Where _
        (From add In el.<Address> _
        Where _
             add.@Type = "Shipping" And _
             add.<State>.Value = "NY" _
        Select add) _
    .Any() _
    Select el
For Each el As XElement In purchaseOrders
    Console.WriteLine(el.@PurchaseOrderNumber)
Next
```

這個範例會產生下列輸出：

```output
99505
```

## <a name="example-find-in-xml-thats-in-a-namespace"></a>範例：在命名空間中的 XML 中尋找

下列範例顯示與上述相同的查詢，但針對命名空間中的 XML。 如需詳細資訊，請參閱 [命名空間總覽](namespaces-overview.md)。

此範例會使用 XML [檔範例 xml 檔：命名空間中的多個](sample-xml-file-multiple-purchase-orders-namespace.md)訂單。

```csharp
XElement root = XElement.Load("PurchaseOrdersInNamespace.xml");
XNamespace aw = "http://www.adventure-works.com";
IEnumerable<XElement> purchaseOrders =
    from el in root.Elements(aw + "PurchaseOrder")
    where
        (from add in el.Elements(aw + "Address")
         where
             (string)add.Attribute(aw + "Type") == "Shipping" &&
             (string)add.Element(aw + "State") == "NY"
         select add)
        .Any()
    select el;
foreach (XElement el in purchaseOrders)
    Console.WriteLine((string)el.Attribute(aw + "PurchaseOrderNumber"));
```

```vb
Imports <xmlns:aw='http://www.adventure-works.com'>

Module Module1
    Sub Main()
        Dim root As XElement = XElement.Load("PurchaseOrdersInNamespace.xml")
        Dim purchaseOrders As IEnumerable(Of XElement) = _
            From el In root.<aw:PurchaseOrder> _
            Where _
                (From add In el.<aw:Address> _
                Where _
                     add.@aw:Type = "Shipping" And _
                     add.<aw:State>.Value = "NY" _
                Select add) _
            .Any() _
            Select el
        For Each el As XElement In purchaseOrders
            Console.WriteLine(el.@aw:PurchaseOrderNumber)
        Next
    End Sub
End Module
```

這個範例會產生下列輸出：

```output
99505
```

## <a name="see-also"></a>另請參閱

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [投射作業 (C#)](../../csharp/programming-guide/concepts/linq/projection-operations.md)
- [數量詞作業 (C#)](../../csharp/programming-guide/concepts/linq/quantifier-operations.md)
- [XML 子代軸屬性 (Visual Basic)](../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [XML 屬性軸屬性 (Visual Basic)](../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
- [XML Value 屬性 (Visual Basic)](../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [投影作業 (Visual Basic) ](../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
- [數量詞作業 (Visual Basic) ](../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)
