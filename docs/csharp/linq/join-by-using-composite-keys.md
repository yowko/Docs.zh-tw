---
title: "使用複合索引鍵執行聯結"
description: "如何使用複合索引鍵執行聯結。"
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: da70b54d-3213-45eb-8437-fbe75cbcf935
ms.openlocfilehash: c285e768d64d1da7e428e29fc67838e87575500c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="join-by-using-composite-keys"></a><span data-ttu-id="12872-104">使用複合索引鍵執行聯結</span><span class="sxs-lookup"><span data-stu-id="12872-104">Join by using composite keys</span></span>

<span data-ttu-id="12872-105">此範例示範如何執行聯結作業，您想要在其中使用多個索引鍵來定義比對項目。</span><span class="sxs-lookup"><span data-stu-id="12872-105">This example shows how to perform join operations in which you want to use more than one key to define a match.</span></span> <span data-ttu-id="12872-106">使用複合索引鍵便可完成這項定義。</span><span class="sxs-lookup"><span data-stu-id="12872-106">This is accomplished by using a composite key.</span></span> <span data-ttu-id="12872-107">您會將複合索引鍵建立成匿名型別，或是包含要比較之值的具名型別。</span><span class="sxs-lookup"><span data-stu-id="12872-107">You create a composite key as an anonymous type or named typed with the values that you want to compare.</span></span> <span data-ttu-id="12872-108">如果將跨方法界限傳遞查詢變數，請使用可覆寫索引鍵之 <xref:System.Object.Equals%2A> 和 <xref:System.Object.GetHashCode%2A> 的具名類型。</span><span class="sxs-lookup"><span data-stu-id="12872-108">If the query variable will be passed across method boundaries, use a named type that overrides <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> for the key.</span></span> <span data-ttu-id="12872-109">在每個索引鍵中，這些屬性的名稱及其出現的順序都必須相同。</span><span class="sxs-lookup"><span data-stu-id="12872-109">The names of the properties, and the order in which they occur, must be identical in each key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12872-110">範例</span><span class="sxs-lookup"><span data-stu-id="12872-110">Example</span></span>  
 <span data-ttu-id="12872-111">下列範例示範如何使用複合索引鍵來聯結來自三個資料表的資料：</span><span class="sxs-lookup"><span data-stu-id="12872-111">The following example demonstrates how to use a composite key to join data from three tables:</span></span>  
  
```csharp  
var query = from o in db.Orders  
    from p in db.Products  
    join d in db.OrderDetails   
        on new {o.OrderID, p.ProductID} equals new {d.OrderID,        d.ProductID} into details  
        from d in details  
        select new {o.OrderID, p.ProductID, d.UnitPrice};  
```  
  
 <span data-ttu-id="12872-112">複合索引鍵上的型別推斷，會根據索引鍵中的屬性名稱及其出現的順序來進行。</span><span class="sxs-lookup"><span data-stu-id="12872-112">Type inference on composite keys depends on the names of the properties in the keys, and the order in which they occur.</span></span> <span data-ttu-id="12872-113">如果來源序列中的屬性沒有相同名稱，您就必須在索引鍵中指派新的名稱。</span><span class="sxs-lookup"><span data-stu-id="12872-113">If the properties in the source sequences do not have the same names, you must assign new names in the keys.</span></span> <span data-ttu-id="12872-114">例如，如果 `Orders` 資料表和 `OrderDetails` 資料表分別對其資料行使用不同的名稱，您就可以在匿名型別中指派相同的名稱以建立複合索引鍵：</span><span class="sxs-lookup"><span data-stu-id="12872-114">For example, if the `Orders` table and `OrderDetails` table each used different names for their columns, you could create composite keys by assigning identical names in the anonymous types:</span></span>  
  
```csharp  
join...on new {Name = o.CustomerName, ID = o.CustID} equals   
    new {Name = d.CustName, ID = d.CustID }  
```  
  
 <span data-ttu-id="12872-115">複合索引鍵也可用於 `group` 子句。</span><span class="sxs-lookup"><span data-stu-id="12872-115">Composite keys can be also used in a `group` clause.</span></span>  

## <a name="see-also"></a><span data-ttu-id="12872-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="12872-116">See also</span></span>  
 [<span data-ttu-id="12872-117">LINQ 查詢運算式</span><span class="sxs-lookup"><span data-stu-id="12872-117">LINQ query expressions</span></span>](index.md)  
 [<span data-ttu-id="12872-118">join 子句</span><span class="sxs-lookup"><span data-stu-id="12872-118">join clause</span></span>](../language-reference/keywords/join-clause.md)  
 [<span data-ttu-id="12872-119">group 子句</span><span class="sxs-lookup"><span data-stu-id="12872-119">group clause</span></span>](../language-reference/keywords/group-clause.md)
