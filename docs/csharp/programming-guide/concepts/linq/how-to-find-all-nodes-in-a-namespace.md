---
title: 如何查找命名空間 （C#） 中的所有節點
ms.date: 07/20/2015
ms.assetid: 3a38b913-a53e-4d0e-a19d-8782bffd3364
ms.openlocfilehash: 408f4207798720428d0dd3821d33fd3edf2f897e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141191"
---
# <a name="how-to-find-all-nodes-in-a-namespace-c"></a><span data-ttu-id="9a72b-102">如何查找命名空間 （C#） 中的所有節點</span><span class="sxs-lookup"><span data-stu-id="9a72b-102">How to find all nodes in a namespace (C#)</span></span>
<span data-ttu-id="9a72b-103">您可以在每個項目或屬性的命名空間上篩選，尋找該特定命名空間中的所有節點。</span><span class="sxs-lookup"><span data-stu-id="9a72b-103">You can filter on the namespace of each element or attribute to find all nodes in that particular namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a72b-104">範例</span><span class="sxs-lookup"><span data-stu-id="9a72b-104">Example</span></span>  
 <span data-ttu-id="9a72b-105">下列範例會使用兩個命名空間建立 XML 樹狀。</span><span class="sxs-lookup"><span data-stu-id="9a72b-105">The following example creates an XML tree with two namespaces.</span></span> <span data-ttu-id="9a72b-106">接著，它會逐一查看樹狀結構，並在這些其中一個命名空間中，列印所有項目和屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="9a72b-106">It then iterates through the tree and prints the names of all the elements and attributes in one of those namespaces.</span></span>  
  
```csharp  
string markup = @"<aw:Root xmlns:aw='http://www.adventure-works.com' xmlns:fc='www.fourthcoffee.com'>  
  <fc:Child1>abc</fc:Child1>  
  <fc:Child2>def</fc:Child2>  
  <aw:Child3>ghi</aw:Child3>  
  <fc:Child4>  
    <fc:GrandChild1>jkl</fc:GrandChild1>  
    <aw:GrandChild2>mno</aw:GrandChild2>  
  </fc:Child4>  
</aw:Root>";  
XElement xmlTree = XElement.Parse(markup);  
Console.WriteLine("Nodes in the http://www.adventure-works.com namespace");  
IEnumerable<XElement> awElements =  
    from el in xmlTree.Descendants()  
    where el.Name.Namespace == "http://www.adventure-works.com"  
    select el;  
foreach (XElement el in awElements)  
    Console.WriteLine(el.Name.ToString());  
```  
  
 <span data-ttu-id="9a72b-107">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="9a72b-107">This code produces the following output:</span></span>  
  
```output  
Nodes in the http://www.adventure-works.com namespace  
{http://www.adventure-works.com}Child3  
{http://www.adventure-works.com}GrandChild2  
```  
  
## <a name="example"></a><span data-ttu-id="9a72b-108">範例</span><span class="sxs-lookup"><span data-stu-id="9a72b-108">Example</span></span>  
 <span data-ttu-id="9a72b-109">下列查詢所存取的 XML 檔案包含兩種不同命名空間中的採購訂單。</span><span class="sxs-lookup"><span data-stu-id="9a72b-109">The XML file accessed by the following query contains purchase orders in two different namespaces.</span></span> <span data-ttu-id="9a72b-110">此查詢只會使用其中一個命名空間中的項目建立新的樹狀。</span><span class="sxs-lookup"><span data-stu-id="9a72b-110">The query creates a new tree with just the elements in one of the namespaces.</span></span>  
  
 <span data-ttu-id="9a72b-111">此範例使用下列 XML 文件︰[範例 XML 檔：合併的採購訂單](./sample-xml-file-consolidated-purchase-orders.md)。</span><span class="sxs-lookup"><span data-stu-id="9a72b-111">This example uses the following XML document: [Sample XML File: Consolidated Purchase Orders](./sample-xml-file-consolidated-purchase-orders.md).</span></span>  
  
```csharp  
XDocument cpo = XDocument.Load("ConsolidatedPurchaseOrders.xml");  
XNamespace aw = "http://www.adventure-works.com";  
XElement newTree = new XElement("Root",  
    from el in cpo.Root.Elements()  
    where el.Name.Namespace == aw  
    select el  
);  
Console.WriteLine(newTree);  
```  
  
 <span data-ttu-id="9a72b-112">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="9a72b-112">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <aw:PurchaseOrder PONumber="11223" Date="2000-01-15" xmlns:aw="http://www.adventure-works.com">  
    <aw:ShippingAddress>  
      <aw:Name>Chris Preston</aw:Name>  
      <aw:Street>123 Main St.</aw:Street>  
      <aw:City>Seattle</aw:City>  
      <aw:State>WA</aw:State>  
      <aw:Zip>98113</aw:Zip>  
      <aw:Country>USA</aw:Country>  
    </aw:ShippingAddress>  
    <aw:BillingAddress>  
      <aw:Name>Chris Preston</aw:Name>  
      <aw:Street>123 Main St.</aw:Street>  
      <aw:City>Seattle</aw:City>  
      <aw:State>WA</aw:State>  
      <aw:Zip>98113</aw:Zip>  
      <aw:Country>USA</aw:Country>  
    </aw:BillingAddress>  
    <aw:DeliveryInstructions>Ship only complete order.</aw:DeliveryInstructions>  
    <aw:Item PartNum="LIT-01">  
      <aw:ProductID>Litware Networking Card</aw:ProductID>  
      <aw:Qty>1</aw:Qty>  
      <aw:Price>20.99</aw:Price>  
    </aw:Item>  
    <aw:Item PartNum="LIT-25">  
      <aw:ProductID>Litware 17in LCD Monitor</aw:ProductID>  
      <aw:Qty>1</aw:Qty>  
      <aw:Price>199.99</aw:Price>  
    </aw:Item>  
  </aw:PurchaseOrder>  
</Root>  
```  
