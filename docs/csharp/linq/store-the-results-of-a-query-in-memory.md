---
title: 將查詢的結果儲存在記憶體中
description: 如何儲存結果。
ms.date: 11/30/2016
ms.assetid: 5b863961-1750-4cf9-9607-acea5054d15a
ms.openlocfilehash: c125d134d7c1db98363844c12fc8abd3faa9c868
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="store-the-results-of-a-query-in-memory"></a><span data-ttu-id="cc703-103">將查詢的結果儲存在記憶體中</span><span class="sxs-lookup"><span data-stu-id="cc703-103">Store the results of a query in memory</span></span>

<span data-ttu-id="cc703-104">查詢基本上是如何擷取和組織資料的一組指令。</span><span class="sxs-lookup"><span data-stu-id="cc703-104">A query is basically a set of instructions for how to retrieve and organize data.</span></span> <span data-ttu-id="cc703-105">要求結果中的每個後續項目時，會延遲執行查詢。</span><span class="sxs-lookup"><span data-stu-id="cc703-105">Queries are executed lazily, as each subsequent item in the result is requested.</span></span> <span data-ttu-id="cc703-106">當您使用 `foreach` 逐一查看結果時，會將項目傳回為已存取。</span><span class="sxs-lookup"><span data-stu-id="cc703-106">When you use `foreach` to iterate the results, items are returned as accessed.</span></span> <span data-ttu-id="cc703-107">若要評估查詢，並儲存其結果，而不執行 `foreach` 迴圈，則只要在查詢變數上呼叫下列其中一種方法即可︰</span><span class="sxs-lookup"><span data-stu-id="cc703-107">To evaluate a query and store its results without executing a `foreach` loop, just call one of the following methods on the query variable:</span></span>  
  
-   <xref:System.Linq.Enumerable.ToList%2A>  
  
-   <xref:System.Linq.Enumerable.ToArray%2A>  
  
-   <xref:System.Linq.Enumerable.ToDictionary%2A>  
  
-   <xref:System.Linq.Enumerable.ToLookup%2A>  
  
 <span data-ttu-id="cc703-108">建議當您儲存查詢結果時，將傳回的集合物件指派給新的變數，如下列範例所示︰</span><span class="sxs-lookup"><span data-stu-id="cc703-108">We recommend that when you store the query results, you assign the returned collection object to a new variable as shown in the following example:</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc703-109">範例</span><span class="sxs-lookup"><span data-stu-id="cc703-109">Example</span></span>  
 [!code-csharp[csProgGuideLINQ#25](../../../samples/snippets/csharp/concepts/linq/how-to-store-the-results-of-a-query-in-memory_1.cs)]  
  

## <a name="see-also"></a><span data-ttu-id="cc703-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="cc703-110">See Also</span></span>  
 [<span data-ttu-id="cc703-111">LINQ 查詢運算式</span><span class="sxs-lookup"><span data-stu-id="cc703-111">LINQ Query Expressions</span></span>](index.md)
