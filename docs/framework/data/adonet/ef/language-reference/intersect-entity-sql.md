---
title: INTERSECT (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 93c6fe33-f341-4b52-911e-adf503891951
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 949cca70c63da1204db783b883a29b1a41247630
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="intersect-entity-sql"></a><span data-ttu-id="6b9a5-102">INTERSECT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="6b9a5-102">INTERSECT (Entity SQL)</span></span>
<span data-ttu-id="6b9a5-103">傳回 INTERSECT 運算元左右兩側之查詢運算式都會傳回的任何相異值集合。</span><span class="sxs-lookup"><span data-stu-id="6b9a5-103">Returns a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="6b9a5-104">所有運算式都必須具有與 `expression`相同的型別或是共同基底型別或衍生型別。</span><span class="sxs-lookup"><span data-stu-id="6b9a5-104">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b9a5-105">語法</span><span class="sxs-lookup"><span data-stu-id="6b9a5-105">Syntax</span></span>  
  
```  
expression INTERSECT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="6b9a5-106">引數</span><span class="sxs-lookup"><span data-stu-id="6b9a5-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="6b9a5-107">任何有效的查詢運算式，該運算式會傳回要與另一個查詢運算式傳回之集合相比較的集合。</span><span class="sxs-lookup"><span data-stu-id="6b9a5-107">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6b9a5-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="6b9a5-108">Return Value</span></span>  
 <span data-ttu-id="6b9a5-109">具有與 `expression`相同的型別或是共同基底類型或衍生型別的集合。</span><span class="sxs-lookup"><span data-stu-id="6b9a5-109">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b9a5-110">備註</span><span class="sxs-lookup"><span data-stu-id="6b9a5-110">Remarks</span></span>  
 <span data-ttu-id="6b9a5-111">INTERSECT 是其中一個 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子。</span><span class="sxs-lookup"><span data-stu-id="6b9a5-111">INTERSECT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="6b9a5-112">所有 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子都會從左到右評估。</span><span class="sxs-lookup"><span data-stu-id="6b9a5-112">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="6b9a5-113">優先順序資訊[!INCLUDE[esql](../../../../../../includes/esql-md.md)]設定運算子，請參閱[EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="6b9a5-113">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b9a5-114">範例</span><span class="sxs-lookup"><span data-stu-id="6b9a5-114">Example</span></span>  
 <span data-ttu-id="6b9a5-115">下列 Entity SQL 查詢會使用 INTERSECT 運算元，傳回 INTERSECT 運算元左右兩側之查詢運算式都傳回的任何相異值集合。</span><span class="sxs-lookup"><span data-stu-id="6b9a5-115">The following Entity SQL query uses the INTERSECT operator to return a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="6b9a5-116">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="6b9a5-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="6b9a5-117">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="6b9a5-117">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="6b9a5-118">遵循 [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。</span><span class="sxs-lookup"><span data-stu-id="6b9a5-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="6b9a5-119">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="6b9a5-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#INTERSECT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#intersect)]  
  
## <a name="see-also"></a><span data-ttu-id="6b9a5-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="6b9a5-120">See Also</span></span>  
 [<span data-ttu-id="6b9a5-121">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="6b9a5-121">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
