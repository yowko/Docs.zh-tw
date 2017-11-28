---
title: "如何：鏈結軸方法呼叫 (LINQ to XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 067e6da2-ee32-486d-803c-e611b328e39a
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7cf5cb445dc64dfa5f4734ae58e6e921a5a92148
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-chain-axis-method-calls-linq-to-xml-c"></a><span data-ttu-id="2baa8-102">如何：鏈結軸方法呼叫 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="2baa8-102">How to: Chain Axis Method Calls (LINQ to XML) (C#)</span></span>
<span data-ttu-id="2baa8-103">您在程式碼中使用的常見模式為呼叫座標軸方法，然後呼叫其中一個擴充方法座標軸。</span><span class="sxs-lookup"><span data-stu-id="2baa8-103">A common pattern that you will use in your code is to call an axis method, then call one of the extension method axes.</span></span>  
  
 <span data-ttu-id="2baa8-104">有兩個座標軸可傳回項目集合而且具有 `Elements` 名稱：<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> 方法和 <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="2baa8-104">There are two axes with the name of `Elements` that return a collection of elements: the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method and the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="2baa8-105">您可以結合這兩個座標軸，在樹狀的指定深度，尋找指定之名稱的所有項目。</span><span class="sxs-lookup"><span data-stu-id="2baa8-105">You can combine these two axes to find all elements of a specified name at a given depth in the tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2baa8-106">範例</span><span class="sxs-lookup"><span data-stu-id="2baa8-106">Example</span></span>  
 <span data-ttu-id="2baa8-107">這個範例會使用 <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> 和 <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType>，在所有 `Name` 項目的所有 `Address` 項目中，尋找所有 `PurchaseOrder` 項目。</span><span class="sxs-lookup"><span data-stu-id="2baa8-107">This example uses <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> and <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> to find all `Name` elements in all `Address` elements in all `PurchaseOrder` elements.</span></span>  
  
 <span data-ttu-id="2baa8-108">此範例使用下列 XML 文件︰[範例 XML 檔：多份採購單 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="2baa8-108">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="2baa8-109">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="2baa8-109">This example produces the following output:</span></span>  
  
```xml  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
 <span data-ttu-id="2baa8-110">之所以可以這樣做，是因為 `Elements` 軸的其中一個實作是 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XContainer>。</span><span class="sxs-lookup"><span data-stu-id="2baa8-110">This works because one of the implementations of the `Elements` axis is as an extension method on <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="2baa8-111"><xref:System.Xml.Linq.XElement> 衍生自 <xref:System.Xml.Linq.XContainer>，所以可以呼叫在呼叫結果上的 <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> 方法至 <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="2baa8-111"><xref:System.Xml.Linq.XElement> derives from <xref:System.Xml.Linq.XContainer>, so you can call the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method on the results of a call to the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2baa8-112">範例</span><span class="sxs-lookup"><span data-stu-id="2baa8-112">Example</span></span>  
 <span data-ttu-id="2baa8-113">有時候您會想要在可能有也可能沒有介入祖系時，擷取特定項目深度的所有項目。</span><span class="sxs-lookup"><span data-stu-id="2baa8-113">Sometimes you want to retrieve all elements at a particular element depth when there might or might not be intervening ancestors.</span></span> <span data-ttu-id="2baa8-114">例如，在下列文件中，您可能想要擷取 `ConfigParameter` 項目子系的所有 `Customer` 項目，但不是 `ConfigParameter` 項目子系的 `Root`。</span><span class="sxs-lookup"><span data-stu-id="2baa8-114">For example, in the following document, you might want to retrieve all the `ConfigParameter` elements that are children of the `Customer` element, but not the `ConfigParameter` that is a child of the `Root` element.</span></span>  
  
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
  
 <span data-ttu-id="2baa8-115">如果要這樣做，您可以使用 <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> 座標軸，如下所示：</span><span class="sxs-lookup"><span data-stu-id="2baa8-115">To do this, you can use the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> axis, as follows:</span></span>  
  
```csharp  
XElement root = XElement.Load("Irregular.xml");  
IEnumerable<XElement> configParameters =   
    root.Elements("Customer").Elements("Config").  
    Elements("ConfigParameter");  
foreach (XElement cp in configParameters)  
    Console.WriteLine(cp);  
```  
  
 <span data-ttu-id="2baa8-116">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="2baa8-116">This example produces the following output:</span></span>  
  
```xml  
<ConfigParameter>FirstConfigParameter</ConfigParameter>  
<ConfigParameter>SecondConfigParameter</ConfigParameter>  
```  
  
## <a name="example"></a><span data-ttu-id="2baa8-117">範例</span><span class="sxs-lookup"><span data-stu-id="2baa8-117">Example</span></span>  
 <span data-ttu-id="2baa8-118">下列範例顯示命名空間中之 XML 的相同技術。</span><span class="sxs-lookup"><span data-stu-id="2baa8-118">The following example shows the same technique for XML that is in a namespace.</span></span> <span data-ttu-id="2baa8-119">如需詳細資訊，請參閱[處理 XML 命名空間 (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)。</span><span class="sxs-lookup"><span data-stu-id="2baa8-119">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="2baa8-120">此範例使用下列 XML 文件︰[範例 XML 檔：命名空間中的多份採購單](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="2baa8-120">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="2baa8-121">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="2baa8-121">This example produces the following output:</span></span>  
  
```xml  
<aw:Name xmlns:aw="http://www.adventure-works.com">Ellen Adams</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Tai Yee</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2baa8-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2baa8-122">See Also</span></span>  
 [<span data-ttu-id="2baa8-123">LINQ to XML 座標軸 (C#)</span><span class="sxs-lookup"><span data-stu-id="2baa8-123">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
