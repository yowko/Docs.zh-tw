---
title: 作法：尋找具有特定屬性的項目 (C#)
ms.date: 07/20/2015
ms.assetid: b92591aa-3cfb-490e-99f6-da8de335e362
ms.openlocfilehash: da2d1691af6268a97e1f586e92c26bbb26906100
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593600"
---
# <a name="how-to-find-an-element-with-a-specific-attribute-c"></a><span data-ttu-id="aa103-102">作法：尋找具有特定屬性的項目 (C#)</span><span class="sxs-lookup"><span data-stu-id="aa103-102">How to: Find an Element with a Specific Attribute (C#)</span></span>
<span data-ttu-id="aa103-103">這個主題顯示如何尋找其屬性具有特定值的項目。</span><span class="sxs-lookup"><span data-stu-id="aa103-103">This topic shows how to find an element that has an attribute that has a specific value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa103-104">範例</span><span class="sxs-lookup"><span data-stu-id="aa103-104">Example</span></span>  
 <span data-ttu-id="aa103-105">此範例顯示如何尋找其 `Address` 屬性具有 "Billing" 值的 `Type` 項目。</span><span class="sxs-lookup"><span data-stu-id="aa103-105">The example shows how to find the `Address` element that has a `Type` attribute with a value of "Billing".</span></span>  
  
 <span data-ttu-id="aa103-106">此範例使用下列 XML 文件：[XML 範例檔：典型訂購單 (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md)。</span><span class="sxs-lookup"><span data-stu-id="aa103-106">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> address =  
    from el in root.Elements("Address")  
    where (string)el.Attribute("Type") == "Billing"  
    select el;  
foreach (XElement el in address)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="aa103-107">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="aa103-107">This code produces the following output:</span></span>  
  
```xml  
<Address Type="Billing">  
  <Name>Tai Yee</Name>  
  <Street>8 Oak Avenue</Street>  
  <City>Old Town</City>  
  <State>PA</State>  
  <Zip>95819</Zip>  
  <Country>USA</Country>  
</Address>  
```  
  
## <a name="example"></a><span data-ttu-id="aa103-108">範例</span><span class="sxs-lookup"><span data-stu-id="aa103-108">Example</span></span>  
 <span data-ttu-id="aa103-109">下列範例顯示命名空間中之 XML 的相同查詢。</span><span class="sxs-lookup"><span data-stu-id="aa103-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="aa103-110">如需詳細資訊，請參閱[命名空間概觀 (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="aa103-110">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="aa103-111">此範例使用下列 XML 文件：[XML 範例檔：命名空間中的典型訂購單](./sample-xml-file-typical-purchase-order-in-a-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="aa103-111">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("PurchaseOrderInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> address =  
    from el in root.Elements(aw + "Address")  
    where (string)el.Attribute(aw + "Type") == "Billing"  
    select el;  
foreach (XElement el in address)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="aa103-112">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="aa103-112">This code produces the following output:</span></span>  
  
```xml  
<aw:Address aw:Type="Billing" xmlns:aw="http://www.adventure-works.com">  
  <aw:Name>Tai Yee</aw:Name>  
  <aw:Street>8 Oak Avenue</aw:Street>  
  <aw:City>Old Town</aw:City>  
  <aw:State>PA</aw:State>  
  <aw:Zip>95819</aw:Zip>  
  <aw:Country>USA</aw:Country>  
</aw:Address>  
```  
  
## <a name="see-also"></a><span data-ttu-id="aa103-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aa103-113">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="aa103-114">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="aa103-114">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="aa103-115">投影作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="aa103-115">Projection Operations (C#)</span></span>](./projection-operations.md)
