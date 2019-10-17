---
title: INTERSECT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 93c6fe33-f341-4b52-911e-adf503891951
ms.openlocfilehash: dc7338d176302b8683d541ab0dc715dd8d149c6f
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319773"
---
# <a name="intersect-entity-sql"></a><span data-ttu-id="c7237-102">INTERSECT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="c7237-102">INTERSECT (Entity SQL)</span></span>
<span data-ttu-id="c7237-103">傳回 INTERSECT 運算元左右兩側之查詢運算式都會傳回的任何相異值集合。</span><span class="sxs-lookup"><span data-stu-id="c7237-103">Returns a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="c7237-104">所有運算式都必須具有與 `expression`相同的型別或是共同基底型別或衍生型別。</span><span class="sxs-lookup"><span data-stu-id="c7237-104">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7237-105">語法</span><span class="sxs-lookup"><span data-stu-id="c7237-105">Syntax</span></span>  
  
```sql  
expression INTERSECT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="c7237-106">引數</span><span class="sxs-lookup"><span data-stu-id="c7237-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="c7237-107">任何有效的查詢運算式，該運算式會傳回要與另一個查詢運算式傳回之集合相比較的集合。</span><span class="sxs-lookup"><span data-stu-id="c7237-107">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c7237-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="c7237-108">Return Value</span></span>  
 <span data-ttu-id="c7237-109">具有與 `expression`相同的型別或是共同基底類型或衍生型別的集合。</span><span class="sxs-lookup"><span data-stu-id="c7237-109">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7237-110">備註</span><span class="sxs-lookup"><span data-stu-id="c7237-110">Remarks</span></span>  
 <span data-ttu-id="c7237-111">INTERSECT 是其中一個 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子。</span><span class="sxs-lookup"><span data-stu-id="c7237-111">INTERSECT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="c7237-112">所有 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子都會從左到右評估。</span><span class="sxs-lookup"><span data-stu-id="c7237-112">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="c7237-113">如需 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子的優先順序資訊，請參閱[EXCEPT](except-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="c7237-113">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7237-114">範例</span><span class="sxs-lookup"><span data-stu-id="c7237-114">Example</span></span>  
 <span data-ttu-id="c7237-115">下列 Entity SQL 查詢會使用 INTERSECT 運算元，傳回 INTERSECT 運算元左右兩側之查詢運算式都傳回的任何相異值集合。</span><span class="sxs-lookup"><span data-stu-id="c7237-115">The following Entity SQL query uses the INTERSECT operator to return a collection of any distinct values that are returned by both the query expressions on the left and right sides of the INTERSECT operand.</span></span> <span data-ttu-id="c7237-116">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="c7237-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="c7237-117">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="c7237-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="c7237-118">遵循 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。</span><span class="sxs-lookup"><span data-stu-id="c7237-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="c7237-119">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="c7237-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#INTERSECT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#intersect)]  
  
## <a name="see-also"></a><span data-ttu-id="c7237-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="c7237-120">See also</span></span>

- [<span data-ttu-id="c7237-121">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="c7237-121">Entity SQL Reference</span></span>](entity-sql-reference.md)
