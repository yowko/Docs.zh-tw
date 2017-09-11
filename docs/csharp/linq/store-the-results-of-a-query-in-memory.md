---
title: "將查詢的結果儲存在記憶體中"
description: "如何儲存結果。"
keywords: ".NET、.NET Core、C#"
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 5b863961-1750-4cf9-9607-acea5054d15a
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 35d908bde06ef55ba2dc93a73211f7be33b9332c
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="store-the-results-of-a-query-in-memory"></a><span data-ttu-id="17ecb-104">將查詢的結果儲存在記憶體中</span><span class="sxs-lookup"><span data-stu-id="17ecb-104">Store the results of a query in memory</span></span>

<span data-ttu-id="17ecb-105">查詢基本上是如何擷取和組織資料的一組指令。</span><span class="sxs-lookup"><span data-stu-id="17ecb-105">A query is basically a set of instructions for how to retrieve and organize data.</span></span> <span data-ttu-id="17ecb-106">要求結果中的每個後續項目時，會延遲執行查詢。</span><span class="sxs-lookup"><span data-stu-id="17ecb-106">Queries are executed lazily, as each subsequent item in the result is requested.</span></span> <span data-ttu-id="17ecb-107">當您使用 `foreach` 逐一查看結果時，會將項目傳回為已存取。</span><span class="sxs-lookup"><span data-stu-id="17ecb-107">When you use `foreach` to iterate the results, items are returned as accessed.</span></span> <span data-ttu-id="17ecb-108">若要評估查詢，並儲存其結果，而不執行 `foreach` 迴圈，則只要在查詢變數上呼叫下列其中一種方法即可︰</span><span class="sxs-lookup"><span data-stu-id="17ecb-108">To evaluate a query and store its results without executing a `foreach` loop, just call one of the following methods on the query variable:</span></span>  
  
-   <xref:System.Linq.Enumerable.ToList%2A>  
  
-   <xref:System.Linq.Enumerable.ToArray%2A>  
  
-   <xref:System.Linq.Enumerable.ToDictionary%2A>  
  
-   <xref:System.Linq.Enumerable.ToLookup%2A>  
  
 <span data-ttu-id="17ecb-109">建議當您儲存查詢結果時，將傳回的集合物件指派給新的變數，如下列範例所示︰</span><span class="sxs-lookup"><span data-stu-id="17ecb-109">We recommend that when you store the query results, you assign the returned collection object to a new variable as shown in the following example:</span></span>  
  
## <a name="example"></a><span data-ttu-id="17ecb-110">範例</span><span class="sxs-lookup"><span data-stu-id="17ecb-110">Example</span></span>  
 <span data-ttu-id="17ecb-111">[!code-cs[csProgGuideLINQ#25](../../../samples/snippets/csharp/concepts/linq/how-to-store-the-results-of-a-query-in-memory_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="17ecb-111">[!code-cs[csProgGuideLINQ#25](../../../samples/snippets/csharp/concepts/linq/how-to-store-the-results-of-a-query-in-memory_1.cs)]</span></span>  
  

## <a name="see-also"></a><span data-ttu-id="17ecb-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17ecb-112">See Also</span></span>  
 [<span data-ttu-id="17ecb-113">LINQ 查詢運算式</span><span class="sxs-lookup"><span data-stu-id="17ecb-113">LINQ Query Expressions</span></span>](index.md)

