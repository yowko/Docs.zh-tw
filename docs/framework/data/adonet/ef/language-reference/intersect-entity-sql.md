---
title: INTERSECT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 93c6fe33-f341-4b52-911e-adf503891951
ms.openlocfilehash: 217cd9b2a428c890d83d2b55d45321a04488398e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203640"
---
# <a name="intersect-entity-sql"></a><span data-ttu-id="6d368-102">INTERSECT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="6d368-102">INTERSECT (Entity SQL)</span></span>

<span data-ttu-id="6d368-103">傳回 INTERSECT 運算元左右兩側之查詢運算式都會傳回的任何相異值集合。</span><span class="sxs-lookup"><span data-stu-id="6d368-103">Returns a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="6d368-104">所有運算式都必須具有與 `expression`相同的型別或是共同基底型別或衍生型別。</span><span class="sxs-lookup"><span data-stu-id="6d368-104">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d368-105">語法</span><span class="sxs-lookup"><span data-stu-id="6d368-105">Syntax</span></span>  
  
```sql  
expression INTERSECT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="6d368-106">引數</span><span class="sxs-lookup"><span data-stu-id="6d368-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="6d368-107">任何有效的查詢運算式，該運算式會傳回要與另一個查詢運算式傳回之集合相比較的集合。</span><span class="sxs-lookup"><span data-stu-id="6d368-107">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6d368-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="6d368-108">Return Value</span></span>  

 <span data-ttu-id="6d368-109">具有與 `expression`相同的型別或是共同基底類型或衍生型別的集合。</span><span class="sxs-lookup"><span data-stu-id="6d368-109">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d368-110">備註</span><span class="sxs-lookup"><span data-stu-id="6d368-110">Remarks</span></span>  

 <span data-ttu-id="6d368-111">INTERSECT 是其中一個 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子。</span><span class="sxs-lookup"><span data-stu-id="6d368-111">INTERSECT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="6d368-112">所有 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子都會從左到右評估。</span><span class="sxs-lookup"><span data-stu-id="6d368-112">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="6d368-113">如需設定運算子的優先順序資訊 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ，請參閱 [EXCEPT](except-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="6d368-113">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d368-114">範例</span><span class="sxs-lookup"><span data-stu-id="6d368-114">Example</span></span>  

 <span data-ttu-id="6d368-115">下列 Entity SQL 查詢會使用 INTERSECT 運算元，傳回 INTERSECT 運算元左右兩側之查詢運算式都傳回的任何相異值集合。</span><span class="sxs-lookup"><span data-stu-id="6d368-115">The following Entity SQL query uses the INTERSECT operator to return a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="6d368-116">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="6d368-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="6d368-117">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="6d368-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="6d368-118">遵循 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。</span><span class="sxs-lookup"><span data-stu-id="6d368-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="6d368-119">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="6d368-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#INTERSECT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#intersect)]  
  
## <a name="see-also"></a><span data-ttu-id="6d368-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d368-120">See also</span></span>

- [<span data-ttu-id="6d368-121">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="6d368-121">Entity SQL Reference</span></span>](entity-sql-reference.md)
