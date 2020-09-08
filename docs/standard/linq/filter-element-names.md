---
title: 如何篩選元素名稱-LINQ to XML
description: 瞭解如何在呼叫會傳回 System.xml.linq.xelement> 之 IEnumerable 的方法時，篩選元素名稱。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 1849fb03-f075-421f-863c-e8fb32773cdf
ms.openlocfilehash: 1f831fe0008c94b3956e93f3ced7176d8c0bf34e
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552105"
---
# <a name="how-to-filter-on-element-names-linq-to-xml"></a><span data-ttu-id="53ca4-103">如何篩選項目名稱 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="53ca4-103">How to filter on element names (LINQ to XML)</span></span>

<span data-ttu-id="53ca4-104">當您呼叫可傳回 <xref:System.Collections.Generic.IEnumerable%601> 之 <xref:System.Xml.Linq.XElement> 的其中一個方法時，您可以篩選項目名稱。</span><span class="sxs-lookup"><span data-stu-id="53ca4-104">When you call one of the methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, you can filter on the element name.</span></span>

## <a name="example-retrieve-descendants-filtered-to-a-specified-name"></a><span data-ttu-id="53ca4-105">範例：取出已篩選為指定名稱的子系</span><span class="sxs-lookup"><span data-stu-id="53ca4-105">Example: Retrieve descendants filtered to a specified name</span></span>

<span data-ttu-id="53ca4-106">此範例會抓取已篩選成隻包含具有指定名稱之子系的子系集合。</span><span class="sxs-lookup"><span data-stu-id="53ca4-106">This example retrieves a collection of descendants that's filtered to contain only descendants with the specified name.</span></span>

<span data-ttu-id="53ca4-107">這個範例會使用 XML [檔範例 xml 檔：典型的採購訂單](sample-xml-file-typical-purchase-order.md)。</span><span class="sxs-lookup"><span data-stu-id="53ca4-107">This example uses XML document [Sample XML file: Typical purchase order](sample-xml-file-typical-purchase-order.md).</span></span>

```csharp
XElement po = XElement.Load("PurchaseOrder.xml");
IEnumerable<XElement> items =
    from el in po.Descendants("ProductName")
    select el;
foreach(XElement prdName in items)
    Console.WriteLine(prdName.Name + ":" + (string) prdName);
```

```vb
Dim po As XElement = XElement.Load("PurchaseOrder.xml")
Dim items As IEnumerable(Of XElement) = _
    From el In po...<ProductName> _
    Select el
For Each prdName As XElement In items
    Console.WriteLine(prdName.Name.ToString & ":" & prdName.Value)
Next
```

<span data-ttu-id="53ca4-108">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="53ca4-108">This example produces the following output:</span></span>

```output
ProductName:Lawnmower
ProductName:Baby Monitor
```

<span data-ttu-id="53ca4-109">其他傳回 <xref:System.Collections.Generic.IEnumerable%601> 集合之 <xref:System.Xml.Linq.XElement> 的方法都依照相同的模式。</span><span class="sxs-lookup"><span data-stu-id="53ca4-109">The other methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> collections follow the same pattern.</span></span> <span data-ttu-id="53ca4-110">它們的簽章類似於 <xref:System.Xml.Linq.XContainer.Elements%2A> 及 <xref:System.Xml.Linq.XContainer.Descendants%2A>。</span><span class="sxs-lookup"><span data-stu-id="53ca4-110">Their signatures are similar to <xref:System.Xml.Linq.XContainer.Elements%2A> and <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span></span> <span data-ttu-id="53ca4-111">下列是具有類似方法簽章之方法的完整清單：</span><span class="sxs-lookup"><span data-stu-id="53ca4-111">The following is the complete list of methods that have similar method signatures:</span></span>

- <xref:System.Xml.Linq.XNode.Ancestors%2A>
- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>
- <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>
- <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>
- <xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A>

## <a name="example-retrieve-from-xml-thats-in-a-namespace"></a><span data-ttu-id="53ca4-112">範例：從命名空間中的 XML 取得</span><span class="sxs-lookup"><span data-stu-id="53ca4-112">Example: Retrieve from XML that's in a namespace</span></span>

<span data-ttu-id="53ca4-113">下列範例顯示命名空間中的相同 XML 查詢。</span><span class="sxs-lookup"><span data-stu-id="53ca4-113">The following example shows the same query for XML that's in a namespace.</span></span> <span data-ttu-id="53ca4-114">如需詳細資訊，請參閱 [命名空間總覽](namespaces-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="53ca4-114">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

<span data-ttu-id="53ca4-115">此範例會使用 XML [檔範例 xml 檔：命名空間中的典型採購訂單](sample-xml-file-typical-purchase-order-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="53ca4-115">The example uses XML document [Sample XML file: Typical purchase order in a namespace](sample-xml-file-typical-purchase-order-namespace.md).</span></span>

```csharp
XNamespace aw = "http://www.adventure-works.com";
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");
IEnumerable<XElement> items =
    from el in po.Descendants(aw + "ProductName")
    select el;
foreach (XElement prdName in items)
    Console.WriteLine(prdName.Name + ":" + (string)prdName);
```

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim po As XElement = XElement.Load("PurchaseOrderInNamespace.xml")
        Dim items As IEnumerable(Of XElement) = _
            From el In po...<aw:ProductName> _
            Select el
        For Each prdName As XElement In items
            Console.WriteLine(prdName.Name.ToString & ":" & prdName.Value)
        Next
    End Sub
End Module
```

<span data-ttu-id="53ca4-116">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="53ca4-116">This example produces the following output:</span></span>

```output
{http://www.adventure-works.com}ProductName:Lawnmower
{http://www.adventure-works.com}ProductName:Baby Monitor
```

## <a name="see-also"></a><span data-ttu-id="53ca4-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53ca4-117">See also</span></span>

- [<span data-ttu-id="53ca4-118">LINQ to XML 軸總覽</span><span class="sxs-lookup"><span data-stu-id="53ca4-118">LINQ to XML axes overview</span></span>](linq-xml-axes-overview.md)
