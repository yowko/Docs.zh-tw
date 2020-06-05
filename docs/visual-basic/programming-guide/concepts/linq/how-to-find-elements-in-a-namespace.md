---
title: 作法：在命名空間中尋找項目 (XPath-LINQ to XML)
ms.date: 07/20/2015
ms.assetid: c7cb3b77-3424-4b54-9efa-4dc715948e41
ms.openlocfilehash: 3663516e6b6289fe3b1d0599ff3ed4b7dad6a80a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405192"
---
# <a name="how-to-find-elements-in-a-namespace-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="fc140-102">如何：在命名空間中尋找元素（XPath-LINQ to XML）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="fc140-102">How to: Find Elements in a Namespace (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="fc140-103">XPath 運算式可以在特定的命名空間中尋找節點。</span><span class="sxs-lookup"><span data-stu-id="fc140-103">XPath expressions can find nodes in a particular namespace.</span></span> <span data-ttu-id="fc140-104">XPath 運算式使用命名空間前置詞來指定命名空間。</span><span class="sxs-lookup"><span data-stu-id="fc140-104">XPath expressions use namespace prefixes for specifying namespaces.</span></span> <span data-ttu-id="fc140-105">若要剖析包含命名空間前置詞的 XPath 運算式，您必須將物件傳遞到實作 <xref:System.Xml.IXmlNamespaceResolver> 的 XPath 方法。</span><span class="sxs-lookup"><span data-stu-id="fc140-105">To parse an XPath expression that contains namespace prefixes, you must pass an object to the XPath methods that implements <xref:System.Xml.IXmlNamespaceResolver>.</span></span> <span data-ttu-id="fc140-106">此範例會使用 <xref:System.Xml.XmlNamespaceManager>。</span><span class="sxs-lookup"><span data-stu-id="fc140-106">This example uses <xref:System.Xml.XmlNamespaceManager>.</span></span>  
  
 <span data-ttu-id="fc140-107">XPath 運算式為：</span><span class="sxs-lookup"><span data-stu-id="fc140-107">The XPath expression is:</span></span>  
  
 `./aw:*`  
  
## <a name="example"></a><span data-ttu-id="fc140-108">範例</span><span class="sxs-lookup"><span data-stu-id="fc140-108">Example</span></span>  
 <span data-ttu-id="fc140-109">下列範例會讀取包含兩個命名空間的 XML 樹狀。</span><span class="sxs-lookup"><span data-stu-id="fc140-109">The following example reads an XML tree that contains two namespaces.</span></span> <span data-ttu-id="fc140-110">該範例會使用 <xref:System.Xml.XmlReader> 來讀取 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="fc140-110">It uses an <xref:System.Xml.XmlReader> to read the XML document.</span></span> <span data-ttu-id="fc140-111">接著，它會從 <xref:System.Xml.XmlNameTable> 取得 <xref:System.Xml.XmlReader>，並從 <xref:System.Xml.XmlNamespaceManager> 取得 <xref:System.Xml.XmlNameTable>。</span><span class="sxs-lookup"><span data-stu-id="fc140-111">It then gets an <xref:System.Xml.XmlNameTable> from the <xref:System.Xml.XmlReader>, and an <xref:System.Xml.XmlNamespaceManager> from the <xref:System.Xml.XmlNameTable>.</span></span> <span data-ttu-id="fc140-112">選取項目時，它會使用 <xref:System.Xml.XmlNamespaceManager>。</span><span class="sxs-lookup"><span data-stu-id="fc140-112">It uses the <xref:System.Xml.XmlNamespaceManager> when selecting elements.</span></span>  
  
```vb  
Dim reader As XmlReader = _  
        XmlReader.Create("ConsolidatedPurchaseOrders.xml")  
Dim root As XElement = XElement.Load(reader)  
Dim nameTable As XmlNameTable = reader.NameTable  
Dim namespaceManager As XmlNamespaceManager = New XmlNamespaceManager(nameTable)  
namespaceManager.AddNamespace("aw", "http://www.adventure-works.com")  
  
Dim list1 As IEnumerable(Of XElement) = _  
        root.XPathSelectElements("./aw:*", namespaceManager)  
Dim list2 As IEnumerable(Of XElement) = _  
    From el In root.Elements() _  
    Where el.Name.Namespace = "http://www.adventure-works.com" _  
    Select el  
  
If list1.Count() = list2.Count() And _  
        list1.Intersect(list2).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list2  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="fc140-113">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="fc140-113">This example produces the following output:</span></span>  
  
```console
Results are identical  
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
```  
  
## <a name="see-also"></a><span data-ttu-id="fc140-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc140-114">See also</span></span>

- [<span data-ttu-id="fc140-115">XPath 使用者的 LINQ to XML （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="fc140-115">LINQ to XML for XPath Users (Visual Basic)</span></span>](linq-to-xml-for-xpath-users.md)
