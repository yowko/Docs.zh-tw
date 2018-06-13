---
title: 如何：尋找具有特定屬性的項目 (C#)
ms.date: 07/20/2015
ms.assetid: b92591aa-3cfb-490e-99f6-da8de335e362
ms.openlocfilehash: 53296b2ace23bbc57deb0f5e7c0b23ebfc9613d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33325691"
---
# <a name="how-to-find-an-element-with-a-specific-attribute-c"></a><span data-ttu-id="696ab-102">如何：尋找具有特定屬性的項目 (C#)</span><span class="sxs-lookup"><span data-stu-id="696ab-102">How to: Find an Element with a Specific Attribute (C#)</span></span>
<span data-ttu-id="696ab-103">這個主題顯示如何尋找其屬性具有特定值的項目。</span><span class="sxs-lookup"><span data-stu-id="696ab-103">This topic shows how to find an element that has an attribute that has a specific value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="696ab-104">範例</span><span class="sxs-lookup"><span data-stu-id="696ab-104">Example</span></span>  
 <span data-ttu-id="696ab-105">此範例顯示如何尋找其 `Address` 屬性具有 "Billing" 值的 `Type` 項目。</span><span class="sxs-lookup"><span data-stu-id="696ab-105">The example shows how to find the `Address` element that has a `Type` attribute with a value of "Billing".</span></span>  
  
 <span data-ttu-id="696ab-106">此範例使用下列 XML 文件︰[範例 XML 檔：典型採購訂單 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md)。</span><span class="sxs-lookup"><span data-stu-id="696ab-106">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> address =  
    from el in root.Elements("Address")  
    where (string)el.Attribute("Type") == "Billing"  
    select el;  
foreach (XElement el in address)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="696ab-107">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="696ab-107">This code produces the following output:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="696ab-108">範例</span><span class="sxs-lookup"><span data-stu-id="696ab-108">Example</span></span>  
 <span data-ttu-id="696ab-109">下列範例顯示命名空間中之 XML 的相同查詢。</span><span class="sxs-lookup"><span data-stu-id="696ab-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="696ab-110">如需詳細資訊，請參閱[處理 XML 命名空間 (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)。</span><span class="sxs-lookup"><span data-stu-id="696ab-110">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="696ab-111">此範例使用下列 XML 文件︰[範例 XML 檔：命名空間中的典型採購訂單](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="696ab-111">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="696ab-112">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="696ab-112">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="696ab-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="696ab-113">See Also</span></span>  
 <xref:System.Xml.Linq.XElement.Attribute%2A>  
 <xref:System.Xml.Linq.XContainer.Elements%2A>  
 [<span data-ttu-id="696ab-114">基本查詢 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="696ab-114">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)  
 [<span data-ttu-id="696ab-115">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="696ab-115">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="696ab-116">投影作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="696ab-116">Projection Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)
