---
title: 如何尋找子項目清單-LINQ to XML
description: 本文將比較 XPath 子專案座標軸與 LINQ to XML System.xml.linq.xcontainer.elements 元素軸。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 7c589dd8-f680-4cdb-9d6a-78d57e2555e8
ms.openlocfilehash: 84b820f3192a173130c485f3e7cdadf9499932f1
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552196"
---
# <a name="how-to-find-a-list-of-child-elements-linq-to-xml"></a><span data-ttu-id="e4017-103">如何尋找 (LINQ to XML) 的子項目清單</span><span class="sxs-lookup"><span data-stu-id="e4017-103">How to find a list of child elements (LINQ to XML)</span></span>

<span data-ttu-id="e4017-104">本文會比較 XPath 子項目軸與 LINQ to XML <xref:System.Xml.Linq.XContainer.Elements%2A> 軸。</span><span class="sxs-lookup"><span data-stu-id="e4017-104">This article compares the XPath child elements axis to the LINQ to XML <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span>

## <a name="example-find-all-child-elements-of-an-element"></a><span data-ttu-id="e4017-105">範例：尋找元素的所有子項目</span><span class="sxs-lookup"><span data-stu-id="e4017-105">Example: Find all child elements of an element</span></span>

<span data-ttu-id="e4017-106">此範例會尋找 XML 檔範例 XML 檔中專案的所有子項目 `Address` [：多個採購訂單](sample-xml-file-multiple-purchase-orders.md)。</span><span class="sxs-lookup"><span data-stu-id="e4017-106">This example finds all of the child elements of the `Address` element in XML document [Sample XML file: Multiple purchase orders](sample-xml-file-multiple-purchase-orders.md).</span></span>

<span data-ttu-id="e4017-107">XPath 運算式為：`./*`</span><span class="sxs-lookup"><span data-stu-id="e4017-107">The XPath expression is: `./*`</span></span>

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

<span data-ttu-id="e4017-108">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="e4017-108">This example produces the following output:</span></span>

```output
Results are identical
<Name>Ellen Adams</Name>
<Street>123 Maple Street</Street>
<City>Mill Valley</City>
<State>CA</State>
<Zip>10999</Zip>
<Country>USA</Country>
```

## <a name="see-also"></a><span data-ttu-id="e4017-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4017-109">See also</span></span>

- [<span data-ttu-id="e4017-110">XPath 使用者的 LINQ to XML (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="e4017-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
