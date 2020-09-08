---
title: 如何篩選屬性-LINQ to XML
description: '本文說明如何使用 LINQ to XML query 和 XPath （在 c # 和 Visual Basic 中）來尋找具有指定名稱和屬性值的子系元素。'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 208d6256-1bd7-4237-b2c9-909f26dfd0e2
ms.openlocfilehash: 51867cefcdfc42812d4003fb669c11751fb3ca34
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552102"
---
# <a name="how-to-filter-on-an-attribute-linq-to-xml"></a>如何篩選屬性 (LINQ to XML) 

本文說明如何使用 LINQ to XML query 和 XPath （在 c # 和 Visual Basic 中）來尋找具有指定名稱和屬性值的子系元素。

## <a name="example-find-all-descendant-elements-that-have-a-specified-name-and-attribute-value"></a>範例：尋找具有指定名稱和屬性值的所有子代元素

這個範例會使用 LINQ to XML query 和 XPath 來尋找 XML [檔範例 xml 檔：多份採購訂單](sample-xml-file-multiple-purchase-orders.md)、名稱為的所有子系元素 `Address` ，以及 `Type` 值為 "運費" 的屬性。 XPath 運算式為 `.//Address[@Type='Shipping']`

```csharp
XDocument po = XDocument.Load("PurchaseOrders.xml");

// LINQ to XML query
IEnumerable<XElement> list1 =
    from el in po.Descendants("Address")
    where (string)el.Attribute("Type") == "Shipping"
    select el;

// XPath expression
IEnumerable<XElement> list2 = po.XPathSelectElements(".//Address[@Type='Shipping']");

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
Dim list1 As IEnumerable(Of XElement) = _
    From el In po...<Address> _
    Where el.@Type = "Shipping" _
    Select el

' XPath expression
Dim list2 As IEnumerable(Of XElement) = _
    po.XPathSelectElements(".//Address[@Type='Shipping']")

If (list1.Count = list2.Count And _
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
<Address Type="Shipping">
  <Name>Ellen Adams</Name>
  <Street>123 Maple Street</Street>
  <City>Mill Valley</City>
  <State>CA</State>
  <Zip>10999</Zip>
  <Country>USA</Country>
</Address>
<Address Type="Shipping">
  <Name>Cristian Osorio</Name>
  <Street>456 Main Street</Street>
  <City>Buffalo</City>
  <State>NY</State>
  <Zip>98112</Zip>
  <Country>USA</Country>
</Address>
<Address Type="Shipping">
  <Name>Jessica Arnold</Name>
  <Street>4055 Madison Ave</Street>
  <City>Seattle</City>
  <State>WA</State>
  <Zip>98112</Zip>
  <Country>USA</Country>
</Address>
```

## <a name="see-also"></a>另請參閱

- [XPath 使用者的 LINQ to XML (Visual Basic) ](/../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
