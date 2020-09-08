---
title: 如何尋找具有特定屬性的元素-LINQ to XML
description: 瞭解如何尋找其屬性具有特定值的元素。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: b92591aa-3cfb-490e-99f6-da8de335e362
ms.openlocfilehash: 4c74de90a348d81ac87c98bf6ee27f3c78f34e83
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552089"
---
# <a name="how-to-find-an-element-with-a-specific-attribute-linq-to-xml"></a><span data-ttu-id="fe6e2-103">如何尋找具有特定屬性 (LINQ to XML) 的元素</span><span class="sxs-lookup"><span data-stu-id="fe6e2-103">How to find an element with a specific attribute (LINQ to XML)</span></span>

<span data-ttu-id="fe6e2-104">本文提供的範例將說明如何尋找其屬性具有特定值的元素。</span><span class="sxs-lookup"><span data-stu-id="fe6e2-104">This article provides examples of how to find an element whose attribute has a specific value.</span></span>

## <a name="example-find-an-element-whose-attribute-has-a-specific-value"></a><span data-ttu-id="fe6e2-105">範例：尋找其屬性具有特定值的元素</span><span class="sxs-lookup"><span data-stu-id="fe6e2-105">Example: Find an element whose attribute has a specific value</span></span>

<span data-ttu-id="fe6e2-106">下列範例顯示如何尋找 `Address` 具有 `Type` 值為 "帳單" 之屬性的專案。</span><span class="sxs-lookup"><span data-stu-id="fe6e2-106">The following example shows how to find the `Address` element that has a `Type` attribute with a value of "Billing".</span></span> <span data-ttu-id="fe6e2-107">此範例會使用 XML [檔範例 xml 檔：典型的採購訂單](sample-xml-file-typical-purchase-order.md)。</span><span class="sxs-lookup"><span data-stu-id="fe6e2-107">The example uses XML document [Sample XML file: Typical purchase order](sample-xml-file-typical-purchase-order.md).</span></span>

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

<span data-ttu-id="fe6e2-108">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="fe6e2-108">This example produces the following output:</span></span>

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

## <a name="example-find-an-element-in-xml-thats-in-a-namespace"></a><span data-ttu-id="fe6e2-109">範例：在命名空間中尋找 XML 內的元素</span><span class="sxs-lookup"><span data-stu-id="fe6e2-109">Example: Find an element in XML that's in a namespace</span></span>

<span data-ttu-id="fe6e2-110">下列範例顯示相同的查詢，但針對命名空間中的 XML。</span><span class="sxs-lookup"><span data-stu-id="fe6e2-110">The following example shows the same query, but for XML that's in a namespace.</span></span> <span data-ttu-id="fe6e2-111">它使用 XML [檔範例 xml 檔：命名空間中的典型採購訂單](sample-xml-file-typical-purchase-order-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="fe6e2-111">It uses XML document [Sample XML file: typical purchase order in a namespace](sample-xml-file-typical-purchase-order-namespace.md).</span></span>

<span data-ttu-id="fe6e2-112">如需命名空間的詳細資訊，請參閱 [命名空間總覽](namespaces-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="fe6e2-112">For more information about namespaces, see [Namespaces overview](namespaces-overview.md).</span></span>

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

<span data-ttu-id="fe6e2-113">此範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="fe6e2-113">This example produces the following output::</span></span>

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

## <a name="see-also"></a><span data-ttu-id="fe6e2-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe6e2-114">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="fe6e2-115">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="fe6e2-115">Standard Query Operators Overview (C#)</span></span>](../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="fe6e2-116">投射作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="fe6e2-116">Projection Operations (C#)</span></span>](../../csharp/programming-guide/concepts/linq/projection-operations.md)
- [<span data-ttu-id="fe6e2-117">基本查詢 (LINQ to XML)  (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="fe6e2-117">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
- [<span data-ttu-id="fe6e2-118">標準查詢運算子概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fe6e2-118">Standard Query Operators Overview (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="fe6e2-119">投影作業 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="fe6e2-119">Projection Operations (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
