---
title: 作法：尋找具有特定屬性的項目
ms.date: 07/20/2015
ms.assetid: 59fb7c19-d42f-40eb-8cf8-f1d5b9658eb7
ms.openlocfilehash: ec5d3bf46d517e2cfb27c228674d9b86fefffa14
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405244"
---
# <a name="how-to-find-an-element-with-a-specific-attribute-visual-basic"></a><span data-ttu-id="2e6de-102">如何：尋找具有特定屬性的元素（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="2e6de-102">How to: Find an Element with a Specific Attribute (Visual Basic)</span></span>
<span data-ttu-id="2e6de-103">這個主題顯示如何尋找其屬性具有特定值的項目。</span><span class="sxs-lookup"><span data-stu-id="2e6de-103">This topic shows how to find an element that has an attribute that has a specific value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e6de-104">範例</span><span class="sxs-lookup"><span data-stu-id="2e6de-104">Example</span></span>  
 <span data-ttu-id="2e6de-105">此範例顯示如何尋找其 `Address` 屬性具有 "Billing" 值的 `Type` 項目。</span><span class="sxs-lookup"><span data-stu-id="2e6de-105">The example shows how to find the `Address` element that has a `Type` attribute with a value of "Billing".</span></span>  
  
 <span data-ttu-id="2e6de-106">此範例使用下列 XML 文件︰[範例 XML 檔：典型採購訂單 (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="2e6de-106">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("PurchaseOrder.xml")  
Dim address As IEnumerable(Of XElement) = _  
    From el In root.<Address> _  
    Where el.@Type = "Billing" _  
    Select el  
For Each el As XElement In address  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="2e6de-107">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="2e6de-107">This code produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="2e6de-108">請注意，此範例使用[Xml 子軸屬性](../../../language-reference/xml-axis/xml-child-axis-property.md)、 [xml 屬性軸屬性](../../../language-reference/xml-axis/xml-attribute-axis-property.md)和[xml 值屬性](../../../language-reference/xml-axis/xml-value-property.md)。</span><span class="sxs-lookup"><span data-stu-id="2e6de-108">Note that this example uses the [XML Child axis property](../../../language-reference/xml-axis/xml-child-axis-property.md), the [XML Attribute axis property](../../../language-reference/xml-axis/xml-attribute-axis-property.md), and the [XML Value property](../../../language-reference/xml-axis/xml-value-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e6de-109">範例</span><span class="sxs-lookup"><span data-stu-id="2e6de-109">Example</span></span>  
 <span data-ttu-id="2e6de-110">下列範例顯示命名空間中之 XML 的相同查詢。</span><span class="sxs-lookup"><span data-stu-id="2e6de-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="2e6de-111">如需詳細資訊，請參閱[命名空間總覽（LINQ to XML）（Visual Basic）](namespaces-overview-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="2e6de-111">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="2e6de-112">此範例使用下列 XML 文件︰[範例 XML 檔：命名空間中的典型採購訂單](sample-xml-file-typical-purchase-order-in-a-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="2e6de-112">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns:aw='http://www.adventure-works.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("PurchaseOrderInNamespace.xml")  
        Dim address As IEnumerable(Of XElement) = _  
            From el In root.<aw:Address> _  
            Where el.@aw:Type = "Billing" _  
            Select el  
        For Each el As XElement In address  
            Console.WriteLine(el)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="2e6de-113">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="2e6de-113">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2e6de-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e6de-114">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="2e6de-115">基本查詢（LINQ to XML）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="2e6de-115">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](basic-queries-linq-to-xml.md)
- [<span data-ttu-id="2e6de-116">標準查詢運算子概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e6de-116">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="2e6de-117">投射作業（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="2e6de-117">Projection Operations (Visual Basic)</span></span>](projection-operations.md)
