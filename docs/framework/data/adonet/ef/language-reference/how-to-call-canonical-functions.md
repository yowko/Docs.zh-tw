---
title: 如何：呼叫標準函式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b3d84873-7403-4957-8e20-b4ae39f50214
ms.openlocfilehash: 7ad7f79cb41b5d4821a910ede7f955b4f0fe6fab
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-call-canonical-functions"></a><span data-ttu-id="53750-102">如何：呼叫標準函式</span><span class="sxs-lookup"><span data-stu-id="53750-102">How to: Call Canonical Functions</span></span>
<span data-ttu-id="53750-103"><xref:System.Data.Objects.EntityFunctions> 類別包含可公開標準函式以用於 LINQ to Entities 查詢的方法。</span><span class="sxs-lookup"><span data-stu-id="53750-103">The <xref:System.Data.Objects.EntityFunctions> class contains methods that expose canonical functions to use in LINQ to Entities queries.</span></span> <span data-ttu-id="53750-104">如需標準函式的資訊，請參閱[標準函式](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="53750-104">For information about canonical functions, see [Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53750-105"><xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> 類別中的 <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> 和 <xref:System.Data.Objects.EntityFunctions> 方法沒有對等的標準函式。</span><span class="sxs-lookup"><span data-stu-id="53750-105">The <xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> and <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> methods in the <xref:System.Data.Objects.EntityFunctions> class do not have canonical function equivalents.</span></span>  
  
 <span data-ttu-id="53750-106">標準函式 (亦稱為彙總標準函式) 可直接叫用，它們會執行值集的計算，並傳回單一值。</span><span class="sxs-lookup"><span data-stu-id="53750-106">Canonical functions that perform a calculation on a set of values and return a single value (also known as aggregate canonical functions) can be directly invoked.</span></span> <span data-ttu-id="53750-107">呼叫的其他標準函式則做為 LINQ to Entities 查詢的一部份。</span><span class="sxs-lookup"><span data-stu-id="53750-107">Other canonical functions can only be called as part of a LINQ to Entities query.</span></span> <span data-ttu-id="53750-108">若要直接呼叫彙總函式，您必須將 <xref:System.Data.Objects.ObjectQuery%601> 傳遞至函式。</span><span class="sxs-lookup"><span data-stu-id="53750-108">To call an aggregate function directly, you must pass an <xref:System.Data.Objects.ObjectQuery%601> to the function.</span></span> <span data-ttu-id="53750-109">如需詳細資訊，請參閱下列第二個範例。</span><span class="sxs-lookup"><span data-stu-id="53750-109">For more information, see the second example below.</span></span>  
  
 <span data-ttu-id="53750-110">您可以在 LINQ to Entities 查詢中，使用 Common Language Runtime (CLR) 方法呼叫部分標準函式。</span><span class="sxs-lookup"><span data-stu-id="53750-110">You can call some canonical functions by using common language runtime (CLR) methods in LINQ to Entities queries.</span></span> <span data-ttu-id="53750-111">如需 CLR 方法對應到標準函式的清單，請參閱[標準函式對應的 CLR 方法](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md)。</span><span class="sxs-lookup"><span data-stu-id="53750-111">For a list of CLR methods that map to canonical functions, see [CLR Method to Canonical Function Mapping](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="53750-112">範例</span><span class="sxs-lookup"><span data-stu-id="53750-112">Example</span></span>  
 <span data-ttu-id="53750-113">下列範例會使用[AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832)。</span><span class="sxs-lookup"><span data-stu-id="53750-113">The following example uses the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832).</span></span> <span data-ttu-id="53750-114">範例執行 LINQ to Entities 查詢，使用 <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> 方法，傳回 `SellEndDate` 和 `SellStartDate` 之間的差距小於 365 天的所有產品：</span><span class="sxs-lookup"><span data-stu-id="53750-114">The example executes a LINQ to Entities query that uses the <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> method to return all products for which the difference between `SellEndDate` and `SellStartDate` is less than 365 days:</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#1)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="53750-115">範例</span><span class="sxs-lookup"><span data-stu-id="53750-115">Example</span></span>  
 <span data-ttu-id="53750-116">下列範例會使用[AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832)。</span><span class="sxs-lookup"><span data-stu-id="53750-116">The following example uses the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832).</span></span> <span data-ttu-id="53750-117">範例直接呼叫彙總 <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> 方法，以傳回 `SalesOrderHeader` 小計的標準差。</span><span class="sxs-lookup"><span data-stu-id="53750-117">The example calls the aggregate <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> method directly to return the standard deviation of `SalesOrderHeader` subtotals.</span></span> <span data-ttu-id="53750-118">請注意，<xref:System.Data.Objects.ObjectQuery%601> 已傳遞至函式，函式允許其接受呼叫時，不必成為 LINQ to Entities 查詢的一部份。</span><span class="sxs-lookup"><span data-stu-id="53750-118">Note that an <xref:System.Data.Objects.ObjectQuery%601> is passed to the function, which allows it to be called without being part of a LINQ to Entities query.</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#2)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="53750-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53750-119">See Also</span></span>  
 [<span data-ttu-id="53750-120">在 LINQ to Entities 查詢中呼叫函式</span><span class="sxs-lookup"><span data-stu-id="53750-120">Calling Functions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)  
 [<span data-ttu-id="53750-121">LINQ to Entities 中的查詢</span><span class="sxs-lookup"><span data-stu-id="53750-121">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
