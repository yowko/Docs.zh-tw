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
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml"></a><span data-ttu-id="8602c-103">如何擷取元素集合 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="8602c-103">How to retrieve a collection of elements (LINQ to XML)</span></span>

<span data-ttu-id="8602c-104">本文將示範方法，該方法會抓取專案的 <xref:System.Xml.Linq.XContainer.Elements%2A> 子項目集合。</span><span class="sxs-lookup"><span data-stu-id="8602c-104">This article demonstrates the <xref:System.Xml.Linq.XContainer.Elements%2A> method, which retrieves a collection of the child elements of an element.</span></span>

## <a name="example-iterate-through-the-child-elements-of-an-element"></a><span data-ttu-id="8602c-105">範例：逐一查看元素的子項目</span><span class="sxs-lookup"><span data-stu-id="8602c-105">Example: Iterate through the child elements of an element</span></span>

<span data-ttu-id="8602c-106">此範例會逐一查看 `purchaseOrder` 項目的子項目。</span><span class="sxs-lookup"><span data-stu-id="8602c-106">This example iterates through the child elements of the `purchaseOrder` element.</span></span> <span data-ttu-id="8602c-107">它使用 XML [檔範例 xml 檔：典型的採購訂單](sample-xml-file-typical-purchase-order.md)。</span><span class="sxs-lookup"><span data-stu-id="8602c-107">It uses XML document [Sample XML file: Typical purchase order](sample-xml-file-typical-purchase-order.md).</span></span>

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

<span data-ttu-id="8602c-108">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="8602c-108">This example produces the following output:</span></span>

```output
Name: Address
Name: Address
Name: DeliveryNotes
Name: Items
```

## <a name="see-also"></a><span data-ttu-id="8602c-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8602c-109">See also</span></span>

- [<span data-ttu-id="8602c-110">LINQ to XML 軸總覽</span><span class="sxs-lookup"><span data-stu-id="8602c-110">LINQ to XML axes overview</span></span>](linq-xml-axes-overview.md)
