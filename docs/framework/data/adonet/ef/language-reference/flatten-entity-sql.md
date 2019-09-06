---
title: FLATTEN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 1a670c63-0a29-4738-80e6-101f66af05c3
ms.openlocfilehash: 327a20bbc53566846e7d828f511bcd1d25cc5504
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250960"
---
# <a name="flatten-entity-sql"></a><span data-ttu-id="0018c-102">FLATTEN (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="0018c-102">FLATTEN (Entity SQL)</span></span>
<span data-ttu-id="0018c-103">將集合轉換成扁平化集合。</span><span class="sxs-lookup"><span data-stu-id="0018c-103">Converts a collection of collections into a flattened collection.</span></span> <span data-ttu-id="0018c-104">新集合所包含的所有元素與舊集合相同，但是不包含巢狀結構。</span><span class="sxs-lookup"><span data-stu-id="0018c-104">The new collection contains all the same elements as the old collection, but without a nested structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0018c-105">語法</span><span class="sxs-lookup"><span data-stu-id="0018c-105">Syntax</span></span>  
  
```  
FLATTEN ( collection )  
```  
  
## <a name="arguments"></a><span data-ttu-id="0018c-106">引數</span><span class="sxs-lookup"><span data-stu-id="0018c-106">Arguments</span></span>  
 `collection`  
 <span data-ttu-id="0018c-107">任何傳回值集合的集合以便扁平化成為單一集合的有效運算式。</span><span class="sxs-lookup"><span data-stu-id="0018c-107">Any valid expression that returns a collection of value collections to flatten into a single collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0018c-108">備註</span><span class="sxs-lookup"><span data-stu-id="0018c-108">Remarks</span></span>  
 <span data-ttu-id="0018c-109">`FLATTEN` 是其中一個 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子。</span><span class="sxs-lookup"><span data-stu-id="0018c-109">`FLATTEN` is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="0018c-110">所有 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子都會從左到右評估。</span><span class="sxs-lookup"><span data-stu-id="0018c-110">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="0018c-111">如[需](except-entity-sql.md) [!INCLUDE[esql](../../../../../../includes/esql-md.md)]設定運算子的優先順序資訊，請參閱。</span><span class="sxs-lookup"><span data-stu-id="0018c-111">See [EXCEPT](except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0018c-112">範例</span><span class="sxs-lookup"><span data-stu-id="0018c-112">Example</span></span>  
 <span data-ttu-id="0018c-113">下列 Entity SQL 查詢會使用 `FLATTEN` 運算子，將集合轉換成扁平化集合。</span><span class="sxs-lookup"><span data-stu-id="0018c-113">The following Entity SQL query uses the `FLATTEN` operator to convert a collection of collections into a flattened collection.</span></span> <span data-ttu-id="0018c-114">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="0018c-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="0018c-115">[遵循 how to：執行可傳回 StructuralType 結果](../how-to-execute-a-query-that-returns-structuraltype-results.md)的查詢。</span><span class="sxs-lookup"><span data-stu-id="0018c-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="0018c-116">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="0018c-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#FLATTEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#flatten)]  
  
## <a name="see-also"></a><span data-ttu-id="0018c-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0018c-117">See also</span></span>

- [<span data-ttu-id="0018c-118">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="0018c-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
