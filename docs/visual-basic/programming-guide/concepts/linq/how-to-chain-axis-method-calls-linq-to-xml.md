---
title: "如何︰ 鏈結軸心方法呼叫 (LINQ to XML) (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: e4e22942-39bd-460f-b3c0-9f09e53d3aa9
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: a32f50ce8a92fa22d9627a1510a4b3ec1087364e
ms.openlocfilehash: 4997f7e91f968f080c22ca9d3a204c748758f832
ms.contentlocale: zh-tw
ms.lasthandoff: 06/01/2017


---
# <a name="how-to-chain-axis-method-calls-linq-to-xml-visual-basic"></a><span data-ttu-id="913c6-102">如何︰ 鏈結軸心方法呼叫 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="913c6-102">How to: Chain Axis Method Calls (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="913c6-103">您在程式碼中使用的常見模式為呼叫座標軸方法，然後呼叫其中一個擴充方法座標軸。</span><span class="sxs-lookup"><span data-stu-id="913c6-103">A common pattern that you will use in your code is to call an axis method, then call one of the extension method axes.</span></span>  
  
 <span data-ttu-id="913c6-104">有兩個座標軸名稱`Elements`可傳回集合的項目︰<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName>方法和<xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName>方法。</xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName> </xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="913c6-104">There are two axes with the name of `Elements` that return a collection of elements: the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName> method and the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName> method.</span></span> <span data-ttu-id="913c6-105">您可以結合這兩個座標軸，在樹狀的指定深度，尋找指定之名稱的所有項目。</span><span class="sxs-lookup"><span data-stu-id="913c6-105">You can combine these two axes to find all elements of a specified name at a given depth in the tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="913c6-106">範例</span><span class="sxs-lookup"><span data-stu-id="913c6-106">Example</span></span>  
 <span data-ttu-id="913c6-107">這個範例會使用<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName>和<xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName>找到所有`Name`項目的所有`Address`項目的所有`PurchaseOrder`項目。</xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName> </xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="913c6-107">This example uses <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName> and <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName> to find all `Name` elements in all `Address` elements in all `PurchaseOrder` elements.</span></span>  
  
 <span data-ttu-id="913c6-108">這個範例會使用下列 XML 文件︰[範例 XML 檔︰ 多份採購訂單 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="913c6-108">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim purchaseOrders As XElement = XElement.Load("PurchaseOrders.xml")  
Dim names As IEnumerable(Of XElement) = _  
    From el In purchaseOrders.<PurchaseOrder>.<Address>.<Name> _  
    Select el  
For Each e As XElement In names  
    Console.WriteLine(e)  
Next  
```  
  
 <span data-ttu-id="913c6-109">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="913c6-109">This example produces the following output:</span></span>  
  
```xml  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
 <span data-ttu-id="913c6-110">這是因為其中一個實作的`Elements`軸是當做擴充方法上<xref:System.Collections.Generic.IEnumerable%601>的<xref:System.Xml.Linq.XContainer>。</xref:System.Xml.Linq.XContainer> </xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="913c6-110">This works because one of the implementations of the `Elements` axis is as an extension method on <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="913c6-111"><xref:System.Xml.Linq.XElement>衍生自<xref:System.Xml.Linq.XContainer>，因此您可以呼叫<xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName>方法呼叫的結果，在<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName>方法。</xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName> </xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName> </xref:System.Xml.Linq.XContainer></xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="913c6-111"><xref:System.Xml.Linq.XElement> derives from <xref:System.Xml.Linq.XContainer>, so you can call the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName> method on the results of a call to the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="913c6-112">範例</span><span class="sxs-lookup"><span data-stu-id="913c6-112">Example</span></span>  
 <span data-ttu-id="913c6-113">有時候您會想要在可能有也可能沒有介入祖系時，擷取特定項目深度的所有項目。</span><span class="sxs-lookup"><span data-stu-id="913c6-113">Sometimes you want to retrieve all elements at a particular element depth when there might or might not be intervening ancestors.</span></span> <span data-ttu-id="913c6-114">例如，在下列文件中，您可能想要擷取 `ConfigParameter` 項目子系的所有 `Customer` 項目，但不是 `ConfigParameter` 項目子系的 `Root`。</span><span class="sxs-lookup"><span data-stu-id="913c6-114">For example, in the following document, you might want to retrieve all the `ConfigParameter` elements that are children of the `Customer` element, but not the `ConfigParameter` that is a child of the `Root` element.</span></span>  
  
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
  
 <span data-ttu-id="913c6-115">若要這樣做，您可以使用<xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName>座標軸，如下︰</xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="913c6-115">To do this, you can use the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName> axis, as follows:</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("Irregular.xml")  
Dim configParameters As IEnumerable(Of XElement) = _  
    root.<Customer>.<Config>.<ConfigParameter>  
For Each cp As XElement In configParameters  
    Console.WriteLine(cp)  
Next  
```  
  
 <span data-ttu-id="913c6-116">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="913c6-116">This example produces the following output:</span></span>  
  
```xml  
<ConfigParameter>FirstConfigParameter</ConfigParameter>  
<ConfigParameter>SecondConfigParameter</ConfigParameter>  
```  
  
## <a name="example"></a><span data-ttu-id="913c6-117">範例</span><span class="sxs-lookup"><span data-stu-id="913c6-117">Example</span></span>  
 <span data-ttu-id="913c6-118">下列範例顯示命名空間中之 XML 的相同技術。</span><span class="sxs-lookup"><span data-stu-id="913c6-118">The following example shows the same technique for XML that is in a namespace.</span></span> <span data-ttu-id="913c6-119">如需詳細資訊，請參閱[處理 XML 命名空間 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)。</span><span class="sxs-lookup"><span data-stu-id="913c6-119">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="913c6-120">這個範例會使用下列 XML 文件︰[範例 XML 檔︰ 命名空間中的多個採購訂單](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="913c6-120">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="913c6-121">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="913c6-121">This example produces the following output:</span></span>  
  
```xml  
<aw:Name xmlns:aw="http://www.adventure-works.com">Ellen Adams</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Tai Yee</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
```  
  
## <a name="see-also"></a><span data-ttu-id="913c6-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="913c6-122">See Also</span></span>  
 [<span data-ttu-id="913c6-123">LINQ to XML 軸心方法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="913c6-123">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
