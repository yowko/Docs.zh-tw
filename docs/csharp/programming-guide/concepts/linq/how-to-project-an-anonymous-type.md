---
title: '如何投影匿名型別（c #）'
description: '瞭解如何在 c # 中將查詢投影至匿名型別。 使用匿名型別會比建立新的型別更簡單，只是簡單地使用。'
ms.date: 07/20/2015
ms.assetid: 5cb9be13-5ac4-4373-a034-b3520a5b2dec
ms.openlocfilehash: 6598796a4ba95362340f2551b1da6ac6d857eaae
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104633"
---
# <a name="how-to-project-an-anonymous-type-c"></a><span data-ttu-id="9c4ed-104">如何投影匿名型別（c #）</span><span class="sxs-lookup"><span data-stu-id="9c4ed-104">How to project an anonymous type (C#)</span></span>
<span data-ttu-id="9c4ed-105">在某些情況下，即使您知道您只會短期使用新型別，您可能還是想要將查詢規劃為該型別。</span><span class="sxs-lookup"><span data-stu-id="9c4ed-105">In some cases you might want to project a query to a new type, even though you know you will only use this type for a short while.</span></span> <span data-ttu-id="9c4ed-106">建立新型別只用於這個規劃太費工。</span><span class="sxs-lookup"><span data-stu-id="9c4ed-106">It is a lot of extra work to create a new type just to use in the projection.</span></span> <span data-ttu-id="9c4ed-107">在此情況下，較有效率的方法為規劃匿名型別。</span><span class="sxs-lookup"><span data-stu-id="9c4ed-107">A more efficient approach in this case is to project to an anonymous type.</span></span> <span data-ttu-id="9c4ed-108">匿名型別可讓您定義類別，然後宣告並初始化該類別的物件，而不用提供類別一個名稱。</span><span class="sxs-lookup"><span data-stu-id="9c4ed-108">Anonymous types allow you to define a class, then declare and initialize an object of that class, without giving the class a name.</span></span>  
  
 <span data-ttu-id="9c4ed-109">匿名型別為「元組」\*\* 之數學概念的 C# 實作。</span><span class="sxs-lookup"><span data-stu-id="9c4ed-109">Anonymous types are the C# implementation of the mathematical concept of a *tuple*.</span></span> <span data-ttu-id="9c4ed-110">數學術語「Tuple」源自於 single、double、triple、quadruple、quintuple、n-tuple 序列。</span><span class="sxs-lookup"><span data-stu-id="9c4ed-110">The mathematical term tuple originated from the sequence single, double, triple, quadruple, quintuple, n-tuple.</span></span> <span data-ttu-id="9c4ed-111">這表示有限的物件順序，每個都有特定的型別。</span><span class="sxs-lookup"><span data-stu-id="9c4ed-111">It refers to a finite sequence of objects, each of a specific type.</span></span> <span data-ttu-id="9c4ed-112">有時候，這稱為成對的名稱/值清單。</span><span class="sxs-lookup"><span data-stu-id="9c4ed-112">Sometimes this is called a list of name/value pairs.</span></span> <span data-ttu-id="9c4ed-113">例如，在[範例 XML 檔：典型採購訂單 (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md) XML 文件中的地址內容可能如下表示：</span><span class="sxs-lookup"><span data-stu-id="9c4ed-113">For example, the contents of an address in the [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md) XML document could be expressed as follows:</span></span>  
  
```text  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 <span data-ttu-id="9c4ed-114">當您建立匿名型別的執行個體時，將它視為建立順序 n 的 Tuple 比較方法。</span><span class="sxs-lookup"><span data-stu-id="9c4ed-114">When you create an instance of an anonymous type, it is convenient to think of it as creating a tuple of order n.</span></span> <span data-ttu-id="9c4ed-115">如果您撰寫可在 `select` 子句中建立 Tuple 的查詢，該查詢會傳回 Tuple 的 `IEnumerable`。</span><span class="sxs-lookup"><span data-stu-id="9c4ed-115">If you write a query that creates a tuple in the `select` clause, the query returns an `IEnumerable` of the tuple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c4ed-116">範例</span><span class="sxs-lookup"><span data-stu-id="9c4ed-116">Example</span></span>  
 <span data-ttu-id="9c4ed-117">在這個範例中，`select` 子句會規劃匿名型別。</span><span class="sxs-lookup"><span data-stu-id="9c4ed-117">In this example, the `select` clause projects an anonymous type.</span></span> <span data-ttu-id="9c4ed-118">然後，此範例會使用 `var` 來建立 `IEnumerable` 物件。</span><span class="sxs-lookup"><span data-stu-id="9c4ed-118">The example then uses `var` to create the `IEnumerable` object.</span></span> <span data-ttu-id="9c4ed-119">在 `foreach` 迴圈中，反覆運算變數會變成在查詢運算式中建立之匿名型別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9c4ed-119">Within the `foreach` loop, the iteration variable becomes an instance of the anonymous type created in the query expression.</span></span>  
  
 <span data-ttu-id="9c4ed-120">此範例使用下列 XML 文件︰[範例 XML 檔：客戶和訂單 (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md)。</span><span class="sxs-lookup"><span data-stu-id="9c4ed-120">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
```csharp  
XElement custOrd = XElement.Load("CustomersOrders.xml");  
var custList =  
    from el in custOrd.Element("Customers").Elements("Customer")  
    select new {  
        CustomerID = (string)el.Attribute("CustomerID"),  
        CompanyName = (string)el.Element("CompanyName"),  
        ContactName = (string)el.Element("ContactName")  
    };  
foreach (var cust in custList)  
    Console.WriteLine("{0}:{1}:{2}", cust.CustomerID, cust.CompanyName, cust.ContactName);  
```  
  
 <span data-ttu-id="9c4ed-121">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="9c4ed-121">This code produces the following output:</span></span>  
  
```output  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  