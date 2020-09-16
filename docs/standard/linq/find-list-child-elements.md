---
title: 如何尋找子項目清單-LINQ to XML
description: 本文將比較 XPath 子專案座標軸與 LINQ to XML System.xml.linq.xcontainer.elements 元素軸。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 7c589dd8-f680-4cdb-9d6a-78d57e2555e8
ms.openlocfilehash: c575df2e8caa2125091265c00557b91a24601e48
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90549595"
---
# <a name="how-to-find-a-list-of-child-elements-linq-to-xml"></a>如何尋找 (LINQ to XML) 的子項目清單

本文會比較 XPath 子項目軸與 LINQ to XML <xref:System.Xml.Linq.XContainer.Elements%2A> 軸。

## <a name="example-find-all-child-elements-of-an-element"></a>範例：尋找元素的所有子項目

此範例會尋找 XML 檔範例 XML 檔中專案的所有子項目 `Address` [：多個採購訂單](sample-xml-file-multiple-purchase-orders.md)。

XPath 運算式為：`./*`

```csharp
XDocument cpo = XDocument.Load("PurchaseOrders.xml");
XElement po = cpo.Root.Element("PurchaseOrder").Element("Address");

// LINQ to XML query
IEnumerable<XElement> list1 = po.Elements();

// XPath expression
IEnumerable<XElement> list2 = po.XPathSelectElements("./*");

if (list1.Count() == list2.Count() &&
        list1.Intersect(list2).Count() == list1.Count())
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
foreach (XElement el in list1)
    Console.WriteLine(el);
```

```vb
Dim cpo As XDocument = XDocument.Load("PurchaseOrders.xml")
Dim po As XElement = cpo.Root.<PurchaseOrder>.<Address>.FirstOrDefault

' LINQ to XML query
Dim list1 As IEnumerable(Of XElement) = po.Elements()

' XPath expression
Dim list2 As IEnumerable(Of XElement) = po.XPathSelectElements("./*")

If (list1.Count() = list2.Count()) AndAlso _
    (list1.Intersect(list2).Count() = list1.Count()) Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If
For Each el As XElement In list1
    Console.WriteLine(el)
Next
```

這個範例會產生下列輸出：

```output
Results are identical
<Name>Ellen Adams</Name>
<Street>123 Maple Street</Street>
<City>Mill Valley</City>
<State>CA</State>
<Zip>10999</Zip>
<Country>USA</Country>
```

## <a name="see-also"></a>另請參閱

- [XPath 使用者的 LINQ to XML (Visual Basic) ](./comparison-xpath-linq-xml.md)
