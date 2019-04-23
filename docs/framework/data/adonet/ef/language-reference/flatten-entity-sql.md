---
title: FLATTEN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 1a670c63-0a29-4738-80e6-101f66af05c3
ms.openlocfilehash: 4f9a6315fc9cc2f295c21cc5fb7e1007e47796b9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59304568"
---
# <a name="flatten-entity-sql"></a><span data-ttu-id="b907b-102">FLATTEN (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="b907b-102">FLATTEN (Entity SQL)</span></span>
<span data-ttu-id="b907b-103">將集合轉換成扁平化集合。</span><span class="sxs-lookup"><span data-stu-id="b907b-103">Converts a collection of collections into a flattened collection.</span></span> <span data-ttu-id="b907b-104">新集合所包含的所有元素與舊集合相同，但是不包含巢狀結構。</span><span class="sxs-lookup"><span data-stu-id="b907b-104">The new collection contains all the same elements as the old collection, but without a nested structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b907b-105">語法</span><span class="sxs-lookup"><span data-stu-id="b907b-105">Syntax</span></span>  
  
```  
FLATTEN ( collection )  
```  
  
## <a name="arguments"></a><span data-ttu-id="b907b-106">引數</span><span class="sxs-lookup"><span data-stu-id="b907b-106">Arguments</span></span>  
 `collection`  
 <span data-ttu-id="b907b-107">任何傳回值集合的集合以便扁平化成為單一集合的有效運算式。</span><span class="sxs-lookup"><span data-stu-id="b907b-107">Any valid expression that returns a collection of value collections to flatten into a single collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b907b-108">備註</span><span class="sxs-lookup"><span data-stu-id="b907b-108">Remarks</span></span>  
 <span data-ttu-id="b907b-109">`FLATTEN` 是其中一個 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子。</span><span class="sxs-lookup"><span data-stu-id="b907b-109">`FLATTEN` is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="b907b-110">所有 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子都會從左到右評估。</span><span class="sxs-lookup"><span data-stu-id="b907b-110">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="b907b-111">請參閱[EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md)的優先順序資訊[!INCLUDE[esql](../../../../../../includes/esql-md.md)]設定運算子。</span><span class="sxs-lookup"><span data-stu-id="b907b-111">See [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b907b-112">範例</span><span class="sxs-lookup"><span data-stu-id="b907b-112">Example</span></span>  
 <span data-ttu-id="b907b-113">下列 Entity SQL 查詢會使用 `FLATTEN` 運算子，將集合轉換成扁平化集合。</span><span class="sxs-lookup"><span data-stu-id="b907b-113">The following Entity SQL query uses the `FLATTEN` operator to convert a collection of collections into a flattened collection.</span></span> <span data-ttu-id="b907b-114">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="b907b-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="b907b-115">請依照下列中的程序[How to:執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)。</span><span class="sxs-lookup"><span data-stu-id="b907b-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="b907b-116">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="b907b-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#FLATTEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#flatten)]  
  
## <a name="see-also"></a><span data-ttu-id="b907b-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b907b-117">See also</span></span>

- [<span data-ttu-id="b907b-118">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="b907b-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
