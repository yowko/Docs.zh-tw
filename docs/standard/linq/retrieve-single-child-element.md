---
title: 如何取出單一子項目-LINQ to XML
description: '取出具有指定名稱的第一個子項目。 您可以在 c # 中使用 System.xml.linq.xcontainer.elements，並在 Visual Basic 中使用陣列索引子標記法。'
ms.date: 07/20/2015
ms.assetid: ce37db9e-76fa-46eb-b4cc-e8f32d22ad90
ms.openlocfilehash: e557e82e4e5891d6890a0efb4973796050b75349
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552704"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml"></a><span data-ttu-id="9cde0-104">如何擷取單一子元素 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="9cde0-104">How to retrieve a single child element (LINQ to XML)</span></span>

<span data-ttu-id="9cde0-105">本文說明如何取出單一子項目，也就是具有指定名稱的第一個子專案。</span><span class="sxs-lookup"><span data-stu-id="9cde0-105">This article explains how to retrieve a single child element, the first child element that has a specified name.</span></span> <span data-ttu-id="9cde0-106">在 c # 中，您可以使用方法來完成這項作業 <xref:System.Xml.Linq.XContainer.Element%2A> 。</span><span class="sxs-lookup"><span data-stu-id="9cde0-106">In C# you do this with the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span> <span data-ttu-id="9cde0-107">在 Visual Basic 您可以使用陣列索引子標記法來進行。</span><span class="sxs-lookup"><span data-stu-id="9cde0-107">In Visual Basic you do it with array indexer notation.</span></span>

## <a name="example-retrieve-the-first-element-that-has-a-specified-name"></a><span data-ttu-id="9cde0-108">範例：取出具有指定名稱的第一個元素</span><span class="sxs-lookup"><span data-stu-id="9cde0-108">Example: Retrieve the first element that has a specified name</span></span>

<span data-ttu-id="9cde0-109">下列範例會 `DeliveryNotes` 從範例 xml 檔中的 xml 檔抓取第一個元素 [：典型的採購訂單](sample-xml-file-typical-purchase-order.md)。</span><span class="sxs-lookup"><span data-stu-id="9cde0-109">The following example retrieves the first `DeliveryNotes` element from the XML document in [Sample XML file: Typical purchase order](sample-xml-file-typical-purchase-order.md).</span></span>

```csharp
XElement po = XElement.Load("PurchaseOrder.xml");
XElement e = po.Element("DeliveryNotes");
Console.WriteLine(e);
```

```vb
Dim po As XElement = XElement.Load("PurchaseOrder.xml")
Dim e As XElement = po.<DeliveryNotes>(0)
Console.WriteLine(e)
```

<span data-ttu-id="9cde0-110">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="9cde0-110">This example produces the following output:</span></span>

```xml
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>
```

## <a name="example-retrieve-from-xml-thats-in-a-namespace"></a><span data-ttu-id="9cde0-111">範例：從命名空間中的 XML 取得</span><span class="sxs-lookup"><span data-stu-id="9cde0-111">Example: Retrieve from XML that's in a namespace</span></span>

<span data-ttu-id="9cde0-112">下列範例會執行與上述範例相同的動作，但針對命名空間中的 XML 執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="9cde0-112">The following example does the same thing as the one above, but for XML that's in a namespace.</span></span> <span data-ttu-id="9cde0-113">它會使用 XML [檔範例 xml 檔：命名空間中的典型採購訂單](sample-xml-file-typical-purchase-order-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="9cde0-113">It uses the XML document [Sample XML file: Typical purchase order in a namespace](sample-xml-file-typical-purchase-order-namespace.md).</span></span> <span data-ttu-id="9cde0-114">如需命名空間的詳細資訊，請參閱 [命名空間總覽](namespaces-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="9cde0-114">For more information about namespaces, see [Namespaces overview](namespaces-overview.md).</span></span>

```csharp
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");
XNamespace aw = "http://www.adventure-works.com";
XElement e = po.Element(aw + "DeliveryNotes");
Console.WriteLine(e);
```

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim po As XElement = XElement.Load("PurchaseOrderInNamespace.xml")
        Dim e As XElement = po.<aw:DeliveryNotes>(0)
        Console.WriteLine(e)
    End Sub
End Module
```

<span data-ttu-id="9cde0-115">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="9cde0-115">This example produces the following output:</span></span>

```xml
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>
```

## <a name="see-also"></a><span data-ttu-id="9cde0-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9cde0-116">See also</span></span>

- [<span data-ttu-id="9cde0-117">LINQ to XML 軸總覽</span><span class="sxs-lookup"><span data-stu-id="9cde0-117">LINQ to XML axes overview</span></span>](linq-xml-axes-overview.md)
