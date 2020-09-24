---
title: '! (NOT) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: a1447a34-df06-4393-93c3-0612ebd41abc
ms.openlocfilehash: 0eb9be9ed4cbce45a51d15eea68e9fb1a26f0107
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191836"
---
# <a name="-not-entity-sql"></a><span data-ttu-id="cf2d5-103">!</span><span class="sxs-lookup"><span data-stu-id="cf2d5-103">!</span></span> <span data-ttu-id="cf2d5-104">(NOT) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="cf2d5-104">(NOT) (Entity SQL)</span></span>

<span data-ttu-id="cf2d5-105">執行 `Boolean` 運算式的否定運算。</span><span class="sxs-lookup"><span data-stu-id="cf2d5-105">Negates a `Boolean` expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf2d5-106">語法</span><span class="sxs-lookup"><span data-stu-id="cf2d5-106">Syntax</span></span>  
  
```sql  
NOT boolean_expression  
-- or  
! boolean_expression  
```
  
## <a name="arguments"></a><span data-ttu-id="cf2d5-107">引數</span><span class="sxs-lookup"><span data-stu-id="cf2d5-107">Arguments</span></span>  

 `boolean_expression`  
 <span data-ttu-id="cf2d5-108">傳回布林值的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="cf2d5-108">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf2d5-109">備註</span><span class="sxs-lookup"><span data-stu-id="cf2d5-109">Remarks</span></span>  

 <span data-ttu-id="cf2d5-110">驚嘆號 (!) 的功能與 NOT 運算子相同。</span><span class="sxs-lookup"><span data-stu-id="cf2d5-110">The exclamation point (!) has the same functionality as the NOT operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf2d5-111">範例</span><span class="sxs-lookup"><span data-stu-id="cf2d5-111">Example</span></span>  

 <span data-ttu-id="cf2d5-112">下列 Entity SQL 查詢會使用 NOT 運算子執行 `Boolean` 運算式的否定運算。</span><span class="sxs-lookup"><span data-stu-id="cf2d5-112">The following Entity SQL query uses the NOT operator to negates a `Boolean` expression.</span></span> <span data-ttu-id="cf2d5-113">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="cf2d5-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="cf2d5-114">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="cf2d5-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="cf2d5-115">遵循 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。</span><span class="sxs-lookup"><span data-stu-id="cf2d5-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="cf2d5-116">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="cf2d5-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#NOT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#not)]  
  
## <a name="see-also"></a><span data-ttu-id="cf2d5-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf2d5-117">See also</span></span>

- [<span data-ttu-id="cf2d5-118">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="cf2d5-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
