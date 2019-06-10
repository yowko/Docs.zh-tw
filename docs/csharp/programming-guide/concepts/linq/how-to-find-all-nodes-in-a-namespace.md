---
title: 作法：在命名空間中尋找所有節點 (C#)
ms.date: 07/20/2015
ms.assetid: 3a38b913-a53e-4d0e-a19d-8782bffd3364
ms.openlocfilehash: d94a6c517a76e8ed91f20a17e798ad3806a34a70
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486825"
---
# <a name="how-to-find-all-nodes-in-a-namespace-c"></a><span data-ttu-id="f87a4-102">作法：在命名空間中尋找所有節點 (C#)</span><span class="sxs-lookup"><span data-stu-id="f87a4-102">How to: Find All Nodes in a Namespace (C#)</span></span>
<span data-ttu-id="f87a4-103">您可以在每個項目或屬性的命名空間上篩選，尋找該特定命名空間中的所有節點。</span><span class="sxs-lookup"><span data-stu-id="f87a4-103">You can filter on the namespace of each element or attribute to find all nodes in that particular namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f87a4-104">範例</span><span class="sxs-lookup"><span data-stu-id="f87a4-104">Example</span></span>  
 <span data-ttu-id="f87a4-105">下列範例會使用兩個命名空間建立 XML 樹狀。</span><span class="sxs-lookup"><span data-stu-id="f87a4-105">The following example creates an XML tree with two namespaces.</span></span> <span data-ttu-id="f87a4-106">接著，它會逐一查看樹狀結構，並在這些其中一個命名空間中，列印所有項目和屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="f87a4-106">It then iterates through the tree and prints the names of all the elements and attributes in one of those namespaces.</span></span>  
  
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
  
 <span data-ttu-id="f87a4-107">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="f87a4-107">This code produces the following output:</span></span>  
  
```  
Nodes in the http://www.adventure-works.com namespace  
{http://www.adventure-works.com}Child3  
{http://www.adventure-works.com}GrandChild2  
```  
  
## <a name="example"></a><span data-ttu-id="f87a4-108">範例</span><span class="sxs-lookup"><span data-stu-id="f87a4-108">Example</span></span>  
 <span data-ttu-id="f87a4-109">下列查詢所存取的 XML 檔案包含兩種不同命名空間中的採購訂單。</span><span class="sxs-lookup"><span data-stu-id="f87a4-109">The XML file accessed by the following query contains purchase orders in two different namespaces.</span></span> <span data-ttu-id="f87a4-110">此查詢只會使用其中一個命名空間中的項目建立新的樹狀。</span><span class="sxs-lookup"><span data-stu-id="f87a4-110">The query creates a new tree with just the elements in one of the namespaces.</span></span>  
  
 <span data-ttu-id="f87a4-111">此範例使用下列 XML 文件：[XML 範例檔：合併的訂購單](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-consolidated-purchase-orders.md)。</span><span class="sxs-lookup"><span data-stu-id="f87a4-111">This example uses the following XML document: [Sample XML File: Consolidated Purchase Orders](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-consolidated-purchase-orders.md).</span></span>  
  
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
  
 <span data-ttu-id="f87a4-112">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="f87a4-112">This code produces the following output:</span></span>  
  
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
