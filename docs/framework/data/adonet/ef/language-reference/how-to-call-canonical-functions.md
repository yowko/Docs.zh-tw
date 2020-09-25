---
title: 如何：呼叫標準函式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b3d84873-7403-4957-8e20-b4ae39f50214
ms.openlocfilehash: acfbdbaf21fe1d454b68dfef5bf4f88d8020ea65
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204446"
---
# <a name="how-to-call-canonical-functions"></a><span data-ttu-id="24526-102">如何：呼叫標準函式</span><span class="sxs-lookup"><span data-stu-id="24526-102">How to: Call Canonical Functions</span></span>

<span data-ttu-id="24526-103"><xref:System.Data.Objects.EntityFunctions> 類別包含可公開標準函式以用於 LINQ to Entities 查詢的方法。</span><span class="sxs-lookup"><span data-stu-id="24526-103">The <xref:System.Data.Objects.EntityFunctions> class contains methods that expose canonical functions to use in LINQ to Entities queries.</span></span> <span data-ttu-id="24526-104">如需標準函式的資訊，請參閱[標準函式](canonical-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="24526-104">For information about canonical functions, see [Canonical Functions](canonical-functions.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="24526-105"><xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> 類別中的 <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> 和 <xref:System.Data.Objects.EntityFunctions> 方法沒有對等的標準函式。</span><span class="sxs-lookup"><span data-stu-id="24526-105">The <xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> and <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> methods in the <xref:System.Data.Objects.EntityFunctions> class do not have canonical function equivalents.</span></span>  
  
 <span data-ttu-id="24526-106">標準函式 (亦稱為彙總標準函式) 可直接叫用，它們會執行值集的計算，並傳回單一值。</span><span class="sxs-lookup"><span data-stu-id="24526-106">Canonical functions that perform a calculation on a set of values and return a single value (also known as aggregate canonical functions) can be directly invoked.</span></span> <span data-ttu-id="24526-107">呼叫的其他標準函式則做為 LINQ to Entities 查詢的一部份。</span><span class="sxs-lookup"><span data-stu-id="24526-107">Other canonical functions can only be called as part of a LINQ to Entities query.</span></span> <span data-ttu-id="24526-108">若要直接呼叫彙總函式，您必須將 <xref:System.Data.Objects.ObjectQuery%601> 傳遞至函式。</span><span class="sxs-lookup"><span data-stu-id="24526-108">To call an aggregate function directly, you must pass an <xref:System.Data.Objects.ObjectQuery%601> to the function.</span></span> <span data-ttu-id="24526-109">如需詳細資訊，請參閱下列第二個範例。</span><span class="sxs-lookup"><span data-stu-id="24526-109">For more information, see the second example below.</span></span>  
  
 <span data-ttu-id="24526-110">您可以在 LINQ to Entities 查詢中，使用 Common Language Runtime (CLR) 方法呼叫部分標準函式。</span><span class="sxs-lookup"><span data-stu-id="24526-110">You can call some canonical functions by using common language runtime (CLR) methods in LINQ to Entities queries.</span></span> <span data-ttu-id="24526-111">如需對應至標準函式的 CLR 方法清單，請參閱 [Clr 方法與標準](clr-method-to-canonical-function-mapping.md)函式的對應。</span><span class="sxs-lookup"><span data-stu-id="24526-111">For a list of CLR methods that map to canonical functions, see [CLR Method to Canonical Function Mapping](clr-method-to-canonical-function-mapping.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="24526-112">範例</span><span class="sxs-lookup"><span data-stu-id="24526-112">Example</span></span>  

 <span data-ttu-id="24526-113">下列範例會使用 [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)。</span><span class="sxs-lookup"><span data-stu-id="24526-113">The following example uses the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span> <span data-ttu-id="24526-114">範例執行 LINQ to Entities 查詢，使用 <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> 方法，傳回 `SellEndDate` 和 `SellStartDate` 之間的差距小於 365 天的所有產品：</span><span class="sxs-lookup"><span data-stu-id="24526-114">The example executes a LINQ to Entities query that uses the <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> method to return all products for which the difference between `SellEndDate` and `SellStartDate` is less than 365 days:</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#1)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="24526-115">範例</span><span class="sxs-lookup"><span data-stu-id="24526-115">Example</span></span>  

 <span data-ttu-id="24526-116">下列範例會使用 [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)。</span><span class="sxs-lookup"><span data-stu-id="24526-116">The following example uses the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span> <span data-ttu-id="24526-117">範例直接呼叫彙總 <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> 方法，以傳回 `SalesOrderHeader` 小計的標準差。</span><span class="sxs-lookup"><span data-stu-id="24526-117">The example calls the aggregate <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> method directly to return the standard deviation of `SalesOrderHeader` subtotals.</span></span> <span data-ttu-id="24526-118">請注意，<xref:System.Data.Objects.ObjectQuery%601> 已傳遞至函式，函式允許其接受呼叫時，不必成為 LINQ to Entities 查詢的一部份。</span><span class="sxs-lookup"><span data-stu-id="24526-118">Note that an <xref:System.Data.Objects.ObjectQuery%601> is passed to the function, which allows it to be called without being part of a LINQ to Entities query.</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#2)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="24526-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24526-119">See also</span></span>

- [<span data-ttu-id="24526-120">在 LINQ to Entities 查詢中呼叫函式</span><span class="sxs-lookup"><span data-stu-id="24526-120">Calling Functions in LINQ to Entities Queries</span></span>](calling-functions-in-linq-to-entities-queries.md)
- [<span data-ttu-id="24526-121">LINQ to Entities 中的查詢</span><span class="sxs-lookup"><span data-stu-id="24526-121">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
