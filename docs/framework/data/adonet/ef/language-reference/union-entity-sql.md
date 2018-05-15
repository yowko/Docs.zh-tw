---
title: UNION (Entity SQL)
ms.date: 03/30/2017
ms.assetid: df98a4db-b00d-4c8b-bd74-0d285f27e1df
ms.openlocfilehash: 52a7a332166250e8fa8084986fd0d89da6fdf42d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="union-entity-sql"></a><span data-ttu-id="37b60-102">UNION (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="37b60-102">UNION (Entity SQL)</span></span>
<span data-ttu-id="37b60-103">將二個或多個查詢的結果結合成單一集合。</span><span class="sxs-lookup"><span data-stu-id="37b60-103">Combines the results of two or more queries into a single collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37b60-104">語法</span><span class="sxs-lookup"><span data-stu-id="37b60-104">Syntax</span></span>  
  
```  
expression  
UNION [ ALL ]  
expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="37b60-105">引數</span><span class="sxs-lookup"><span data-stu-id="37b60-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="37b60-106">任何有效的查詢運算式，該運算式會傳回與此集合結合的集合。所有運算式都必須具有與 `expression`相同的型別或是共同基底類型或衍生型別。</span><span class="sxs-lookup"><span data-stu-id="37b60-106">Any valid query expression that returns a collection to combine with the collection All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
 <span data-ttu-id="37b60-107">UNION</span><span class="sxs-lookup"><span data-stu-id="37b60-107">UNION</span></span>  
 <span data-ttu-id="37b60-108">指定要結合多個集合，並當做單一集合傳回。</span><span class="sxs-lookup"><span data-stu-id="37b60-108">Specifies that multiple collections are to be combined and returned as a single collection.</span></span>  
  
 <span data-ttu-id="37b60-109">ALL</span><span class="sxs-lookup"><span data-stu-id="37b60-109">ALL</span></span>  
 <span data-ttu-id="37b60-110">指定要結合多個集合，並當做單一集合傳回，包括重複的項目。</span><span class="sxs-lookup"><span data-stu-id="37b60-110">Specifies that multiple collections are to be combined and returned as a single collection, including duplicates.</span></span> <span data-ttu-id="37b60-111">若未指定，就會從結果集合中移除重複的項目。</span><span class="sxs-lookup"><span data-stu-id="37b60-111">If not specified, duplicates are removed from the result collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="37b60-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="37b60-112">Return Value</span></span>  
 <span data-ttu-id="37b60-113">具有與 `expression`相同的型別或是共同基底類型或衍生型別的集合。</span><span class="sxs-lookup"><span data-stu-id="37b60-113">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37b60-114">備註</span><span class="sxs-lookup"><span data-stu-id="37b60-114">Remarks</span></span>  
 <span data-ttu-id="37b60-115">UNION 是其中一個 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子。</span><span class="sxs-lookup"><span data-stu-id="37b60-115">UNION is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="37b60-116">所有 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子都會從左到右評估。</span><span class="sxs-lookup"><span data-stu-id="37b60-116">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="37b60-117">優先順序資訊[!INCLUDE[esql](../../../../../../includes/esql-md.md)]設定運算子，請參閱[EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="37b60-117">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="37b60-118">範例</span><span class="sxs-lookup"><span data-stu-id="37b60-118">Example</span></span>  
 <span data-ttu-id="37b60-119">下列 Entity SQL 查詢會使用 UNION ALL 運算子，將兩個查詢的結果結合成單一集合。</span><span class="sxs-lookup"><span data-stu-id="37b60-119">The following Entity SQL query uses the UNION ALL operator to combine the results of two queries into a single collection.</span></span> <span data-ttu-id="37b60-120">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="37b60-120">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="37b60-121">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="37b60-121">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="37b60-122">遵循 [如何：執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。</span><span class="sxs-lookup"><span data-stu-id="37b60-122">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="37b60-123">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="37b60-123">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#UNION](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#union)]  
  
## <a name="see-also"></a><span data-ttu-id="37b60-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37b60-124">See Also</span></span>  
 [<span data-ttu-id="37b60-125">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="37b60-125">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
