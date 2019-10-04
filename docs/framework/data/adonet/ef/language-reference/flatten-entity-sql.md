---
title: FLATTEN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 1a670c63-0a29-4738-80e6-101f66af05c3
ms.openlocfilehash: 84b846e3db86c664bc42363f3d983a1001f5c318
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833812"
---
# <a name="flatten-entity-sql"></a><span data-ttu-id="1e99a-102">FLATTEN (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="1e99a-102">FLATTEN (Entity SQL)</span></span>
<span data-ttu-id="1e99a-103">將集合轉換成扁平化集合。</span><span class="sxs-lookup"><span data-stu-id="1e99a-103">Converts a collection of collections into a flattened collection.</span></span> <span data-ttu-id="1e99a-104">新集合所包含的所有元素與舊集合相同，但是不包含巢狀結構。</span><span class="sxs-lookup"><span data-stu-id="1e99a-104">The new collection contains all the same elements as the old collection, but without a nested structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e99a-105">語法</span><span class="sxs-lookup"><span data-stu-id="1e99a-105">Syntax</span></span>  
  
```sql  
FLATTEN ( collection )  
```  
  
## <a name="arguments"></a><span data-ttu-id="1e99a-106">引數</span><span class="sxs-lookup"><span data-stu-id="1e99a-106">Arguments</span></span>  
 `collection`  
 <span data-ttu-id="1e99a-107">任何傳回值集合的集合以便扁平化成為單一集合的有效運算式。</span><span class="sxs-lookup"><span data-stu-id="1e99a-107">Any valid expression that returns a collection of value collections to flatten into a single collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e99a-108">備註</span><span class="sxs-lookup"><span data-stu-id="1e99a-108">Remarks</span></span>  
 <span data-ttu-id="1e99a-109">`FLATTEN` 是其中一個 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子。</span><span class="sxs-lookup"><span data-stu-id="1e99a-109">`FLATTEN` is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="1e99a-110">所有 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子都會從左到右評估。</span><span class="sxs-lookup"><span data-stu-id="1e99a-110">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="1e99a-111">如需 @no__t 1 設定運算子的優先順序資訊，請參閱[除外](except-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="1e99a-111">See [EXCEPT](except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e99a-112">範例</span><span class="sxs-lookup"><span data-stu-id="1e99a-112">Example</span></span>  
 <span data-ttu-id="1e99a-113">下列 Entity SQL 查詢會使用 `FLATTEN` 運算子，將集合轉換成扁平化集合。</span><span class="sxs-lookup"><span data-stu-id="1e99a-113">The following Entity SQL query uses the `FLATTEN` operator to convert a collection of collections into a flattened collection.</span></span> <span data-ttu-id="1e99a-114">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="1e99a-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="1e99a-115">依照 [How 中的程式進行：執行可傳回 StructuralType 結果 @ no__t-0 的查詢。</span><span class="sxs-lookup"><span data-stu-id="1e99a-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="1e99a-116">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="1e99a-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#FLATTEN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#flatten)]  
  
## <a name="see-also"></a><span data-ttu-id="1e99a-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e99a-117">See also</span></span>

- [<span data-ttu-id="1e99a-118">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="1e99a-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
