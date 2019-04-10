---
title: '! (NOT) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: a1447a34-df06-4393-93c3-0612ebd41abc
ms.openlocfilehash: 51d3bdbc4adb0b5fd6275629219698dd9b42fa86
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59306764"
---
# <a name="-not-entity-sql"></a><span data-ttu-id="0b847-103">!</span><span class="sxs-lookup"><span data-stu-id="0b847-103">!</span></span> <span data-ttu-id="0b847-104">(NOT) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="0b847-104">(NOT) (Entity SQL)</span></span>
<span data-ttu-id="0b847-105">執行 `Boolean` 運算式的否定運算。</span><span class="sxs-lookup"><span data-stu-id="0b847-105">Negates a `Boolean` expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b847-106">語法</span><span class="sxs-lookup"><span data-stu-id="0b847-106">Syntax</span></span>  
  
```  
NOT boolean_expression  
or  
! boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="0b847-107">引數</span><span class="sxs-lookup"><span data-stu-id="0b847-107">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="0b847-108">傳回布林值的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="0b847-108">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b847-109">備註</span><span class="sxs-lookup"><span data-stu-id="0b847-109">Remarks</span></span>  
 <span data-ttu-id="0b847-110">驚嘆號 (!) 的功能與 NOT 運算子相同。</span><span class="sxs-lookup"><span data-stu-id="0b847-110">The exclamation point (!) has the same functionality as the NOT operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b847-111">範例</span><span class="sxs-lookup"><span data-stu-id="0b847-111">Example</span></span>  
 <span data-ttu-id="0b847-112">下列 Entity SQL 查詢會使用 NOT 運算子執行 `Boolean` 運算式的否定運算。</span><span class="sxs-lookup"><span data-stu-id="0b847-112">The following Entity SQL query uses the NOT operator to negates a `Boolean` expression.</span></span> <span data-ttu-id="0b847-113">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="0b847-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="0b847-114">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="0b847-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="0b847-115">請依照下列中的程序[How to:執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)。</span><span class="sxs-lookup"><span data-stu-id="0b847-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="0b847-116">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="0b847-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NOT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#not)]  
  
## <a name="see-also"></a><span data-ttu-id="0b847-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b847-117">See also</span></span>

- [<span data-ttu-id="0b847-118">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="0b847-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
