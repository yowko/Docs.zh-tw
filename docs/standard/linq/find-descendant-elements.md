---
title: 如何尋找子代元素-LINQ to XML
description: '本文說明如何在 c # 和 Visual Basic 中使用 XPath 和 LINQ to XML 查詢，以尋找具有指定名稱的所有子系元素。'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: b318da39-bb8b-4c56-a019-e13b12b01831
ms.openlocfilehash: 36547c4ad39953e25bf7a8d5f69aa4a712e51982
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554229"
---
# <a name="how-to-find-descendant-elements-linq-to-xml"></a>如何尋找 (LINQ to XML) 的子代元素

本文說明如何在 c # 和 Visual Basic 中使用 XPath 和 LINQ to XML 查詢，以尋找具有指定名稱的所有子系元素。

## <a name="example-find-descendant-elements-that-have-a-specified-name"></a>範例：尋找具有指定名稱的子系元素

 此範例示範如何使用 LINQ to XML query 和 XPath 來尋找 XML 檔範例 XML 檔中所命名的所有子系專案 `Name` [：多個訂單](sample-xml-file-multiple-purchase-orders.md)。 XPath 運算式為 `//Name`。

```csharp
XDocument po = XDocument.Load("PurchaseOrders.xml");

// LINQ to XML query
IEnumerable<XElement> list1 = po.Root.Descendants("Name");

// XPath expression
IEnumerable<XElement> list2 = po.XPathSelectElements("//Name");

if (list1.Count() == list2.Count() &&
        list1.Intersect(list2).Count() == list1.Count())
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
foreach (XElement el in list1)
    Console.WriteLine(el);
```

```vb
Dim po As XDocument = XDocument.Load("PurchaseOrders.xml")

' LINQ to XML query
Dim list1 As IEnumerable(Of XElement) = po...<Name>

' XPath expression
Dim list2 As IEnumerable(Of XElement) = po.XPathSelectElements("//Name")

If (list1.Count() = list2.Count() And _
        list1.Intersect(list2).Count() = list1.Count()) Then
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
<Name>Tai Yee</Name>
<Name>Cristian Osorio</Name>
<Name>Cristian Osorio</Name>
<Name>Jessica Arnold</Name>
<Name>Jessica Arnold</Name>
```

## <a name="see-also"></a>另請參閱

- [XPath 使用者的 LINQ to XML (Visual Basic) ](./comparison-xpath-linq-xml.md)
