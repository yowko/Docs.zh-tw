---
title: '如何篩選元素名稱（LINQ to XML）（c #）'
description: 瞭解當您呼叫會傳回 System.xml.linq.xelement> 之 IEnumerable 的方法時，如何篩選元素名稱。
ms.date: 07/20/2015
ms.assetid: 1849fb03-f075-421f-863c-e8fb32773cdf
ms.openlocfilehash: be660a69b8d860ad907661ce17002379b8842121
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301745"
---
# <a name="how-to-filter-on-element-names-linq-to-xml-c"></a><span data-ttu-id="075ef-103">如何篩選元素名稱（LINQ to XML）（c #）</span><span class="sxs-lookup"><span data-stu-id="075ef-103">How to filter on element names (LINQ to XML) (C#)</span></span>
<span data-ttu-id="075ef-104">當您呼叫可傳回 <xref:System.Collections.Generic.IEnumerable%601> 之 <xref:System.Xml.Linq.XElement> 的其中一個方法時，您可以篩選項目名稱。</span><span class="sxs-lookup"><span data-stu-id="075ef-104">When you call one of the methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, you can filter on the element name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="075ef-105">範例</span><span class="sxs-lookup"><span data-stu-id="075ef-105">Example</span></span>  
 <span data-ttu-id="075ef-106">這個範例會擷取子代 (Descendant) 的集合，而且該集合會篩選成僅包含具有指定之名稱的子代。</span><span class="sxs-lookup"><span data-stu-id="075ef-106">This example retrieves a collection of descendants that is filtered to contain only descendants with the specified name.</span></span>  
  
 <span data-ttu-id="075ef-107">此範例使用下列 XML 文件︰[範例 XML 檔：典型採購訂單 (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md)。</span><span class="sxs-lookup"><span data-stu-id="075ef-107">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants("ProductName")  
    select el;  
foreach(XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string) prdName);  
```  
  
 <span data-ttu-id="075ef-108">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="075ef-108">This code produces the following output:</span></span>  
  
```output  
ProductName:Lawnmower  
ProductName:Baby Monitor  
```  
  
 <span data-ttu-id="075ef-109">其他傳回 <xref:System.Collections.Generic.IEnumerable%601> 集合之 <xref:System.Xml.Linq.XElement> 的方法都依照相同的模式。</span><span class="sxs-lookup"><span data-stu-id="075ef-109">The other methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> collections follow the same pattern.</span></span> <span data-ttu-id="075ef-110">它們的簽章類似於 <xref:System.Xml.Linq.XContainer.Elements%2A> 及 <xref:System.Xml.Linq.XContainer.Descendants%2A>。</span><span class="sxs-lookup"><span data-stu-id="075ef-110">Their signatures are similar to <xref:System.Xml.Linq.XContainer.Elements%2A> and <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span></span> <span data-ttu-id="075ef-111">下列是具有類似方法簽章之方法的完整清單：</span><span class="sxs-lookup"><span data-stu-id="075ef-111">The following is the complete list of methods that have similar method signatures:</span></span>  
  
- <xref:System.Xml.Linq.XNode.Ancestors%2A>  
  
- <xref:System.Xml.Linq.XContainer.Descendants%2A>  
  
- <xref:System.Xml.Linq.XContainer.Elements%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>  
  
- <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>  
  
- <xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A>  
  
## <a name="example"></a><span data-ttu-id="075ef-112">範例</span><span class="sxs-lookup"><span data-stu-id="075ef-112">Example</span></span>  
 <span data-ttu-id="075ef-113">下列範例顯示命名空間中之 XML 的相同查詢。</span><span class="sxs-lookup"><span data-stu-id="075ef-113">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="075ef-114">如需詳細資訊，請參閱[命名空間概觀 (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="075ef-114">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="075ef-115">此範例使用下列 XML 文件︰[範例 XML 檔：命名空間中的典型採購訂單](./sample-xml-file-typical-purchase-order-in-a-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="075ef-115">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants(aw + "ProductName")  
    select el;  
foreach (XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string)prdName);  
```  
  
 <span data-ttu-id="075ef-116">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="075ef-116">This code produces the following output:</span></span>  
  
```output  
{http://www.adventure-works.com}ProductName:Lawnmower  
{http://www.adventure-works.com}ProductName:Baby Monitor  
```  
  
## <a name="see-also"></a><span data-ttu-id="075ef-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="075ef-117">See also</span></span>

- [<span data-ttu-id="075ef-118">LINQ to XML 座標軸 (C#)</span><span class="sxs-lookup"><span data-stu-id="075ef-118">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
