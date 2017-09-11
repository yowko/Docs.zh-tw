---
title: "如何︰ 投影匿名類型 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 30b42987-0e0e-4b2b-adb1-5255ddfbcd7b
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 41f982ce1c67e7dccfd8ea2f3dd17a774a20646f
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017


---
# <a name="how-to-project-an-anonymous-type-visual-basic"></a><span data-ttu-id="ba8bc-102">如何︰ 投影匿名類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ba8bc-102">How to: Project an Anonymous Type (Visual Basic)</span></span>
<span data-ttu-id="ba8bc-103">在某些情況下，即使您知道您只會短期使用新型別，您可能還是想要將查詢規劃為該型別。</span><span class="sxs-lookup"><span data-stu-id="ba8bc-103">In some cases you might want to project a query to a new type, even though you know you will only use this type for a short while.</span></span> <span data-ttu-id="ba8bc-104">建立新型別只用於這個規劃太費工。</span><span class="sxs-lookup"><span data-stu-id="ba8bc-104">It is a lot of extra work to create a new type just to use in the projection.</span></span> <span data-ttu-id="ba8bc-105">在此情況下，較有效率的方法為規劃匿名型別。</span><span class="sxs-lookup"><span data-stu-id="ba8bc-105">A more efficient approach in this case is to project to an anonymous type.</span></span> <span data-ttu-id="ba8bc-106">匿名型別可讓您定義類別，然後宣告並初始化該類別的物件，而不用提供類別一個名稱。</span><span class="sxs-lookup"><span data-stu-id="ba8bc-106">Anonymous types allow you to define a class, then declare and initialize an object of that class, without giving the class a name.</span></span>  
  
 <span data-ttu-id="ba8bc-107">匿名型別是數學概念的 C# 實作*tuple*。</span><span class="sxs-lookup"><span data-stu-id="ba8bc-107">Anonymous types are the C# implementation of the mathematical concept of a *tuple*.</span></span> <span data-ttu-id="ba8bc-108">數學術語「Tuple」源自於 single、double、triple、quadruple、quintuple、n-tuple 序列。</span><span class="sxs-lookup"><span data-stu-id="ba8bc-108">The mathematical term tuple originated from the sequence single, double, triple, quadruple, quintuple, n-tuple.</span></span> <span data-ttu-id="ba8bc-109">這表示有限的物件順序，每個都有特定的型別。</span><span class="sxs-lookup"><span data-stu-id="ba8bc-109">It refers to a finite sequence of objects, each of a specific type.</span></span> <span data-ttu-id="ba8bc-110">有時候，這稱為成對的名稱/值清單。</span><span class="sxs-lookup"><span data-stu-id="ba8bc-110">Sometimes this is called a list of name/value pairs.</span></span> <span data-ttu-id="ba8bc-111">比方說，在地址內容[範例 XML 檔︰ 典型採購訂單 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md)無法表示 XML 文件，如下所示︰</span><span class="sxs-lookup"><span data-stu-id="ba8bc-111">For example, the contents of an address in the [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md) XML document could be expressed as follows:</span></span>  
  
```  
Name: Ellen Adams  
Street: 123 Maple Street  
City: Mill Valley  
State: CA  
Zip: 90952  
Country: USA  
```  
  
 <span data-ttu-id="ba8bc-112">當您建立匿名型別的執行個體時，將它視為建立順序 n 的 Tuple 比較方法。</span><span class="sxs-lookup"><span data-stu-id="ba8bc-112">When you create an instance of an anonymous type, it is convenient to think of it as creating a tuple of order n.</span></span> <span data-ttu-id="ba8bc-113">如果您撰寫可在 `Select` 子句中建立 Tuple 的查詢，該查詢會傳回 Tuple 的 `IEnumerable`。</span><span class="sxs-lookup"><span data-stu-id="ba8bc-113">If you write a query that creates a tuple in the `Select` clause, the query returns an `IEnumerable` of the tuple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba8bc-114">範例</span><span class="sxs-lookup"><span data-stu-id="ba8bc-114">Example</span></span>  
 <span data-ttu-id="ba8bc-115">在這個範例中，`Select` 子句會規劃匿名型別。</span><span class="sxs-lookup"><span data-stu-id="ba8bc-115">In this example, the `Select` clause projects an anonymous type.</span></span> <span data-ttu-id="ba8bc-116">然後，此範例會使用 `Dim` 來建立 `IEnumerable` 物件。</span><span class="sxs-lookup"><span data-stu-id="ba8bc-116">The example then uses `Dim` to create the `IEnumerable` object.</span></span> <span data-ttu-id="ba8bc-117">在 `For Each` 迴圈中，反覆運算變數會變成在查詢運算式中建立之匿名型別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ba8bc-117">Within the `For Each` loop, the iteration variable becomes an instance of the anonymous type created in the query expression.</span></span>  
  
 <span data-ttu-id="ba8bc-118">這個範例會使用下列 XML 文件︰[範例 XML 檔︰ 客戶和訂單 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="ba8bc-118">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim custOrd As XElement = XElement.Load("CustomersOrders.xml")  
Dim custList = _  
    From el In custOrd.<Customers>.<Customer> _  
    Select New With { _  
        .CustomerID = el.@<CustomerID>, _  
        .CompanyName = el.<CompanyName>.Value, _  
        .ContactName = el.<ContactName>.Value _  
    }  
For Each cust In custList  
    Console.WriteLine("{0}:{1}:{2}", cust.CustomerID, cust.CompanyName, cust.ContactName)  
Next  
```  
  
 <span data-ttu-id="ba8bc-119">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="ba8bc-119">This code produces the following output:</span></span>  
  
```  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a><span data-ttu-id="ba8bc-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba8bc-120">See Also</span></span>  
 [<span data-ttu-id="ba8bc-121">投影和轉換 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ba8bc-121">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)

