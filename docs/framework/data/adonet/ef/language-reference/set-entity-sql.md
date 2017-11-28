---
title: SET (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 28b4deac-c7e4-4f09-b428-4d352ef2dc94
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e70db99157e0bc49e1548d18c8fccfa44af42356
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="set-entity-sql"></a><span data-ttu-id="1ae08-102">SET (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="1ae08-102">SET (Entity SQL)</span></span>
<span data-ttu-id="1ae08-103">SET 運算式會產生移除所有重複項目的新集合，利用這種方式將物件的集合轉換成集合。</span><span class="sxs-lookup"><span data-stu-id="1ae08-103">The SET expression is used to convert a collection of objects into a set by yielding a new collection with all duplicate elements removed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ae08-104">語法</span><span class="sxs-lookup"><span data-stu-id="1ae08-104">Syntax</span></span>  
  
```  
SET ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="1ae08-105">引數</span><span class="sxs-lookup"><span data-stu-id="1ae08-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="1ae08-106">傳回集合的任何有效查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="1ae08-106">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ae08-107">備註</span><span class="sxs-lookup"><span data-stu-id="1ae08-107">Remarks</span></span>  
 <span data-ttu-id="1ae08-108">SET 運算式 `SET(c)` 在邏輯上相當於下列 SELECT 陳述式 (Statement)：</span><span class="sxs-lookup"><span data-stu-id="1ae08-108">The set expression `SET(c)` is logically equivalent to the following select statement:</span></span>  
  
```  
SELECT VALUE DISTINCT c FROM c  
```  
  
 <span data-ttu-id="1ae08-109">`SET` 是其中一個 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子。</span><span class="sxs-lookup"><span data-stu-id="1ae08-109">`SET` is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="1ae08-110">所有 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子都會從左到右評估。</span><span class="sxs-lookup"><span data-stu-id="1ae08-110">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="1ae08-111">請參閱[EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md)的優先順序資訊[!INCLUDE[esql](../../../../../../includes/esql-md.md)]設定運算子。</span><span class="sxs-lookup"><span data-stu-id="1ae08-111">See [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md) for precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ae08-112">範例</span><span class="sxs-lookup"><span data-stu-id="1ae08-112">Example</span></span>  
 <span data-ttu-id="1ae08-113">下列 Entity SQL 查詢會使用 SET 運算式，將物件的集合 (Collection) 轉換成單一集合 (Set)。</span><span class="sxs-lookup"><span data-stu-id="1ae08-113">The following Entity SQL query uses the SET expression to convert a collection of objects into a set.</span></span> <span data-ttu-id="1ae08-114">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="1ae08-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="1ae08-115">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="1ae08-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="1ae08-116">請依照下列中的程序[如何： 執行查詢，傳回 PrimitiveType 結果](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)。</span><span class="sxs-lookup"><span data-stu-id="1ae08-116">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="1ae08-117">將下列查詢當成引數，傳遞至 `ExecutePrimitiveTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="1ae08-117">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#SET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#set)]  
  
## <a name="see-also"></a><span data-ttu-id="1ae08-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ae08-118">See Also</span></span>  
 [<span data-ttu-id="1ae08-119">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="1ae08-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
