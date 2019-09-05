---
title: EXISTS (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d28ead43-4afb-4bdc-af64-efd2e05005d7
ms.openlocfilehash: 20e18bf536f2b89eca9515b3c5dca7ca7fbd6fe5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250995"
---
# <a name="exists-entity-sql"></a><span data-ttu-id="e1bf9-102">EXISTS (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e1bf9-102">EXISTS (Entity SQL)</span></span>
<span data-ttu-id="e1bf9-103">判斷集合是否為空。</span><span class="sxs-lookup"><span data-stu-id="e1bf9-103">Determines if a collection is empty.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1bf9-104">語法</span><span class="sxs-lookup"><span data-stu-id="e1bf9-104">Syntax</span></span>  
  
```  
[NOT] EXISTS ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="e1bf9-105">引數</span><span class="sxs-lookup"><span data-stu-id="e1bf9-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="e1bf9-106">可傳回集合的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="e1bf9-106">Any valid expression that returns a collection.</span></span>  
  
 <span data-ttu-id="e1bf9-107">NOT</span><span class="sxs-lookup"><span data-stu-id="e1bf9-107">NOT</span></span>  
 <span data-ttu-id="e1bf9-108">指定 EXISTS 的結果為否定運算。</span><span class="sxs-lookup"><span data-stu-id="e1bf9-108">Specifies that the result of EXISTS be negated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e1bf9-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="e1bf9-109">Return Value</span></span>  
 <span data-ttu-id="e1bf9-110">如果集合不是空的則為 `true`，否則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="e1bf9-110">`true` if the collection is not empty; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1bf9-111">備註</span><span class="sxs-lookup"><span data-stu-id="e1bf9-111">Remarks</span></span>  
 <span data-ttu-id="e1bf9-112">EXISTS 是其中一個 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子。</span><span class="sxs-lookup"><span data-stu-id="e1bf9-112">EXISTS is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="e1bf9-113">所有 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子都會從左到右評估。</span><span class="sxs-lookup"><span data-stu-id="e1bf9-113">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="e1bf9-114">如需[!INCLUDE[esql](../../../../../../includes/esql-md.md)]設定運算子的優先順序資訊, 請參閱[EXCEPT](except-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="e1bf9-114">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1bf9-115">範例</span><span class="sxs-lookup"><span data-stu-id="e1bf9-115">Example</span></span>  
 <span data-ttu-id="e1bf9-116">下列 Entity SQL 查詢會使用 EXISTS 運算子判斷集合是否為空的。</span><span class="sxs-lookup"><span data-stu-id="e1bf9-116">The following Entity SQL query uses the EXISTS operator to determine whether the collection is empty.</span></span> <span data-ttu-id="e1bf9-117">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="e1bf9-117">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="e1bf9-118">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="e1bf9-118">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="e1bf9-119">[遵循 how to:執行可傳回 StructuralType 結果](../how-to-execute-a-query-that-returns-structuraltype-results.md)的查詢。</span><span class="sxs-lookup"><span data-stu-id="e1bf9-119">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="e1bf9-120">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="e1bf9-120">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EXISTS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#exists)]  
  
## <a name="see-also"></a><span data-ttu-id="e1bf9-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1bf9-121">See also</span></span>

- [<span data-ttu-id="e1bf9-122">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="e1bf9-122">Entity SQL Reference</span></span>](entity-sql-reference.md)
