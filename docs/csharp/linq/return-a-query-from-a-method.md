---
title: "從方法傳回查詢"
description: "如何傳回查詢。"
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.openlocfilehash: c1b69e3f5f0cd2c50ae80d2454e6b7f13dc30344
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2017
---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a><span data-ttu-id="e3bca-104">如何：從方法傳回查詢 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="e3bca-104">How to: Return a Query from a Method (C# Programming Guide)</span></span>
<span data-ttu-id="e3bca-105">這個範例示範如何以傳回值和 `out` 參數形式從方法中傳回查詢。</span><span class="sxs-lookup"><span data-stu-id="e3bca-105">This example shows how to return a query from a method as the return value and as an `out` parameter.</span></span>  
  
 <span data-ttu-id="e3bca-106">查詢物件是可編寫的，這表示您可以從方法傳回查詢。</span><span class="sxs-lookup"><span data-stu-id="e3bca-106">Query objects are composable, meaning that you can return a query from a method.</span></span> <span data-ttu-id="e3bca-107">代表查詢的物件不會儲存所產生的集合，而是在必要時產生結果的步驟。</span><span class="sxs-lookup"><span data-stu-id="e3bca-107">Objects that represent queries do not store the resulting collection, but rather the steps to produce the results when needed.</span></span> <span data-ttu-id="e3bca-108">從方法傳回查詢物件的優點，在於可以進一步編寫或修改它們。</span><span class="sxs-lookup"><span data-stu-id="e3bca-108">The advantage of returning query objects from methods is that they can be further composed or modified.</span></span> <span data-ttu-id="e3bca-109">因此，傳回查詢的方法的任何傳回值或 `out` 參數也必須具有該類型。</span><span class="sxs-lookup"><span data-stu-id="e3bca-109">Therefore any return value or `out` parameter of a method that returns a query must also have that type.</span></span> <span data-ttu-id="e3bca-110">如果方法將查詢具體化到具體 <xref:System.Collections.Generic.List%601> 或 <xref:System.Array> 類型，則會視為傳回查詢結果，而不是查詢本身。</span><span class="sxs-lookup"><span data-stu-id="e3bca-110">If a method materializes a query into a concrete <xref:System.Collections.Generic.List%601> or <xref:System.Array> type, it is considered to be returning the query results instead of the query itself.</span></span> <span data-ttu-id="e3bca-111">從方法傳回的查詢變數仍然可以進行編寫或修改。</span><span class="sxs-lookup"><span data-stu-id="e3bca-111">A query variable that is returned from a method can still be composed or modified.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3bca-112">範例</span><span class="sxs-lookup"><span data-stu-id="e3bca-112">Example</span></span>  
 <span data-ttu-id="e3bca-113">在下列範例中，第一個方法會以傳回值形式傳回查詢，第二個方法會以 `out` 參數形式傳回查詢。</span><span class="sxs-lookup"><span data-stu-id="e3bca-113">In the following example, the first method returns a query as a return value, and the second method returns a query as an `out` parameter.</span></span> <span data-ttu-id="e3bca-114">請注意，在這兩種情況下，它是傳回的查詢，而不是查詢結果。</span><span class="sxs-lookup"><span data-stu-id="e3bca-114">Note that in both cases it is a query that is  returned, not query results.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#80](../../../samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a><span data-ttu-id="e3bca-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3bca-115">See Also</span></span>  
 [<span data-ttu-id="e3bca-116">LINQ 查詢運算式</span><span class="sxs-lookup"><span data-stu-id="e3bca-116">LINQ Query Expressions</span></span>](index.md)
