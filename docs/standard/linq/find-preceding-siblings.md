---
title: 如何尋找先前的同級-LINQ to XML
description: 瞭解如何在指定元素之前尋找同級元素。 顯示兩個方法：一個使用 System.xml.xpath.extensions.xpathselectelements 沿著前一個同級軸，另一個則使用 System.xml.linq.xnode>. System.xml.linq.xnode.elementsbeforeself。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: b281ff99-d08a-43d0-bea1-eff831b2f8ae
ms.openlocfilehash: 0cfd516f274eaf2940a7b944d34c6ea494e7eaa1
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546186"
---
# <a name="how-to-find-preceding-siblings-linq-to-xml"></a>如何找出先前的同級 (LINQ to XML) 

本文說明如何使用上一個 <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> 同級軸來尋找在指定專案之前的同級元素，以及如何使用 <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> 來尋找相同的元素。

## <a name="example-use-two-methods-to-find-sibling-elements-that-precede-an-element"></a>範例：使用兩個方法來尋找元素之前的同級元素

下列範例會尋找 `FullAddress` xml 檔範例 xml 檔中的元素 [：客戶和訂單](sample-xml-file-customers-orders.md)，並以兩種不同的方式抓取上述的同級元素。 然後，它會比較結果並尋找相同的結果。

> [!NOTE]
> 這兩種方法都會提供依檔順序排列的結果。

使用的 XPath 運算式是 `preceding-sibling::*` 。

```csharp
XElement co = XElement.Load("CustomersOrders.xml");

XElement add = co.Element("Customers").Element("Customer").Element("FullAddress");

// LINQ to XML query
IEnumerable<XElement> list1 = add.ElementsBeforeSelf();

// XPath expression
IEnumerable<XElement> list2 = add.XPathSelectElements("preceding-sibling::*");

if (list1.Count() == list2.Count() &&
        list1.Intersect(list2).Count() == list1.Count())
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
foreach (XElement el in list2)
    Console.WriteLine(el);
```

```vb
Dim co As XElement = XElement.Load("CustomersOrders.xml")
Dim add As XElement = co.<Customers>.<Customer>. _
        <FullAddress>.FirstOrDefault

' LINQ to XML query
Dim list1 As IEnumerable(Of XElement) = add.ElementsBeforeSelf()

' XPath expression
Dim list2 As IEnumerable(Of XElement) = add.XPathSelectElements("preceding-sibling::*")

If list1.Count() = list2.Count() And _
        list1.Intersect(list2).Count() = list1.Count() Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If
For Each el As XElement In list2
    Console.WriteLine(el)
Next
```

這個範例會產生下列輸出：

```output
Results are identical
<CompanyName>Great Lakes Food Market</CompanyName>
<ContactName>Howard Snyder</ContactName>
<ContactTitle>Marketing Manager</ContactTitle>
<Phone>(503) 555-7555</Phone>
```

## <a name="see-also"></a>另請參閱

- [XPath 使用者的 LINQ to XML (Visual Basic) ](./comparison-xpath-linq-xml.md)
