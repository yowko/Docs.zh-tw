---
title: 如何連鎖座標軸方法呼叫-LINQ to XML
description: 瞭解如何使用 System.xml.linq.xcontainer.elements. elements 和 Extensions. Elements 方法，在樹狀結構中的給定深度尋找指定名稱的所有元素。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 067e6da2-ee32-486d-803c-e611b328e39a
ms.openlocfilehash: 23d3b5a3dacbc56a570a92178cb8e28482907ca1
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552272"
---
# <a name="how-to-chain-axis-method-calls-linq-to-xml"></a><span data-ttu-id="f74c5-103">如何鏈結軸方法呼叫 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="f74c5-103">How to chain axis method calls (LINQ to XML)</span></span>

<span data-ttu-id="f74c5-104">您在程式碼中使用的常見模式為呼叫座標軸方法，然後呼叫其中一個擴充方法座標軸。</span><span class="sxs-lookup"><span data-stu-id="f74c5-104">A common pattern that you will use in your code is to call an axis method, then call one of the extension method axes.</span></span>

<span data-ttu-id="f74c5-105">有兩個座標軸可傳回項目集合而且具有 `Elements` 名稱：<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> 方法和 <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="f74c5-105">There are two axes with the name of `Elements` that return a collection of elements: the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method and the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="f74c5-106">您可以結合這兩個座標軸，在樹狀的指定深度，尋找指定之名稱的所有項目。</span><span class="sxs-lookup"><span data-stu-id="f74c5-106">You can combine these two axes to find all elements of a specified name at a given depth in the tree.</span></span>

## <a name="example-retrieve-all-name-elements"></a><span data-ttu-id="f74c5-107">範例：取出所有名稱元素</span><span class="sxs-lookup"><span data-stu-id="f74c5-107">Example: Retrieve all name elements</span></span>

<span data-ttu-id="f74c5-108">這個範例會使用 <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> 和 <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> 來取得 `Name` `Address` 所有專案中所有專案的所有專案 `PurchaseOrder` 。</span><span class="sxs-lookup"><span data-stu-id="f74c5-108">This example uses <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> and <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> to retrieve all `Name` elements in all `Address` elements in all `PurchaseOrder` elements.</span></span>

<span data-ttu-id="f74c5-109">此範例會使用 XML [檔範例 xml 檔：多份採購訂單](sample-xml-file-multiple-purchase-orders.md)。</span><span class="sxs-lookup"><span data-stu-id="f74c5-109">This example uses XML document [Sample XML file: Multiple purchase orders](sample-xml-file-multiple-purchase-orders.md).</span></span>

```csharp
XElement purchaseOrders = XElement.Load("PurchaseOrders.xml");
IEnumerable<XElement> names =
    from el in purchaseOrders
        .Elements("PurchaseOrder")
        .Elements("Address")
        .Elements("Name")
    select el;
foreach (XElement e in names)
    Console.WriteLine(e);
```

```vb
Dim purchaseOrders As XElement = XElement.Load("PurchaseOrders.xml")
Dim names As IEnumerable(Of XElement) = _
    From el In purchaseOrders.<PurchaseOrder>.<Address>.<Name> _
    Select el
For Each e As XElement In names
    Console.WriteLine(e)
Next
```

<span data-ttu-id="f74c5-110">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="f74c5-110">This example produces the following output:</span></span>

```xml
<Name>Ellen Adams</Name>
<Name>Tai Yee</Name>
<Name>Cristian Osorio</Name>
<Name>Cristian Osorio</Name>
<Name>Jessica Arnold</Name>
<Name>Jessica Arnold</Name>
```

<span data-ttu-id="f74c5-111">之所以可以這樣做，是因為 `Elements` 軸的其中一個實作是 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XContainer>。</span><span class="sxs-lookup"><span data-stu-id="f74c5-111">This works because one of the implementations of the `Elements` axis is as an extension method on <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="f74c5-112"><xref:System.Xml.Linq.XElement> 衍生自 <xref:System.Xml.Linq.XContainer>，所以可以呼叫在呼叫結果上的 <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> 方法至 <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="f74c5-112"><xref:System.Xml.Linq.XElement> derives from <xref:System.Xml.Linq.XContainer>, so you can call the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method on the results of a call to the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method.</span></span>

## <a name="example-retrieve-all-elements-at-a-particular-depth"></a><span data-ttu-id="f74c5-113">範例：取得特定深度的所有元素</span><span class="sxs-lookup"><span data-stu-id="f74c5-113">Example: Retrieve all elements at a particular depth</span></span>

<span data-ttu-id="f74c5-114">有時您會想要在沒有中間祖系時，取得特定專案深度的所有元素。</span><span class="sxs-lookup"><span data-stu-id="f74c5-114">Sometimes you want to retrieve all elements at a particular element depth when there may not be intervening ancestors.</span></span> <span data-ttu-id="f74c5-115">例如，在下列檔中，您可能會想要取出元素子系的所有專案 `ConfigParameter` `Customer` ，而不是專案的 `ConfigParameter` 子系 `Root` 。</span><span class="sxs-lookup"><span data-stu-id="f74c5-115">For example, in the following document, you might want to retrieve all the `ConfigParameter` elements that are children of the `Customer` element, but not the `ConfigParameter` that's a child of the `Root` element.</span></span>

```xml
<Root>
  <ConfigParameter>RootConfigParameter</ConfigParameter>
  <Customer>
    <Name>Frank</Name>
    <Config>
      <ConfigParameter>FirstConfigParameter</ConfigParameter>
    </Config>
  </Customer>
  <Customer>
    <Name>Bob</Name>
    <!--This customer doesn't have a Config element-->
  </Customer>
  <Customer>
    <Name>Bill</Name>
    <Config>
      <ConfigParameter>SecondConfigParameter</ConfigParameter>
    </Config>
  </Customer>
</Root>
```

 <span data-ttu-id="f74c5-116">如果要這樣做，您可以使用 <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> 座標軸，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f74c5-116">To do this, you can use the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> axis, as follows:</span></span>

```csharp
XElement root = XElement.Load("Irregular.xml");
IEnumerable<XElement> configParameters =
    root.Elements("Customer").Elements("Config").
    Elements("ConfigParameter");
foreach (XElement cp in configParameters)
    Console.WriteLine(cp);
```

```vb
Dim root As XElement = XElement.Load("Irregular.xml")
Dim configParameters As IEnumerable(Of XElement) = _
    root.<Customer>.<Config>.<ConfigParameter>
For Each cp As XElement In configParameters
    Console.WriteLine(cp)
Next
```

<span data-ttu-id="f74c5-117">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="f74c5-117">This example produces the following output:</span></span>

```xml
<ConfigParameter>FirstConfigParameter</ConfigParameter>
<ConfigParameter>SecondConfigParameter</ConfigParameter>
```

## <a name="example-retrieve-elements-for-xml-thats-in-a-namespace"></a><span data-ttu-id="f74c5-118">範例：取出位於命名空間中的 XML 元素</span><span class="sxs-lookup"><span data-stu-id="f74c5-118">Example: Retrieve elements for XML that's in a namespace</span></span>

<span data-ttu-id="f74c5-119">下列範例顯示命名空間中的 XML 相同技術。</span><span class="sxs-lookup"><span data-stu-id="f74c5-119">The following example shows the same technique for XML that's in a namespace.</span></span> <span data-ttu-id="f74c5-120">如需詳細資訊，請參閱 [命名空間總覽](namespaces-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="f74c5-120">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

<span data-ttu-id="f74c5-121">此範例會使用 XML [檔範例 xml 檔：命名空間中的多個](sample-xml-file-multiple-purchase-orders-namespace.md)訂單。</span><span class="sxs-lookup"><span data-stu-id="f74c5-121">This example uses XML document [Sample XML file: Multiple purchase orders in a namespace](sample-xml-file-multiple-purchase-orders-namespace.md).</span></span>

```csharp
XNamespace aw = "http://www.adventure-works.com";
XElement purchaseOrders = XElement.Load("PurchaseOrdersInNamespace.xml");
IEnumerable<XElement> names =
    from el in purchaseOrders
        .Elements(aw + "PurchaseOrder")
        .Elements(aw + "Address")
        .Elements(aw + "Name")
    select el;
foreach (XElement e in names)
    Console.WriteLine(e);
```

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim purchaseOrders As XElement = XElement.Load("PurchaseOrdersInNamespace.xml")
        Dim names As IEnumerable(Of XElement) = _
            From el In purchaseOrders.<aw:PurchaseOrder>.<aw:Address>.<aw:Name> _
            Select el
        For Each e As XElement In names
            Console.WriteLine(e)
        Next
    End Sub
End Module
```

<span data-ttu-id="f74c5-122">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="f74c5-122">This example produces the following output:</span></span>

```xml
<aw:Name xmlns:aw="http://www.adventure-works.com">Ellen Adams</aw:Name>
<aw:Name xmlns:aw="http://www.adventure-works.com">Tai Yee</aw:Name>
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>
```

## <a name="see-also"></a><span data-ttu-id="f74c5-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f74c5-123">See also</span></span>

- [<span data-ttu-id="f74c5-124">LINQ to XML 軸總覽</span><span class="sxs-lookup"><span data-stu-id="f74c5-124">LINQ to XML axes overview</span></span>](linq-xml-axes-overview.md)
