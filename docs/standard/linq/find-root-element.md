---
title: 如何尋找根項目-LINQ to XML
description: '瞭解如何在 c # 和 Visual Basic 中使用 XPath 和 LINQ to XML，以尋找 XML 檔的根項目。'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 4fd824e0-4d39-429b-b092-f6a5c046ee6c
ms.openlocfilehash: 16217960b84276bd3bb4c5cb6b38d7cb56d2b41e
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552186"
---
# <a name="how-to-find-the-root-element-linq-to-xml"></a><span data-ttu-id="cb18e-103">如何尋找 (LINQ to XML 的根項目) </span><span class="sxs-lookup"><span data-stu-id="cb18e-103">How to find the root element (LINQ to XML)</span></span>

<span data-ttu-id="cb18e-104">本文提供的範例示範如何使用 XPath 和 LINQ to XML （在 c # 和 Visual Basic 中）來尋找 XML 檔的根項目。</span><span class="sxs-lookup"><span data-stu-id="cb18e-104">This article provides an example that shows how to use XPath and LINQ to XML, in C# and Visual Basic, to find the root element of an XML document.</span></span>

## <a name="example-find-the-root-element"></a><span data-ttu-id="cb18e-105">範例：尋找根項目</span><span class="sxs-lookup"><span data-stu-id="cb18e-105">Example: Find the root element</span></span>

<span data-ttu-id="cb18e-106">這個範例會使用 LINQ to XML query 和 XPath 來尋找 XML 檔範例 XML 檔中的根項目 [：多個訂單](sample-xml-file-multiple-purchase-orders.md)。</span><span class="sxs-lookup"><span data-stu-id="cb18e-106">This example uses LINQ to XML query and XPath to find the root element in XML document [Sample XML file: Multiple purchase orders](sample-xml-file-multiple-purchase-orders.md).</span></span> <span data-ttu-id="cb18e-107">XPath 運算式為 `/PurchaseOrders`。</span><span class="sxs-lookup"><span data-stu-id="cb18e-107">The XPath expression is `/PurchaseOrders`.</span></span>

```csharp
XDocument po = XDocument.Load("PurchaseOrders.xml");

// LINQ to XML query
XElement el1 = po.Root;

// XPath expression
XElement el2 = po.XPathSelectElement("/PurchaseOrders");

if (el1 == el2)
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
Console.WriteLine(el1.Name);
```

```vb
Dim po As XDocument = XDocument.Load("PurchaseOrders.xml")

' LINQ to XML query
Dim el1 As XElement = po.Root

' XPath expression
Dim el2 As XElement = po.XPathSelectElement("/PurchaseOrders")

If el1 Is el2 Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If
Console.WriteLine(el1.Name)
```

<span data-ttu-id="cb18e-108">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="cb18e-108">This example produces the following output:</span></span>

```output
Results are identical
PurchaseOrders
```

## <a name="see-also"></a><span data-ttu-id="cb18e-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb18e-109">See also</span></span>

- [<span data-ttu-id="cb18e-110">XPath 使用者的 LINQ to XML (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="cb18e-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](/../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
