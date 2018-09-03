---
title: 從方法傳回查詢
description: 如何傳回查詢。
ms.date: 11/30/2016
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.openlocfilehash: 1c5fa534f3f39f8201d93b986e687d85bb303736
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43473940"
---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a><span data-ttu-id="88238-103">如何：從方法傳回查詢 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="88238-103">How to: Return a Query from a Method (C# Programming Guide)</span></span>
<span data-ttu-id="88238-104">這個範例示範如何以傳回值和 `out` 參數形式從方法中傳回查詢。</span><span class="sxs-lookup"><span data-stu-id="88238-104">This example shows how to return a query from a method as the return value and as an `out` parameter.</span></span>  
  
 <span data-ttu-id="88238-105">查詢物件是可編寫的，這表示您可以從方法傳回查詢。</span><span class="sxs-lookup"><span data-stu-id="88238-105">Query objects are composable, meaning that you can return a query from a method.</span></span> <span data-ttu-id="88238-106">代表查詢的物件不會儲存所產生的集合，而是在必要時產生結果的步驟。</span><span class="sxs-lookup"><span data-stu-id="88238-106">Objects that represent queries do not store the resulting collection, but rather the steps to produce the results when needed.</span></span> <span data-ttu-id="88238-107">從方法傳回查詢物件的優點，在於可以進一步編寫或修改它們。</span><span class="sxs-lookup"><span data-stu-id="88238-107">The advantage of returning query objects from methods is that they can be further composed or modified.</span></span> <span data-ttu-id="88238-108">因此，傳回查詢的方法的任何傳回值或 `out` 參數也必須具有該類型。</span><span class="sxs-lookup"><span data-stu-id="88238-108">Therefore any return value or `out` parameter of a method that returns a query must also have that type.</span></span> <span data-ttu-id="88238-109">如果方法將查詢具體化到具體 <xref:System.Collections.Generic.List%601> 或 <xref:System.Array> 類型，則會視為傳回查詢結果，而不是查詢本身。</span><span class="sxs-lookup"><span data-stu-id="88238-109">If a method materializes a query into a concrete <xref:System.Collections.Generic.List%601> or <xref:System.Array> type, it is considered to be returning the query results instead of the query itself.</span></span> <span data-ttu-id="88238-110">從方法傳回的查詢變數仍然可以進行編寫或修改。</span><span class="sxs-lookup"><span data-stu-id="88238-110">A query variable that is returned from a method can still be composed or modified.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88238-111">範例</span><span class="sxs-lookup"><span data-stu-id="88238-111">Example</span></span>  
 <span data-ttu-id="88238-112">在下列範例中，第一個方法會以傳回值形式傳回查詢，第二個方法會以 `out` 參數形式傳回查詢。</span><span class="sxs-lookup"><span data-stu-id="88238-112">In the following example, the first method returns a query as a return value, and the second method returns a query as an `out` parameter.</span></span> <span data-ttu-id="88238-113">請注意，在這兩種情況下，它是傳回的查詢，而不是查詢結果。</span><span class="sxs-lookup"><span data-stu-id="88238-113">Note that in both cases it is a query that is  returned, not query results.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#80](~/samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a><span data-ttu-id="88238-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="88238-114">See Also</span></span>

- [<span data-ttu-id="88238-115">Language-Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="88238-115">Language Integrated Query (LINQ)</span></span>](index.md)
