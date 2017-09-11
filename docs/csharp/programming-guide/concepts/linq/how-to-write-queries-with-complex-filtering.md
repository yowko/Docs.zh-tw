---
title: "如何：撰寫具有複雜篩選功能的查詢 (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 4065d901-cf89-4e47-8bf9-abb65acfb003
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c5b212796df6e65263b8b35514b6807bcdf5797f
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-write-queries-with-complex-filtering-c"></a><span data-ttu-id="ce975-102">如何：撰寫具有複雜篩選功能的查詢 (C#)</span><span class="sxs-lookup"><span data-stu-id="ce975-102">How to: Write Queries with Complex Filtering (C#)</span></span>
<span data-ttu-id="ce975-103">有時候您會想要利用複雜篩選撰寫 LINQ to XML 查詢。</span><span class="sxs-lookup"><span data-stu-id="ce975-103">Sometimes you want to write LINQ to XML queries with complex filters.</span></span> <span data-ttu-id="ce975-104">例如，您可能必須尋找其子項目包含特定名稱和值的所有項目。</span><span class="sxs-lookup"><span data-stu-id="ce975-104">For example, you might have to find all elements that have a child element with a particular name and value.</span></span> <span data-ttu-id="ce975-105">本主題提供利用複雜篩選撰寫查詢的範例。</span><span class="sxs-lookup"><span data-stu-id="ce975-105">This topic gives an example of writing a query with complex filtering.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce975-106">範例</span><span class="sxs-lookup"><span data-stu-id="ce975-106">Example</span></span>  
 <span data-ttu-id="ce975-107">這個範例顯示如何尋找其 `PurchaseOrder` 子項目的 `Address` 屬性等於 "Shipping"，而 `Type` 子項目等於 "NY" 的所有 `State` 項目。</span><span class="sxs-lookup"><span data-stu-id="ce975-107">This example shows how to find all `PurchaseOrder` elements that have a child `Address` element that has a `Type` attribute equal to "Shipping" and a child `State` element equal to "NY".</span></span> <span data-ttu-id="ce975-108">它會在 `Where` 子句中使用巢狀查詢，而且如果集合在其中有任何項目，`Any` 運算子會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="ce975-108">It uses a nested query in the `Where` clause, and the `Any` operator returns `true` if the collection has any elements in it.</span></span> <span data-ttu-id="ce975-109">如需使用以方法為基礎之查詢語法的資訊，請參閱 [LINQ 中的查詢語法及方法語法](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="ce975-109">For information about using method-based query syntax, see [Query Syntax and Method Syntax in LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).</span></span>  
  
 <span data-ttu-id="ce975-110">此範例使用下列 XML 文件︰[範例 XML 檔：多份採購訂單 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="ce975-110">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="ce975-111">如需 `Any` 運算子的詳細資訊，請參閱[數量詞作業 (C#)](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="ce975-111">For more information about the `Any` operator, see [Quantifier Operations (C#)](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md).</span></span>  
  
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
  
 <span data-ttu-id="ce975-112">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="ce975-112">This code produces the following output:</span></span>  
  
```  
99505  
```  
  
## <a name="example"></a><span data-ttu-id="ce975-113">範例</span><span class="sxs-lookup"><span data-stu-id="ce975-113">Example</span></span>  
 <span data-ttu-id="ce975-114">下列範例顯示命名空間中之 XML 的相同查詢。</span><span class="sxs-lookup"><span data-stu-id="ce975-114">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="ce975-115">如需詳細資訊，請參閱[處理 XML 命名空間 (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)。</span><span class="sxs-lookup"><span data-stu-id="ce975-115">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="ce975-116">此範例使用下列 XML 文件︰[範例 XML 檔：命名空間中的多份採購訂單](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="ce975-116">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="ce975-117">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="ce975-117">This code produces the following output:</span></span>  
  
```  
99505  
```  
  
## <a name="see-also"></a><span data-ttu-id="ce975-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce975-118">See Also</span></span>  
 <span data-ttu-id="ce975-119"><xref:System.Xml.Linq.XElement.Attribute%2A></span><span class="sxs-lookup"><span data-stu-id="ce975-119"><xref:System.Xml.Linq.XElement.Attribute%2A></span></span>   
 <span data-ttu-id="ce975-120"><xref:System.Xml.Linq.XContainer.Elements%2A></span><span class="sxs-lookup"><span data-stu-id="ce975-120"><xref:System.Xml.Linq.XContainer.Elements%2A></span></span>   
 <span data-ttu-id="ce975-121">[基本查詢 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md) </span><span class="sxs-lookup"><span data-stu-id="ce975-121">[Basic Queries (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md) </span></span>  
 <span data-ttu-id="ce975-122">[投射作業 (C#)](../../../../csharp/programming-guide/concepts/linq/projection-operations.md) </span><span class="sxs-lookup"><span data-stu-id="ce975-122">[Projection Operations (C#)](../../../../csharp/programming-guide/concepts/linq/projection-operations.md) </span></span>  
 [<span data-ttu-id="ce975-123">數量詞作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="ce975-123">Quantifier Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md)

