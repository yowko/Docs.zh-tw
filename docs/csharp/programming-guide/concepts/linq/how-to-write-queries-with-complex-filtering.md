---
title: HOW TO：撰寫具有複雜篩選功能的查詢 (C#)
ms.date: 07/20/2015
ms.assetid: 4065d901-cf89-4e47-8bf9-abb65acfb003
ms.openlocfilehash: 7759a02c1b9ef0ae0c1af4bfb2600543b21cdf0f
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253203"
---
# <a name="how-to-write-queries-with-complex-filtering-c"></a><span data-ttu-id="eb47d-102">作法：撰寫具有複雜篩選功能的查詢 (C#)</span><span class="sxs-lookup"><span data-stu-id="eb47d-102">How to: Write Queries with Complex Filtering (C#)</span></span>
<span data-ttu-id="eb47d-103">有時候您會想要利用複雜篩選撰寫 LINQ to XML 查詢。</span><span class="sxs-lookup"><span data-stu-id="eb47d-103">Sometimes you want to write LINQ to XML queries with complex filters.</span></span> <span data-ttu-id="eb47d-104">例如，您可能必須尋找其子項目包含特定名稱和值的所有項目。</span><span class="sxs-lookup"><span data-stu-id="eb47d-104">For example, you might have to find all elements that have a child element with a particular name and value.</span></span> <span data-ttu-id="eb47d-105">本主題提供利用複雜篩選撰寫查詢的範例。</span><span class="sxs-lookup"><span data-stu-id="eb47d-105">This topic gives an example of writing a query with complex filtering.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb47d-106">範例</span><span class="sxs-lookup"><span data-stu-id="eb47d-106">Example</span></span>  
 <span data-ttu-id="eb47d-107">這個範例顯示如何尋找其 `PurchaseOrder` 子項目的 `Address` 屬性等於 "Shipping"，而 `Type` 子項目等於 "NY" 的所有 `State` 項目。</span><span class="sxs-lookup"><span data-stu-id="eb47d-107">This example shows how to find all `PurchaseOrder` elements that have a child `Address` element that has a `Type` attribute equal to "Shipping" and a child `State` element equal to "NY".</span></span> <span data-ttu-id="eb47d-108">它會在 `Where` 子句中使用巢狀查詢，而且如果集合在其中有任何項目，`Any` 運算子會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="eb47d-108">It uses a nested query in the `Where` clause, and the `Any` operator returns `true` if the collection has any elements in it.</span></span> <span data-ttu-id="eb47d-109">如需使用以方法為基礎之查詢語法的資訊，請參閱 [LINQ 中的查詢語法及方法語法](./query-syntax-and-method-syntax-in-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="eb47d-109">For information about using method-based query syntax, see [Query Syntax and Method Syntax in LINQ](./query-syntax-and-method-syntax-in-linq.md).</span></span>  
  
 <span data-ttu-id="eb47d-110">此範例使用下列 XML 文件：[XML 範例檔：多個訂購單 (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="eb47d-110">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="eb47d-111">如需 `Any` 運算子的詳細資訊，請參閱[數量詞作業 (C#)](./quantifier-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="eb47d-111">For more information about the `Any` operator, see [Quantifier Operations (C#)](./quantifier-operations.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("PurchaseOrders.xml");  
IEnumerable<XElement> purchaseOrders =  
    from el in root.Elements("PurchaseOrder")  
    where   
        (from add in el.Elements("Address")  
        where  
            (string)add.Attribute("Type") == "Shipping" &&  
            (string)add.Element("State") == "NY"  
        select add)  
        .Any()  
    select el;  
foreach (XElement el in purchaseOrders)  
    Console.WriteLine((string)el.Attribute("PurchaseOrderNumber"));  
```  
  
 <span data-ttu-id="eb47d-112">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="eb47d-112">This code produces the following output:</span></span>  
  
```output  
99505  
```  
  
## <a name="example"></a><span data-ttu-id="eb47d-113">範例</span><span class="sxs-lookup"><span data-stu-id="eb47d-113">Example</span></span>  
 <span data-ttu-id="eb47d-114">下列範例顯示命名空間中之 XML 的相同查詢。</span><span class="sxs-lookup"><span data-stu-id="eb47d-114">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="eb47d-115">如需詳細資訊，請參閱[命名空間概觀 (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="eb47d-115">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="eb47d-116">此範例使用下列 XML 文件：[XML 範例檔：命名空間中的多個訂購單](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="eb47d-116">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("PurchaseOrdersInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> purchaseOrders =  
    from el in root.Elements(aw + "PurchaseOrder")  
    where  
        (from add in el.Elements(aw + "Address")  
         where  
             (string)add.Attribute(aw + "Type") == "Shipping" &&  
             (string)add.Element(aw + "State") == "NY"  
         select add)  
        .Any()  
    select el;  
foreach (XElement el in purchaseOrders)  
    Console.WriteLine((string)el.Attribute(aw + "PurchaseOrderNumber"));  
```  
  
 <span data-ttu-id="eb47d-117">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="eb47d-117">This code produces the following output:</span></span>  
  
```output  
99505  
```  
  
## <a name="see-also"></a><span data-ttu-id="eb47d-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb47d-118">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="eb47d-119">投影作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="eb47d-119">Projection Operations (C#)</span></span>](./projection-operations.md)
- [<span data-ttu-id="eb47d-120">數量詞作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="eb47d-120">Quantifier Operations (C#)</span></span>](./quantifier-operations.md)
