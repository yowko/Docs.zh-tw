---
title: 如何篩選元素名稱（LINQ to XML）（C#）
ms.date: 07/20/2015
ms.assetid: 1849fb03-f075-421f-863c-e8fb32773cdf
ms.openlocfilehash: 74efb19ef5ec77ca29145d27a8e5aa977530b68b
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141259"
---
# <a name="how-to-filter-on-element-names-linq-to-xml-c"></a><span data-ttu-id="5f24f-102">如何篩選元素名稱（LINQ to XML）（C#）</span><span class="sxs-lookup"><span data-stu-id="5f24f-102">How to filter on element names (LINQ to XML) (C#)</span></span>
<span data-ttu-id="5f24f-103">當您呼叫可傳回 <xref:System.Collections.Generic.IEnumerable%601> 之 <xref:System.Xml.Linq.XElement> 的其中一個方法時，您可以篩選項目名稱。</span><span class="sxs-lookup"><span data-stu-id="5f24f-103">When you call one of the methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, you can filter on the element name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f24f-104">範例</span><span class="sxs-lookup"><span data-stu-id="5f24f-104">Example</span></span>  
 <span data-ttu-id="5f24f-105">這個範例會擷取子代 (Descendant) 的集合，而且該集合會篩選成僅包含具有指定之名稱的子代。</span><span class="sxs-lookup"><span data-stu-id="5f24f-105">This example retrieves a collection of descendants that is filtered to contain only descendants with the specified name.</span></span>  
  
 <span data-ttu-id="5f24f-106">此範例使用下列 XML 文件︰[範例 XML 檔：典型採購訂單 (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md)。</span><span class="sxs-lookup"><span data-stu-id="5f24f-106">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants("ProductName")  
    select el;  
foreach(XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string) prdName);  
```  
  
 <span data-ttu-id="5f24f-107">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="5f24f-107">This code produces the following output:</span></span>  
  
```output  
ProductName:Lawnmower  
ProductName:Baby Monitor  
```  
  
 <span data-ttu-id="5f24f-108">其他傳回 <xref:System.Collections.Generic.IEnumerable%601> 集合之 <xref:System.Xml.Linq.XElement> 的方法都依照相同的模式。</span><span class="sxs-lookup"><span data-stu-id="5f24f-108">The other methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> collections follow the same pattern.</span></span> <span data-ttu-id="5f24f-109">它們的簽章類似於 <xref:System.Xml.Linq.XContainer.Elements%2A> 及 <xref:System.Xml.Linq.XContainer.Descendants%2A>。</span><span class="sxs-lookup"><span data-stu-id="5f24f-109">Their signatures are similar to <xref:System.Xml.Linq.XContainer.Elements%2A> and <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span></span> <span data-ttu-id="5f24f-110">下列是具有類似方法簽章之方法的完整清單：</span><span class="sxs-lookup"><span data-stu-id="5f24f-110">The following is the complete list of methods that have similar method signatures:</span></span>  
  
- <xref:System.Xml.Linq.XNode.Ancestors%2A>  
  
- <xref:System.Xml.Linq.XContainer.Descendants%2A>  
  
- <xref:System.Xml.Linq.XContainer.Elements%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A>  
  
## <a name="example"></a><span data-ttu-id="5f24f-111">範例</span><span class="sxs-lookup"><span data-stu-id="5f24f-111">Example</span></span>  
 <span data-ttu-id="5f24f-112">下列範例顯示命名空間中之 XML 的相同查詢。</span><span class="sxs-lookup"><span data-stu-id="5f24f-112">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="5f24f-113">如需詳細資訊，請參閱[命名空間概觀 (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="5f24f-113">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="5f24f-114">此範例使用下列 XML 文件︰[範例 XML 檔：命名空間中的典型採購訂單](./sample-xml-file-typical-purchase-order-in-a-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="5f24f-114">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants(aw + "ProductName")  
    select el;  
foreach (XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string)prdName);  
```  
  
 <span data-ttu-id="5f24f-115">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="5f24f-115">This code produces the following output:</span></span>  
  
```output  
{http://www.adventure-works.com}ProductName:Lawnmower  
{http://www.adventure-works.com}ProductName:Baby Monitor  
```  
  
## <a name="see-also"></a><span data-ttu-id="5f24f-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="5f24f-116">See also</span></span>

- [<span data-ttu-id="5f24f-117">LINQ to XML 座標軸 (C#)</span><span class="sxs-lookup"><span data-stu-id="5f24f-117">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
