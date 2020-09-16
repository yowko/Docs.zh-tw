---
title: 如何尋找具有特定屬性的元素-LINQ to XML
description: 瞭解如何尋找其屬性具有特定值的元素。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: b92591aa-3cfb-490e-99f6-da8de335e362
ms.openlocfilehash: a1569f8a91e980f12ecc1801e00d6414711833d0
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90535457"
---
# <a name="how-to-find-an-element-with-a-specific-attribute-linq-to-xml"></a>如何尋找具有特定屬性 (LINQ to XML) 的元素

本文提供的範例將說明如何尋找其屬性具有特定值的元素。

## <a name="example-find-an-element-whose-attribute-has-a-specific-value"></a>範例：尋找其屬性具有特定值的元素

下列範例顯示如何尋找 `Address` 具有 `Type` 值為 "帳單" 之屬性的專案。 此範例會使用 XML [檔範例 xml 檔：典型的採購訂單](sample-xml-file-typical-purchase-order.md)。

```csharp
XElement root = XElement.Load("PurchaseOrder.xml");
IEnumerable<XElement> address =
    from el in root.Elements("Address")
    where (string)el.Attribute("Type") == "Billing"
    select el;
foreach (XElement el in address)
    Console.WriteLine(el);
```

```vb
Dim root As XElement = XElement.Load("PurchaseOrder.xml")
Dim address As IEnumerable(Of XElement) = _
    From el In root.<Address> _
    Where el.@Type = "Billing" _
    Select el
For Each el As XElement In address
    Console.WriteLine(el)
Next
```

這個範例會產生下列輸出：

```xml
<Address Type="Billing">
  <Name>Tai Yee</Name>
  <Street>8 Oak Avenue</Street>
  <City>Old Town</City>
  <State>PA</State>
  <Zip>95819</Zip>
  <Country>USA</Country>
</Address>
```

## <a name="example-find-an-element-in-xml-thats-in-a-namespace"></a>範例：在命名空間中尋找 XML 內的元素

下列範例顯示相同的查詢，但針對命名空間中的 XML。 它使用 XML [檔範例 xml 檔：命名空間中的典型採購訂單](sample-xml-file-typical-purchase-order-namespace.md)。

如需命名空間的詳細資訊，請參閱 [命名空間總覽](namespaces-overview.md)。

```csharp
XElement root = XElement.Load("PurchaseOrderInNamespace.xml");
XNamespace aw = "http://www.adventure-works.com";
IEnumerable<XElement> address =
    from el in root.Elements(aw + "Address")
    where (string)el.Attribute(aw + "Type") == "Billing"
    select el;
foreach (XElement el in address)
    Console.WriteLine(el);
```

```vb
Imports <xmlns:aw='http://www.adventure-works.com'>

Module Module1
    Sub Main()
        Dim root As XElement = XElement.Load("PurchaseOrderInNamespace.xml")
        Dim address As IEnumerable(Of XElement) = _
            From el In root.<aw:Address> _
            Where el.@aw:Type = "Billing" _
            Select el
        For Each el As XElement In address
            Console.WriteLine(el)
        Next
    End Sub
End Module
```

此範例會產生下列輸出：

```xml
<aw:Address aw:Type="Billing" xmlns:aw="http://www.adventure-works.com">
  <aw:Name>Tai Yee</aw:Name>
  <aw:Street>8 Oak Avenue</aw:Street>
  <aw:City>Old Town</aw:City>
  <aw:State>PA</aw:State>
  <aw:Zip>95819</aw:Zip>
  <aw:Country>USA</aw:Country>
</aw:Address>
```

## <a name="see-also"></a>另請參閱

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [標準查詢運算子概觀 (C#)](../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [投射作業 (C#)](../../csharp/programming-guide/concepts/linq/projection-operations.md)
- [基本查詢 (LINQ to XML)  (Visual Basic) ](../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md)
- [標準查詢運算子概觀 (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [投影作業 (Visual Basic) ](../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
