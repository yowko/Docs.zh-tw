---
title: 如何尋找子項目-LINQ to XML
description: 本文會比較 XPath 子項目軸與 LINQ to XML <xref:System.Xml.Linq.XContainer.Element%2A> 方法。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 4fa6182d-6196-4ed1-9c9e-82949ff89c71
ms.openlocfilehash: 34ddfd78489927a40128196a6fc80e822302428b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557125"
---
# <a name="how-to-find-a-child-element-linq-to-xml"></a>如何尋找 (LINQ to XML 的子項目) 

本文會比較 XPath 子項目軸與 LINQ to XML <xref:System.Xml.Linq.XContainer.Element%2A> 方法。

## <a name="example-find-a-child-element-in-an-xml-document"></a>範例：尋找 XML 檔中的子項目

此範例會尋找 `DeliveryNotes` xml 檔範例 xml 檔中的子專案 [：多個採購訂單](sample-xml-file-multiple-purchase-orders.md)。

XPath 運算式為 `DeliveryNotes`。

```csharp
XDocument cpo = XDocument.Load("PurchaseOrders.xml");
XElement po = cpo.Root.Element("PurchaseOrder");

// LINQ to XML query
XElement el1 = po.Element("DeliveryNotes");

// XPath expression
XElement el2 = po.XPathSelectElement("DeliveryNotes");
// same as "child::DeliveryNotes"
// same as "./DeliveryNotes"

if (el1 == el2)
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
Console.WriteLine(el1);
```

```vb
Dim cpo As XDocument = XDocument.Load("PurchaseOrders.xml")
Dim po As XElement = cpo.Root.<PurchaseOrder>.FirstOrDefault

'LINQ to XML query
Dim el1 As XElement = po.<DeliveryNotes>.FirstOrDefault

' XPath expression
Dim el2 As XElement = po.XPathSelectElement("DeliveryNotes")
' same as "child::DeliveryNotes"
' same as "./DeliveryNotes"

If el1 Is el2 Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If
Console.WriteLine(el1)
```

這個範例會產生下列輸出：

```output
Results are identical
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>
```

## <a name="see-also"></a>另請參閱

- [XPath 使用者的 LINQ to XML (Visual Basic) ](./comparison-xpath-linq-xml.md)
