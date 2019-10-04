---
title: DEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
ms.openlocfilehash: 27fc23a2be47ea00eff20aa8d2f559af5ae90387
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833898"
---
# <a name="deref-entity-sql"></a><span data-ttu-id="923cd-102">DEREF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="923cd-102">DEREF (Entity SQL)</span></span>
<span data-ttu-id="923cd-103">對參考值取值並且產生該取值的結果。</span><span class="sxs-lookup"><span data-stu-id="923cd-103">Dereferences a reference value and produces the result of that dereference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="923cd-104">語法</span><span class="sxs-lookup"><span data-stu-id="923cd-104">Syntax</span></span>  
  
```sql  
SELECT DEREF ( o.expression ) FROM Table AS o;
```  
  
## <a name="arguments"></a><span data-ttu-id="923cd-105">引數</span><span class="sxs-lookup"><span data-stu-id="923cd-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="923cd-106">傳回集合的任何有效查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="923cd-106">Any valid query expression that returns a collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="923cd-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="923cd-107">Return Value</span></span>  
 <span data-ttu-id="923cd-108">所參考之實體的值。</span><span class="sxs-lookup"><span data-stu-id="923cd-108">The value of the entity that is referenced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="923cd-109">備註</span><span class="sxs-lookup"><span data-stu-id="923cd-109">Remarks</span></span>  
 <span data-ttu-id="923cd-110">DEREF 運算子會對參考值取值並且產生該取值的結果。</span><span class="sxs-lookup"><span data-stu-id="923cd-110">The DEREF operator dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="923cd-111">例如，如果 `r` 是類型 ref @ no__t-1T > 的參考，`Deref(r)` 是會產生 `r` 所參考之實體的類型為 `T` 的運算式。</span><span class="sxs-lookup"><span data-stu-id="923cd-111">For example, if `r` is a reference of type ref\<T>, `Deref(r)` is an expression of type `T` that yields the entity referenced by `r`.</span></span> <span data-ttu-id="923cd-112">如果此參數值為 null，或為懸空 (也就是參考的目標不存在)，DEREF 運算子的結果就會是 null。</span><span class="sxs-lookup"><span data-stu-id="923cd-112">If the reference value is null, or is dangling (that is, the target of the reference does not exist), the result of the DEREF operator is null.</span></span>  
  
## <a name="example"></a><span data-ttu-id="923cd-113">範例</span><span class="sxs-lookup"><span data-stu-id="923cd-113">Example</span></span>  
 <span data-ttu-id="923cd-114">以下 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢使用 DEREF 運算子對參考值取值並且產生該取值的結果。</span><span class="sxs-lookup"><span data-stu-id="923cd-114">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the DEREF operator to dereference a reference value and produce the result of that dereference.</span></span> <span data-ttu-id="923cd-115">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="923cd-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="923cd-116">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="923cd-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="923cd-117">依照 [How 中的程式進行：執行可傳回 PrimitiveType 結果 @ no__t-0 的查詢。</span><span class="sxs-lookup"><span data-stu-id="923cd-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="923cd-118">將下列查詢當成引數傳遞至 ExecutePrimitiveTypeQuery 方法：</span><span class="sxs-lookup"><span data-stu-id="923cd-118">Pass the following query as an argument to the ExecutePrimitiveTypeQuery method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#DEREF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#deref)]  
  
## <a name="see-also"></a><span data-ttu-id="923cd-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="923cd-119">See also</span></span>

- [<span data-ttu-id="923cd-120">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="923cd-120">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="923cd-121">REF</span><span class="sxs-lookup"><span data-stu-id="923cd-121">REF</span></span>](ref-entity-sql.md)
- [<span data-ttu-id="923cd-122">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="923cd-122">CREATEREF</span></span>](createref-entity-sql.md)
- [<span data-ttu-id="923cd-123">KEY</span><span class="sxs-lookup"><span data-stu-id="923cd-123">KEY</span></span>](key-entity-sql.md)
- [<span data-ttu-id="923cd-124">可為 Null 的結構類型</span><span class="sxs-lookup"><span data-stu-id="923cd-124">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)
