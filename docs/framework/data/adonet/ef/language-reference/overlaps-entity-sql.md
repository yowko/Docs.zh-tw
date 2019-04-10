---
title: OVERLAPS (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 41743e89-79cb-4d7b-8a27-355b45024b61
ms.openlocfilehash: 9d909fb7efbb29619351cfc866b0f84381d0b80b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59319634"
---
# <a name="overlaps-entity-sql"></a><span data-ttu-id="d0b6b-102">OVERLAPS (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d0b6b-102">OVERLAPS (Entity SQL)</span></span>
<span data-ttu-id="d0b6b-103">判斷兩個集合是否有共同項目。</span><span class="sxs-lookup"><span data-stu-id="d0b6b-103">Determines whether two collections have common elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0b6b-104">語法</span><span class="sxs-lookup"><span data-stu-id="d0b6b-104">Syntax</span></span>  
  
```  
expression OVERLAPS expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="d0b6b-105">引數</span><span class="sxs-lookup"><span data-stu-id="d0b6b-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="d0b6b-106">任何有效的查詢運算式，該運算式會傳回要與另一個查詢運算式傳回之集合相比較的集合。</span><span class="sxs-lookup"><span data-stu-id="d0b6b-106">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span> <span data-ttu-id="d0b6b-107">所有運算式都必須具有與 `expression`相同的型別或是共同基底型別或衍生型別。</span><span class="sxs-lookup"><span data-stu-id="d0b6b-107">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d0b6b-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="d0b6b-108">Return Value</span></span>  
 `true` <span data-ttu-id="d0b6b-109">如果兩個集合有共同的項目;否則， `false`。</span><span class="sxs-lookup"><span data-stu-id="d0b6b-109">if the two collections have common elements; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0b6b-110">備註</span><span class="sxs-lookup"><span data-stu-id="d0b6b-110">Remarks</span></span>  
 <span data-ttu-id="d0b6b-111">OVERLAPS 提供的功能就相當於下列：</span><span class="sxs-lookup"><span data-stu-id="d0b6b-111">OVERLAPS provides functionally equivalent to the following:</span></span>  
  
 `EXISTS ( expression INTERSECT expression )`  
  
 <span data-ttu-id="d0b6b-112">OVERLAPS 是其中一個 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子。</span><span class="sxs-lookup"><span data-stu-id="d0b6b-112">OVERLAPS is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="d0b6b-113">所有 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子都會從左到右評估。</span><span class="sxs-lookup"><span data-stu-id="d0b6b-113">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="d0b6b-114">優先順序資訊[!INCLUDE[esql](../../../../../../includes/esql-md.md)]設定運算子，請參閱 < [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="d0b6b-114">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0b6b-115">範例</span><span class="sxs-lookup"><span data-stu-id="d0b6b-115">Example</span></span>  
 <span data-ttu-id="d0b6b-116">下列 Entity SQL 查詢會使用 OVERLAPS 運算子來判斷兩個集合是否具有共通的值。</span><span class="sxs-lookup"><span data-stu-id="d0b6b-116">The following Entity SQL query uses the OVERLAPS operator to determines whether two collections have a common value.</span></span> <span data-ttu-id="d0b6b-117">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="d0b6b-117">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="d0b6b-118">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="d0b6b-118">To compile and run this, follow these steps:</span></span>  
  
1. <span data-ttu-id="d0b6b-119">請依照下列中的程序[How to:執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)。</span><span class="sxs-lookup"><span data-stu-id="d0b6b-119">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="d0b6b-120">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="d0b6b-120">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#OVERLAPS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#overlaps)]  
  
## <a name="see-also"></a><span data-ttu-id="d0b6b-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0b6b-121">See also</span></span>

- [<span data-ttu-id="d0b6b-122">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="d0b6b-122">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
