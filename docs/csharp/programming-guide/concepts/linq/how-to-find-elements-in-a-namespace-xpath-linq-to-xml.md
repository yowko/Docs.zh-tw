---
title: 如何尋找命名空間中的元素（XPath-LINQ to XML）（C#）
ms.date: 07/20/2015
ms.assetid: cae1c4ac-6cd5-46cf-9b1c-bd85bc9b7ea9
ms.openlocfilehash: da9d819be5234a2429b6eab276f89bd0d877d4a7
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141063"
---
# <a name="how-to-find-elements-in-a-namespace-xpath-linq-to-xml-c"></a><span data-ttu-id="6376f-102">如何尋找命名空間中的元素（XPath-LINQ to XML）（C#）</span><span class="sxs-lookup"><span data-stu-id="6376f-102">How to find elements in a namespace (XPath-LINQ to XML) (C#)</span></span>

<span data-ttu-id="6376f-103">XPath 運算式可以在特定的命名空間中尋找節點。</span><span class="sxs-lookup"><span data-stu-id="6376f-103">XPath expressions can find nodes in a particular namespace.</span></span> <span data-ttu-id="6376f-104">XPath 運算式使用命名空間前置詞來指定命名空間。</span><span class="sxs-lookup"><span data-stu-id="6376f-104">XPath expressions use namespace prefixes for specifying namespaces.</span></span> <span data-ttu-id="6376f-105">若要剖析包含命名空間前置詞的 XPath 運算式，您必須將物件傳遞到實作 <xref:System.Xml.IXmlNamespaceResolver> 的 XPath 方法。</span><span class="sxs-lookup"><span data-stu-id="6376f-105">To parse an XPath expression that contains namespace prefixes, you must pass an object to the XPath methods that implements <xref:System.Xml.IXmlNamespaceResolver>.</span></span> <span data-ttu-id="6376f-106">這個範例會使用 <xref:System.Xml.XmlNamespaceManager>。</span><span class="sxs-lookup"><span data-stu-id="6376f-106">This example uses <xref:System.Xml.XmlNamespaceManager>.</span></span>

<span data-ttu-id="6376f-107">XPath 運算式為：</span><span class="sxs-lookup"><span data-stu-id="6376f-107">The XPath expression is:</span></span>

`./aw:*`

## <a name="example"></a><span data-ttu-id="6376f-108">範例</span><span class="sxs-lookup"><span data-stu-id="6376f-108">Example</span></span>

<span data-ttu-id="6376f-109">下列範例會讀取包含兩個命名空間的 XML 樹狀。</span><span class="sxs-lookup"><span data-stu-id="6376f-109">The following example reads an XML tree that contains two namespaces.</span></span> <span data-ttu-id="6376f-110">該範例會使用 <xref:System.Xml.XmlReader> 來讀取 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="6376f-110">It uses an <xref:System.Xml.XmlReader> to read the XML document.</span></span> <span data-ttu-id="6376f-111">接著，它會從 <xref:System.Xml.XmlNameTable> 取得 <xref:System.Xml.XmlReader>，並從 <xref:System.Xml.XmlNamespaceManager> 取得 <xref:System.Xml.XmlNameTable>。</span><span class="sxs-lookup"><span data-stu-id="6376f-111">It then gets an <xref:System.Xml.XmlNameTable> from the <xref:System.Xml.XmlReader>, and an <xref:System.Xml.XmlNamespaceManager> from the <xref:System.Xml.XmlNameTable>.</span></span> <span data-ttu-id="6376f-112">選取項目時，它會使用 <xref:System.Xml.XmlNamespaceManager>。</span><span class="sxs-lookup"><span data-stu-id="6376f-112">It uses the <xref:System.Xml.XmlNamespaceManager> when selecting elements.</span></span>

```csharp
XmlReader reader = XmlReader.Create("ConsolidatedPurchaseOrders.xml");
XElement root = XElement.Load(reader);
XmlNameTable nameTable = reader.NameTable;
XmlNamespaceManager namespaceManager = new XmlNamespaceManager(nameTable);
namespaceManager.AddNamespace("aw", "http://www.adventure-works.com");
IEnumerable<XElement> list1 = root.XPathSelectElements("./aw:*", namespaceManager);
IEnumerable<XElement> list2 =
    from el in root.Elements()
    where el.Name.Namespace == "http://www.adventure-works.com"
    select el;
if (list1.Count() == list2.Count() &&
        list1.Intersect(list2).Count() == list1.Count())
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
foreach (XElement el in list2)
    Console.WriteLine(el);
```

<span data-ttu-id="6376f-113">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="6376f-113">This example produces the following output:</span></span>

```output
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
