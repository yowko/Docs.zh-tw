---
title: '! (NOT) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: a1447a34-df06-4393-93c3-0612ebd41abc
ms.openlocfilehash: 7755219c5238f78e59332c508643fe2ae1f5096f
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319524"
---
# <a name="-not-entity-sql"></a><span data-ttu-id="2387a-103">!</span><span class="sxs-lookup"><span data-stu-id="2387a-103">!</span></span> <span data-ttu-id="2387a-104">(NOT) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="2387a-104">(NOT) (Entity SQL)</span></span>
<span data-ttu-id="2387a-105">執行 `Boolean` 運算式的否定運算。</span><span class="sxs-lookup"><span data-stu-id="2387a-105">Negates a `Boolean` expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2387a-106">語法</span><span class="sxs-lookup"><span data-stu-id="2387a-106">Syntax</span></span>  
  
```sql  
NOT boolean_expression  
-- or  
! boolean_expression  
``` 
  
## <a name="arguments"></a><span data-ttu-id="2387a-107">引數</span><span class="sxs-lookup"><span data-stu-id="2387a-107">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="2387a-108">傳回布林值的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="2387a-108">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2387a-109">備註</span><span class="sxs-lookup"><span data-stu-id="2387a-109">Remarks</span></span>  
 <span data-ttu-id="2387a-110">驚嘆號 (!) 的功能與 NOT 運算子相同。</span><span class="sxs-lookup"><span data-stu-id="2387a-110">The exclamation point (!) has the same functionality as the NOT operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2387a-111">範例</span><span class="sxs-lookup"><span data-stu-id="2387a-111">Example</span></span>  
 <span data-ttu-id="2387a-112">下列 Entity SQL 查詢會使用 NOT 運算子執行 `Boolean` 運算式的否定運算。</span><span class="sxs-lookup"><span data-stu-id="2387a-112">The following Entity SQL query uses the NOT operator to negates a `Boolean` expression.</span></span> <span data-ttu-id="2387a-113">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="2387a-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="2387a-114">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="2387a-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="2387a-115">遵循 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。</span><span class="sxs-lookup"><span data-stu-id="2387a-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="2387a-116">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="2387a-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#NOT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#not)]  
  
## <a name="see-also"></a><span data-ttu-id="2387a-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="2387a-117">See also</span></span>

- [<span data-ttu-id="2387a-118">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="2387a-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
