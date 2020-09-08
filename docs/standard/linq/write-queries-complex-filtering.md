---
title: 如何撰寫具有複雜篩選的查詢-LINQ to XML
description: 有時候您會想要利用複雜篩選撰寫 LINQ to XML 查詢。 例如，您可能必須尋找其子項目包含特定名稱和值的所有項目。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 4065d901-cf89-4e47-8bf9-abb65acfb003
ms.openlocfilehash: c5e7f812364e7e96e3a4b8f5515d07a3524ec979
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552808"
---
# <a name="how-to-write-queries-with-complex-filtering-linq-to-xml"></a><span data-ttu-id="2d7c4-104">如何使用複雜的篩選撰寫查詢 (LINQ to XML) </span><span class="sxs-lookup"><span data-stu-id="2d7c4-104">How to write queries with complex filtering (LINQ to XML)</span></span>

<span data-ttu-id="2d7c4-105">有時候您會想要利用複雜篩選撰寫 LINQ to XML 查詢。</span><span class="sxs-lookup"><span data-stu-id="2d7c4-105">Sometimes you want to write LINQ to XML queries with complex filters.</span></span> <span data-ttu-id="2d7c4-106">例如，您可能必須尋找其子項目包含特定名稱和值的所有項目。</span><span class="sxs-lookup"><span data-stu-id="2d7c4-106">For example, you might have to find all elements that have a child element with a particular name and value.</span></span> <span data-ttu-id="2d7c4-107">本文提供撰寫複雜篩選查詢的範例。</span><span class="sxs-lookup"><span data-stu-id="2d7c4-107">This article gives an example of writing a query with complex filtering.</span></span>

## <a name="example-find-with-a-nested-query-in-the-where-clause"></a><span data-ttu-id="2d7c4-108">範例：在子句中使用巢狀查詢來尋找 `Where`</span><span class="sxs-lookup"><span data-stu-id="2d7c4-108">Example: Find with a nested query in the `Where` clause</span></span>

<span data-ttu-id="2d7c4-109">這個範例示範如何尋找 `PurchaseOrder` 具有下列專案的所有元素：</span><span class="sxs-lookup"><span data-stu-id="2d7c4-109">This example shows how to find all `PurchaseOrder` elements that have:</span></span>

- <span data-ttu-id="2d7c4-110">`Address`其屬性等於「出貨」的子專案 `Type` 。</span><span class="sxs-lookup"><span data-stu-id="2d7c4-110">A child `Address` element whose `Type` attribute equals "Shipping".</span></span>
- <span data-ttu-id="2d7c4-111">`State`等於 "NY" 的子項目。</span><span class="sxs-lookup"><span data-stu-id="2d7c4-111">A child `State` element that equals "NY".</span></span>

<span data-ttu-id="2d7c4-112">它會在 `Where` 子句中使用巢狀查詢，而且如果集合在其中有任何項目，`Any` 運算子會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="2d7c4-112">It uses a nested query in the `Where` clause, and the `Any` operator returns `true` if the collection has any elements in it.</span></span> <span data-ttu-id="2d7c4-113">此範例會使用 XML [檔範例 xml 檔：多份採購訂單](sample-xml-file-multiple-purchase-orders.md)。</span><span class="sxs-lookup"><span data-stu-id="2d7c4-113">The example uses XML document [Sample XML file: Multiple purchase orders](sample-xml-file-multiple-purchase-orders.md).</span></span>

<span data-ttu-id="2d7c4-114">如需有關運算子的詳細資訊 `Any` ，請參閱 [數量詞作業 (c # ) ](../../../docs/csharp/programming-guide/concepts/linq/quantifier-operations.md) 和 [數量詞作業 (Visual Basic) ](../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="2d7c4-114">For more information about the `Any` operator, see [Quantifier Operations (C#)](../../../docs/csharp/programming-guide/concepts/linq/quantifier-operations.md) and [Quantifier Operations (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md).</span></span>

```csharp
XElement root = XElement.Load("PurchaseOrders.xml");
IEnumerable<XElement> purchaseOrders =
    from el in root.Elements("PurchaseOrder")
    where
        (from add in el.Elements("Address")
        where
            (string)add.Attribute("Type") == "Shipping" &&
            (string)add.Element("State") == "NY"
        select add)
        .Any()
    select el;
foreach (XElement el in purchaseOrders)
    Console.WriteLine((string)el.Attribute("PurchaseOrderNumber"));
```

```vb
Dim root As XElement = XElement.Load("PurchaseOrders.xml")
Dim purchaseOrders As IEnumerable(Of XElement) = _
    From el In root.<PurchaseOrder> _
    Where _
        (From add In el.<Address> _
        Where _
             add.@Type = "Shipping" And _
             add.<State>.Value = "NY" _
        Select add) _
    .Any() _
    Select el
For Each el As XElement In purchaseOrders
    Console.WriteLine(el.@PurchaseOrderNumber)
Next
```

<span data-ttu-id="2d7c4-115">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="2d7c4-115">This example produces the following output:</span></span>

```output
99505
```

## <a name="example-find-in-xml-thats-in-a-namespace"></a><span data-ttu-id="2d7c4-116">範例：在命名空間中的 XML 中尋找</span><span class="sxs-lookup"><span data-stu-id="2d7c4-116">Example: Find in XML that's in a namespace</span></span>

<span data-ttu-id="2d7c4-117">下列範例顯示與上述相同的查詢，但針對命名空間中的 XML。</span><span class="sxs-lookup"><span data-stu-id="2d7c4-117">The following example shows the same query as above, but for XML that's in a namespace.</span></span> <span data-ttu-id="2d7c4-118">如需詳細資訊，請參閱 [命名空間總覽](namespaces-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="2d7c4-118">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

<span data-ttu-id="2d7c4-119">此範例會使用 XML [檔範例 xml 檔：命名空間中的多個](sample-xml-file-multiple-purchase-orders-namespace.md)訂單。</span><span class="sxs-lookup"><span data-stu-id="2d7c4-119">This example uses XML document [Sample XML file: Multiple purchase orders in a namespace](sample-xml-file-multiple-purchase-orders-namespace.md).</span></span>

```csharp
XElement root = XElement.Load("PurchaseOrdersInNamespace.xml");
XNamespace aw = "http://www.adventure-works.com";
IEnumerable<XElement> purchaseOrders =
    from el in root.Elements(aw + "PurchaseOrder")
    where
        (from add in el.Elements(aw + "Address")
         where
             (string)add.Attribute(aw + "Type") == "Shipping" &&
             (string)add.Element(aw + "State") == "NY"
         select add)
        .Any()
    select el;
foreach (XElement el in purchaseOrders)
    Console.WriteLine((string)el.Attribute(aw + "PurchaseOrderNumber"));
```

```vb
Imports <xmlns:aw='http://www.adventure-works.com'>

Module Module1
    Sub Main()
        Dim root As XElement = XElement.Load("PurchaseOrdersInNamespace.xml")
        Dim purchaseOrders As IEnumerable(Of XElement) = _
            From el In root.<aw:PurchaseOrder> _
            Where _
                (From add In el.<aw:Address> _
                Where _
                     add.@aw:Type = "Shipping" And _
                     add.<aw:State>.Value = "NY" _
                Select add) _
            .Any() _
            Select el
        For Each el As XElement In purchaseOrders
            Console.WriteLine(el.@aw:PurchaseOrderNumber)
        Next
    End Sub
End Module
```

<span data-ttu-id="2d7c4-120">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="2d7c4-120">This example produces the following output:</span></span>

```output
99505
```

## <a name="see-also"></a><span data-ttu-id="2d7c4-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d7c4-121">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="2d7c4-122">投射作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="2d7c4-122">Projection Operations (C#)</span></span>](../../csharp/programming-guide/concepts/linq/projection-operations.md)
- [<span data-ttu-id="2d7c4-123">數量詞作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="2d7c4-123">Quantifier Operations (C#)</span></span>](../../csharp/programming-guide/concepts/linq/quantifier-operations.md)
- [<span data-ttu-id="2d7c4-124">XML 子代軸屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2d7c4-124">XML Child Axis Property (Visual Basic)</span></span>](../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="2d7c4-125">XML 屬性軸屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2d7c4-125">XML Attribute Axis Property (Visual Basic)</span></span>](../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
- [<span data-ttu-id="2d7c4-126">XML Value 屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2d7c4-126">XML Value Property (Visual Basic)</span></span>](../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="2d7c4-127">投影作業 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="2d7c4-127">Projection Operations (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
- [<span data-ttu-id="2d7c4-128">數量詞作業 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="2d7c4-128">Quantifier Operations (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)
