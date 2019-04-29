---
title: DEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
ms.openlocfilehash: 1ba562ba6542e6ab0d62f1f8348434ae4f4c9b13
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785303"
---
# <a name="deref-entity-sql"></a><span data-ttu-id="ce6d2-102">DEREF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ce6d2-102">DEREF (Entity SQL)</span></span>
<span data-ttu-id="ce6d2-103">對參考值取值並且產生該取值的結果。</span><span class="sxs-lookup"><span data-stu-id="ce6d2-103">Dereferences a reference value and produces the result of that dereference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce6d2-104">語法</span><span class="sxs-lookup"><span data-stu-id="ce6d2-104">Syntax</span></span>  
  
```  
SELECT DEREF ( o.expression ) from Table as o;  
```  
  
## <a name="arguments"></a><span data-ttu-id="ce6d2-105">引數</span><span class="sxs-lookup"><span data-stu-id="ce6d2-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="ce6d2-106">傳回集合的任何有效查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="ce6d2-106">Any valid query expression that returns a collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ce6d2-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="ce6d2-107">Return Value</span></span>  
 <span data-ttu-id="ce6d2-108">所參考之實體的值。</span><span class="sxs-lookup"><span data-stu-id="ce6d2-108">The value of the entity that is referenced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce6d2-109">備註</span><span class="sxs-lookup"><span data-stu-id="ce6d2-109">Remarks</span></span>  
 <span data-ttu-id="ce6d2-110">DEREF 運算子會對參考值取值並且產生該取值的結果。</span><span class="sxs-lookup"><span data-stu-id="ce6d2-110">The DEREF operator dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="ce6d2-111">例如，如果`r`是型別參考的參考\<T >，`Deref(r)`是類型的運算式`T`產生參考之實體`r`。</span><span class="sxs-lookup"><span data-stu-id="ce6d2-111">For example, if `r` is a reference of type ref\<T>, `Deref(r)` is an expression of type `T` that yields the entity referenced by `r`.</span></span> <span data-ttu-id="ce6d2-112">如果此參數值為 null，或為懸空 (也就是參考的目標不存在)，DEREF 運算子的結果就會是 null。</span><span class="sxs-lookup"><span data-stu-id="ce6d2-112">If the reference value is null, or is dangling (that is, the target of the reference does not exist), the result of the DEREF operator is null.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce6d2-113">範例</span><span class="sxs-lookup"><span data-stu-id="ce6d2-113">Example</span></span>  
 <span data-ttu-id="ce6d2-114">以下 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢使用 DEREF 運算子對參考值取值並且產生該取值的結果。</span><span class="sxs-lookup"><span data-stu-id="ce6d2-114">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the DEREF operator to dereference a reference value and produce the result of that dereference.</span></span> <span data-ttu-id="ce6d2-115">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="ce6d2-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ce6d2-116">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="ce6d2-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="ce6d2-117">請依照下列中的程序[How to:執行可傳回 PrimitiveType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)。</span><span class="sxs-lookup"><span data-stu-id="ce6d2-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="ce6d2-118">將下列查詢當成引數傳遞至 ExecutePrimitiveTypeQuery 方法：</span><span class="sxs-lookup"><span data-stu-id="ce6d2-118">Pass the following query as an argument to the ExecutePrimitiveTypeQuery method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#DEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#deref)]  
  
## <a name="see-also"></a><span data-ttu-id="ce6d2-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce6d2-119">See also</span></span>

- [<span data-ttu-id="ce6d2-120">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="ce6d2-120">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="ce6d2-121">REF</span><span class="sxs-lookup"><span data-stu-id="ce6d2-121">REF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)
- [<span data-ttu-id="ce6d2-122">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="ce6d2-122">CREATEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)
- [<span data-ttu-id="ce6d2-123">KEY</span><span class="sxs-lookup"><span data-stu-id="ce6d2-123">KEY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)
- [<span data-ttu-id="ce6d2-124">可為 Null 的結構類型</span><span class="sxs-lookup"><span data-stu-id="ce6d2-124">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
