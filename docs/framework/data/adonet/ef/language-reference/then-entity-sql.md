---
title: THEN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 54222642-23c6-4f61-9861-67caca53ac5f
ms.openlocfilehash: ba01a978c53b58f7e6c1ac9bc42a97277ac64bbc
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319289"
---
# <a name="then-entity-sql"></a><span data-ttu-id="6afff-102">THEN (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="6afff-102">THEN (Entity SQL)</span></span>
<span data-ttu-id="6afff-103">當 WHEN 子句評估為 `true`時，該子句的結果。</span><span class="sxs-lookup"><span data-stu-id="6afff-103">The result of a WHEN clause when it evaluates to `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6afff-104">語法</span><span class="sxs-lookup"><span data-stu-id="6afff-104">Syntax</span></span>  
  
```sql  
WHEN when_expression THEN then_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="6afff-105">引數</span><span class="sxs-lookup"><span data-stu-id="6afff-105">Arguments</span></span>  
 `when_expression`  
 <span data-ttu-id="6afff-106">任何有效的 Boolean 運算式。</span><span class="sxs-lookup"><span data-stu-id="6afff-106">Any valid Boolean expression.</span></span>  
  
 `then_expression`  
 <span data-ttu-id="6afff-107">傳回集合的任何有效查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="6afff-107">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6afff-108">備註</span><span class="sxs-lookup"><span data-stu-id="6afff-108">Remarks</span></span>  
 <span data-ttu-id="6afff-109">如果 `when_expression` 評估為 `true`值，結果就是對應的 `then-expression`。</span><span class="sxs-lookup"><span data-stu-id="6afff-109">If `when_expression` evaluates to the value `true`, the result is the corresponding `then-expression`.</span></span> <span data-ttu-id="6afff-110">如果沒有滿足任何 WHEN 條件，就會評估 `else-expression` 。</span><span class="sxs-lookup"><span data-stu-id="6afff-110">If none of the WHEN conditions are satisfied, the `else-expression` is evaluated.</span></span> <span data-ttu-id="6afff-111">不過，如果沒有任何 `else-expression`，結果就是 null。</span><span class="sxs-lookup"><span data-stu-id="6afff-111">However, if there is no `else-expression`, the result is null.</span></span>  
  
 <span data-ttu-id="6afff-112">如需範例，請參閱[案例](case-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="6afff-112">For an example, see [CASE](case-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6afff-113">範例</span><span class="sxs-lookup"><span data-stu-id="6afff-113">Example</span></span>  
 <span data-ttu-id="6afff-114">下列 Entity SQL 查詢會使用 CASE 運算式來評估一組 `Boolean` 運算式。</span><span class="sxs-lookup"><span data-stu-id="6afff-114">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions.</span></span> <span data-ttu-id="6afff-115">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="6afff-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="6afff-116">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="6afff-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="6afff-117">依照[如何：執行傳回 PrimitiveType 結果的查詢](../how-to-execute-a-query-that-returns-primitivetype-results.md)中的程式進行。</span><span class="sxs-lookup"><span data-stu-id="6afff-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="6afff-118">將下列查詢當成引數，傳遞至 `ExecutePrimitiveTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="6afff-118">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#CASE_WHEN_THEN_ELSE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="6afff-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="6afff-119">See also</span></span>

- [<span data-ttu-id="6afff-120">CASE</span><span class="sxs-lookup"><span data-stu-id="6afff-120">CASE</span></span>](case-entity-sql.md)
- [<span data-ttu-id="6afff-121">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="6afff-121">Entity SQL Reference</span></span>](entity-sql-reference.md)
