---
title: '&amp;&amp;和（Entity SQL）'
ms.date: 03/30/2017
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
ms.openlocfilehash: 02e404b73e5a9a9c3963e2d2b58ab7592afabc13
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251320"
---
# <a name="ampamp-and-entity-sql"></a><span data-ttu-id="9d377-102">&amp;&amp;和（Entity SQL）</span><span class="sxs-lookup"><span data-stu-id="9d377-102">&amp;&amp; (AND) (Entity SQL)</span></span>
<span data-ttu-id="9d377-103">如果兩個運算式都是 `true` 則傳回 `true`，否則為 `false` 或 `NULL`。</span><span class="sxs-lookup"><span data-stu-id="9d377-103">Returns `true` if both expressions are `true`; otherwise, `false` or `NULL`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d377-104">語法</span><span class="sxs-lookup"><span data-stu-id="9d377-104">Syntax</span></span>  
  
```  
boolean_expression AND boolean_expression  
or  
boolean_expression && boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="9d377-105">引數</span><span class="sxs-lookup"><span data-stu-id="9d377-105">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="9d377-106">傳回布林值的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="9d377-106">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d377-107">備註</span><span class="sxs-lookup"><span data-stu-id="9d377-107">Remarks</span></span>  
 <span data-ttu-id="9d377-108">雙連字號 (&&) 的功能與 AND 運算子相同。</span><span class="sxs-lookup"><span data-stu-id="9d377-108">Double ampersands (&&) have the same functionality as the AND operator.</span></span>  
  
 <span data-ttu-id="9d377-109">下表顯示可能的輸入值和傳回型別。</span><span class="sxs-lookup"><span data-stu-id="9d377-109">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="9d377-110">true</span><span class="sxs-lookup"><span data-stu-id="9d377-110">TRUE</span></span>|<span data-ttu-id="9d377-111">false</span><span class="sxs-lookup"><span data-stu-id="9d377-111">FALSE</span></span>|<span data-ttu-id="9d377-112">NULL</span><span class="sxs-lookup"><span data-stu-id="9d377-112">NULL</span></span>|  
|`FALSE`|<span data-ttu-id="9d377-113">false</span><span class="sxs-lookup"><span data-stu-id="9d377-113">FALSE</span></span>|<span data-ttu-id="9d377-114">false</span><span class="sxs-lookup"><span data-stu-id="9d377-114">FALSE</span></span>|<span data-ttu-id="9d377-115">false</span><span class="sxs-lookup"><span data-stu-id="9d377-115">FALSE</span></span>|  
|`NULL`|<span data-ttu-id="9d377-116">NULL</span><span class="sxs-lookup"><span data-stu-id="9d377-116">NULL</span></span>|<span data-ttu-id="9d377-117">false</span><span class="sxs-lookup"><span data-stu-id="9d377-117">FALSE</span></span>|<span data-ttu-id="9d377-118">NULL</span><span class="sxs-lookup"><span data-stu-id="9d377-118">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9d377-119">範例</span><span class="sxs-lookup"><span data-stu-id="9d377-119">Example</span></span>  
 <span data-ttu-id="9d377-120">下列 Entity SQL 查詢會示範如何使用 AND 運算子。</span><span class="sxs-lookup"><span data-stu-id="9d377-120">The following Entity SQL query demonstrates how to use the AND operator.</span></span> <span data-ttu-id="9d377-121">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="9d377-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="9d377-122">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="9d377-122">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="9d377-123">[遵循 how to：執行可傳回 StructuralType 結果](../how-to-execute-a-query-that-returns-structuraltype-results.md)的查詢。</span><span class="sxs-lookup"><span data-stu-id="9d377-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="9d377-124">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="9d377-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## <a name="see-also"></a><span data-ttu-id="9d377-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d377-125">See also</span></span>

- [<span data-ttu-id="9d377-126">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="9d377-126">Entity SQL Reference</span></span>](entity-sql-reference.md)
