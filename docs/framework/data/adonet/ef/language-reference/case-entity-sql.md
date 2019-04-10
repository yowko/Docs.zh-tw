---
title: CASE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 26a47873-e87d-4ba2-9e2c-3787c21efe89
ms.openlocfilehash: e44f48d040fc77bf702759be0c53a618cd84f9fc
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59334883"
---
# <a name="case-entity-sql"></a><span data-ttu-id="fb8be-102">CASE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="fb8be-102">CASE (Entity SQL)</span></span>
<span data-ttu-id="fb8be-103">評估一組 `Boolean` 運算式，以便判斷結果。</span><span class="sxs-lookup"><span data-stu-id="fb8be-103">Evaluates a set of `Boolean` expressions to determine the result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb8be-104">語法</span><span class="sxs-lookup"><span data-stu-id="fb8be-104">Syntax</span></span>  
  
```  
CASE  
     WHEN Boolean_expression THEN result_expression   
    [ ...n ]   
     [   
    ELSE else_result_expression   
     ]   
END  
```  
  
## <a name="arguments"></a><span data-ttu-id="fb8be-105">引數</span><span class="sxs-lookup"><span data-stu-id="fb8be-105">Arguments</span></span>  
 `n`  
 <span data-ttu-id="fb8be-106">這是一個預留位置，表示可以使用多個 WHEN `Boolean_expression` THEN `result_expression` 子句。</span><span class="sxs-lookup"><span data-stu-id="fb8be-106">Is a placeholder that indicates that multiple WHEN `Boolean_expression` THEN `result_expression` clauses can be used.</span></span>  
  
 <span data-ttu-id="fb8be-107">THEN</span><span class="sxs-lookup"><span data-stu-id="fb8be-107">THEN</span></span> `result_expression`  
 <span data-ttu-id="fb8be-108">是在 `Boolean_expression` 評估為 `true`時傳回的運算式。</span><span class="sxs-lookup"><span data-stu-id="fb8be-108">Is the expression returned when `Boolean_expression` evaluates to `true`.</span></span> `result expression` <span data-ttu-id="fb8be-109">是任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="fb8be-109">is any valid expression.</span></span>  
  
 <span data-ttu-id="fb8be-110">ELSE</span><span class="sxs-lookup"><span data-stu-id="fb8be-110">ELSE</span></span> `else_result_expression`  
 <span data-ttu-id="fb8be-111">這是沒有任何比較作業評估為 `true`時，所傳回的運算式。</span><span class="sxs-lookup"><span data-stu-id="fb8be-111">Is the expression returned if no comparison operation evaluates to `true`.</span></span> <span data-ttu-id="fb8be-112">如果省略這個引數，而且沒有比較作業評估為 `true`，CASE 便傳回 null。</span><span class="sxs-lookup"><span data-stu-id="fb8be-112">If this argument is omitted and no comparison operation evaluates to `true`, CASE returns null.</span></span> `else_result_expression` <span data-ttu-id="fb8be-113">是任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="fb8be-113">is any valid expression.</span></span> <span data-ttu-id="fb8be-114">`else_result_expression` 和任何 `result_expression` 的資料型別都必須相同，或必須為隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="fb8be-114">The data types of `else_result_expression` and any `result_expression` must be the same or must be an implicit conversion.</span></span>  
  
 <span data-ttu-id="fb8be-115">WHEN</span><span class="sxs-lookup"><span data-stu-id="fb8be-115">WHEN</span></span> `Boolean_expression`  
 <span data-ttu-id="fb8be-116">這是使用搜尋的 CASE 格式時所評估的 `Boolean` 運算式。</span><span class="sxs-lookup"><span data-stu-id="fb8be-116">Is the `Boolean` expression evaluated when the searched CASE format is used.</span></span> `Boolean_expression` <span data-ttu-id="fb8be-117">任何有效`Boolean`運算式。</span><span class="sxs-lookup"><span data-stu-id="fb8be-117">is any valid `Boolean` expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fb8be-118">傳回值</span><span class="sxs-lookup"><span data-stu-id="fb8be-118">Return Value</span></span>  
 <span data-ttu-id="fb8be-119">從 `result_expression` 和選擇性 `else_result_expression`的型別集中，傳回優先順序最高的型別。</span><span class="sxs-lookup"><span data-stu-id="fb8be-119">Returns the highest precedence type from the set of types in the `result_expression` and the optional `else_result_expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb8be-120">備註</span><span class="sxs-lookup"><span data-stu-id="fb8be-120">Remarks</span></span>  
 <span data-ttu-id="fb8be-121">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] CASE 運算式與 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] CASE 運算式很相似。</span><span class="sxs-lookup"><span data-stu-id="fb8be-121">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] case expression resembles the [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] case expression.</span></span> <span data-ttu-id="fb8be-122">您可以使用 CASE 運算式來進行一連串條件式測試，以便判斷哪一個運算式會產生適當的結果。</span><span class="sxs-lookup"><span data-stu-id="fb8be-122">You use the case expression to make a series of conditional tests to determine which expression will yield the appropriate result.</span></span> <span data-ttu-id="fb8be-123">這種 CASE 運算式形式會套用至一個或多個 `Boolean` 運算式，以便判斷正確的結果運算式。</span><span class="sxs-lookup"><span data-stu-id="fb8be-123">This form of the case expression applies to a series of one or more `Boolean` expressions to determine the correct resulting expression.</span></span>  
  
 <span data-ttu-id="fb8be-124">CASE 函式會按照指定的順序針對每個 WHEN 子句評估 `Boolean_expression` ，然後傳回評估為 `result_expression` 之第一個 `Boolean_expression` 的 `true`。</span><span class="sxs-lookup"><span data-stu-id="fb8be-124">The CASE function evaluates `Boolean_expression` for each WHEN clause in the order specified, and returns `result_expression` of the first `Boolean_expression` that evaluates to `true`.</span></span> <span data-ttu-id="fb8be-125">此時，系統就不會評估其餘運算式。</span><span class="sxs-lookup"><span data-stu-id="fb8be-125">The remaining expressions are not evaluated.</span></span> <span data-ttu-id="fb8be-126">如果沒有任何 `Boolean_expression` 評估為 `true`，Database Engine 就會傳回 `else_result_expression` (如果指定了 ELSE 子句) 或 null 值 (如果沒有指定任何 ELSE 子句)。</span><span class="sxs-lookup"><span data-stu-id="fb8be-126">If no `Boolean_expression` evaluates to `true`, the Database Engine returns the `else_result_expression` if an ELSE clause is specified, or a null value if no ELSE clause is specified.</span></span>  
  
 <span data-ttu-id="fb8be-127">CASE 陳述式無法傳回多重集 (Multiset)。</span><span class="sxs-lookup"><span data-stu-id="fb8be-127">A CASE statement cannot return a multiset.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb8be-128">範例</span><span class="sxs-lookup"><span data-stu-id="fb8be-128">Example</span></span>  
 <span data-ttu-id="fb8be-129">下列 Entity SQL 查詢會使用 CASE 運算式來評估一組 `Boolean` 運算式，以便判斷結果。</span><span class="sxs-lookup"><span data-stu-id="fb8be-129">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions in order to determine the result.</span></span> <span data-ttu-id="fb8be-130">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="fb8be-130">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="fb8be-131">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="fb8be-131">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="fb8be-132">請依照下列中的程序[How to:執行可傳回 PrimitiveType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)。</span><span class="sxs-lookup"><span data-stu-id="fb8be-132">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="fb8be-133">將下列查詢當成引數，傳遞至 `ExecutePrimitiveTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="fb8be-133">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="fb8be-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb8be-134">See also</span></span>

- [<span data-ttu-id="fb8be-135">THEN</span><span class="sxs-lookup"><span data-stu-id="fb8be-135">THEN</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/then-entity-sql.md)
- [<span data-ttu-id="fb8be-136">SELECT</span><span class="sxs-lookup"><span data-stu-id="fb8be-136">SELECT</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)
- [<span data-ttu-id="fb8be-137">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="fb8be-137">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
