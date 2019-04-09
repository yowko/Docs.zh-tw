---
title: '&amp;&amp; （和）(Entity SQL)'
ms.date: 03/30/2017
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
ms.openlocfilehash: f0b20a8c1960bd6191a35c426dbea45c30ccc1c0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59084060"
---
# <a name="ampamp-and-entity-sql"></a><span data-ttu-id="4098f-102">&amp;&amp; （和）(Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="4098f-102">&amp;&amp; (AND) (Entity SQL)</span></span>
<span data-ttu-id="4098f-103">如果兩個運算式都是 `true` 則傳回 `true`，否則為 `false` 或 `NULL`。</span><span class="sxs-lookup"><span data-stu-id="4098f-103">Returns `true` if both expressions are `true`; otherwise, `false` or `NULL`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4098f-104">語法</span><span class="sxs-lookup"><span data-stu-id="4098f-104">Syntax</span></span>  
  
```  
boolean_expression AND boolean_expression  
or  
boolean_expression && boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="4098f-105">引數</span><span class="sxs-lookup"><span data-stu-id="4098f-105">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="4098f-106">傳回布林值的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="4098f-106">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4098f-107">備註</span><span class="sxs-lookup"><span data-stu-id="4098f-107">Remarks</span></span>  
 <span data-ttu-id="4098f-108">雙連字號 (&&) 的功能與 AND 運算子相同。</span><span class="sxs-lookup"><span data-stu-id="4098f-108">Double ampersands (&&) have the same functionality as the AND operator.</span></span>  
  
 <span data-ttu-id="4098f-109">下表顯示可能的輸入值和傳回型別。</span><span class="sxs-lookup"><span data-stu-id="4098f-109">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="4098f-110">true</span><span class="sxs-lookup"><span data-stu-id="4098f-110">TRUE</span></span>|<span data-ttu-id="4098f-111">false</span><span class="sxs-lookup"><span data-stu-id="4098f-111">FALSE</span></span>|<span data-ttu-id="4098f-112">NULL</span><span class="sxs-lookup"><span data-stu-id="4098f-112">NULL</span></span>|  
|`FALSE`|<span data-ttu-id="4098f-113">false</span><span class="sxs-lookup"><span data-stu-id="4098f-113">FALSE</span></span>|<span data-ttu-id="4098f-114">false</span><span class="sxs-lookup"><span data-stu-id="4098f-114">FALSE</span></span>|<span data-ttu-id="4098f-115">false</span><span class="sxs-lookup"><span data-stu-id="4098f-115">FALSE</span></span>|  
|`NULL`|<span data-ttu-id="4098f-116">NULL</span><span class="sxs-lookup"><span data-stu-id="4098f-116">NULL</span></span>|<span data-ttu-id="4098f-117">false</span><span class="sxs-lookup"><span data-stu-id="4098f-117">FALSE</span></span>|<span data-ttu-id="4098f-118">NULL</span><span class="sxs-lookup"><span data-stu-id="4098f-118">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4098f-119">範例</span><span class="sxs-lookup"><span data-stu-id="4098f-119">Example</span></span>  
 <span data-ttu-id="4098f-120">下列 Entity SQL 查詢會示範如何使用 AND 運算子。</span><span class="sxs-lookup"><span data-stu-id="4098f-120">The following Entity SQL query demonstrates how to use the AND operator.</span></span> <span data-ttu-id="4098f-121">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="4098f-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="4098f-122">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="4098f-122">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="4098f-123">請依照下列中的程序[How to:執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)。</span><span class="sxs-lookup"><span data-stu-id="4098f-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="4098f-124">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="4098f-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## <a name="see-also"></a><span data-ttu-id="4098f-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4098f-125">See also</span></span>

- [<span data-ttu-id="4098f-126">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="4098f-126">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
