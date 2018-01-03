---
title: THEN (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54222642-23c6-4f61-9861-67caca53ac5f
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ecf46b122ec5411913891aa1e33bee071044d032
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="then-entity-sql"></a><span data-ttu-id="03895-102">THEN (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="03895-102">THEN (Entity SQL)</span></span>
<span data-ttu-id="03895-103">當 WHEN 子句評估為 `true`時，該子句的結果。</span><span class="sxs-lookup"><span data-stu-id="03895-103">The result of a WHEN clause when it evaluates to `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03895-104">語法</span><span class="sxs-lookup"><span data-stu-id="03895-104">Syntax</span></span>  
  
```  
WHEN when_expression THEN then_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="03895-105">引數</span><span class="sxs-lookup"><span data-stu-id="03895-105">Arguments</span></span>  
 `when_expression`  
 <span data-ttu-id="03895-106">任何有效的 Boolean 運算式。</span><span class="sxs-lookup"><span data-stu-id="03895-106">Any valid Boolean expression.</span></span>  
  
 `then_expression`  
 <span data-ttu-id="03895-107">傳回集合的任何有效查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="03895-107">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03895-108">備註</span><span class="sxs-lookup"><span data-stu-id="03895-108">Remarks</span></span>  
 <span data-ttu-id="03895-109">如果 `when_expression` 評估為 `true`值，結果就是對應的 `then-expression`。</span><span class="sxs-lookup"><span data-stu-id="03895-109">If `when_expression` evaluates to the value `true`, the result is the corresponding `then-expression`.</span></span> <span data-ttu-id="03895-110">如果沒有滿足任何 WHEN 條件，就會評估 `else-expression` 。</span><span class="sxs-lookup"><span data-stu-id="03895-110">If none of the WHEN conditions are satisfied, the `else-expression` is evaluated.</span></span> <span data-ttu-id="03895-111">不過，如果沒有任何 `else-expression`，結果就是 null。</span><span class="sxs-lookup"><span data-stu-id="03895-111">However, if there is no `else-expression`, the result is null.</span></span>  
  
 <span data-ttu-id="03895-112">如需範例，請參閱[案例](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="03895-112">For an example, see [CASE](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="03895-113">範例</span><span class="sxs-lookup"><span data-stu-id="03895-113">Example</span></span>  
 <span data-ttu-id="03895-114">下列 Entity SQL 查詢會使用 CASE 運算式來評估一組 `Boolean` 運算式。</span><span class="sxs-lookup"><span data-stu-id="03895-114">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions.</span></span> <span data-ttu-id="03895-115">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="03895-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="03895-116">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="03895-116">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="03895-117">請依照下列中的程序[如何： 執行查詢，傳回 PrimitiveType 結果](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)。</span><span class="sxs-lookup"><span data-stu-id="03895-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="03895-118">將下列查詢當成引數，傳遞至 `ExecutePrimitiveTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="03895-118">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="03895-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="03895-119">See Also</span></span>  
 [<span data-ttu-id="03895-120">CASE</span><span class="sxs-lookup"><span data-stu-id="03895-120">CASE</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md)  
 [<span data-ttu-id="03895-121">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="03895-121">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
