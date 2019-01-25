---
title: SET (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 28b4deac-c7e4-4f09-b428-4d352ef2dc94
ms.openlocfilehash: b6adce314e5d4fb1e4077b0efef758d07444e496
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54744436"
---
# <a name="set-entity-sql"></a><span data-ttu-id="bdc4c-102">SET (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="bdc4c-102">SET (Entity SQL)</span></span>
<span data-ttu-id="bdc4c-103">SET 運算式會產生移除所有重複項目的新集合，利用這種方式將物件的集合轉換成集合。</span><span class="sxs-lookup"><span data-stu-id="bdc4c-103">The SET expression is used to convert a collection of objects into a set by yielding a new collection with all duplicate elements removed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdc4c-104">語法</span><span class="sxs-lookup"><span data-stu-id="bdc4c-104">Syntax</span></span>  
  
```  
SET ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="bdc4c-105">引數</span><span class="sxs-lookup"><span data-stu-id="bdc4c-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="bdc4c-106">傳回集合的任何有效查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="bdc4c-106">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bdc4c-107">備註</span><span class="sxs-lookup"><span data-stu-id="bdc4c-107">Remarks</span></span>  
 <span data-ttu-id="bdc4c-108">SET 運算式 `SET(c)` 在邏輯上相當於下列 SELECT 陳述式 (Statement)：</span><span class="sxs-lookup"><span data-stu-id="bdc4c-108">The set expression `SET(c)` is logically equivalent to the following select statement:</span></span>  
  
```  
SELECT VALUE DISTINCT c FROM c  
```  
  
 <span data-ttu-id="bdc4c-109">`SET` 是其中一個 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子。</span><span class="sxs-lookup"><span data-stu-id="bdc4c-109">`SET` is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="bdc4c-110">所有 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子都會從左到右評估。</span><span class="sxs-lookup"><span data-stu-id="bdc4c-110">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="bdc4c-111">請參閱[EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md)的優先順序資訊[!INCLUDE[esql](../../../../../../includes/esql-md.md)]設定運算子。</span><span class="sxs-lookup"><span data-stu-id="bdc4c-111">See [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bdc4c-112">範例</span><span class="sxs-lookup"><span data-stu-id="bdc4c-112">Example</span></span>  
 <span data-ttu-id="bdc4c-113">下列 Entity SQL 查詢會使用 SET 運算式，將物件的集合 (Collection) 轉換成單一集合 (Set)。</span><span class="sxs-lookup"><span data-stu-id="bdc4c-113">The following Entity SQL query uses the SET expression to convert a collection of objects into a set.</span></span> <span data-ttu-id="bdc4c-114">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="bdc4c-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="bdc4c-115">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="bdc4c-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="bdc4c-116">請依照下列中的程序[How to:執行可傳回 PrimitiveType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)。</span><span class="sxs-lookup"><span data-stu-id="bdc4c-116">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="bdc4c-117">將下列查詢當成引數，傳遞至 `ExecutePrimitiveTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="bdc4c-117">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#SET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#set)]  
  
## <a name="see-also"></a><span data-ttu-id="bdc4c-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bdc4c-118">See also</span></span>
- [<span data-ttu-id="bdc4c-119">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="bdc4c-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
