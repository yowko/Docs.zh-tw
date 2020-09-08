---
title: 如何取出元素集合-LINQ to XML
description: 瞭解如何使用 System.xml.linq.xcontainer.elements 方法來取出專案的子項目集合。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: b849668c-7976-4974-b8e1-1cd587d34258
ms.openlocfilehash: e73f608cff13f75f769f77372dc1c09949e00b0e
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552119"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml"></a>如何擷取元素集合 (LINQ to XML)

本文將示範方法，該方法會抓取專案的 <xref:System.Xml.Linq.XContainer.Elements%2A> 子項目集合。

## <a name="example-iterate-through-the-child-elements-of-an-element"></a>範例：逐一查看元素的子項目

此範例會逐一查看 `purchaseOrder` 項目的子項目。 它使用 XML [檔範例 xml 檔：典型的採購訂單](sample-xml-file-typical-purchase-order.md)。

```csharp
XElement po = XElement.Load("PurchaseOrder.xml");
IEnumerable<XElement> childElements =
    from el in po.Elements()
    select el;
foreach (XElement el in childElements)
    Console.WriteLine("Name: " + el.Name);
```

```vb
Dim po As XElement = XElement.Load("PurchaseOrder.xml")
Dim childElements As IEnumerable(Of XElement)
childElements = _
    From el In po.Elements() _
    Select el
For Each el As XElement In childElements
    Console.WriteLine("Name: " & el.Name.ToString())
Next
```

這個範例會產生下列輸出：

```output
Name: Address
Name: Address
Name: DeliveryNotes
Name: Items
```

## <a name="see-also"></a>另請參閱

- [LINQ to XML 軸總覽](linq-xml-axes-overview.md)
