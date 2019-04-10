---
title: '- （減）(Entity SQL)'
ms.date: 03/30/2017
ms.assetid: bc4327f9-09c0-438f-a008-927c5c478040
ms.openlocfilehash: 2e4c08788ea57000e189c8371f0494641931184b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59316683"
---
# <a name="--subtract-entity-sql"></a><span data-ttu-id="813fb-102">- (減號) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="813fb-102">- (Subtract) (Entity SQL)</span></span>
<span data-ttu-id="813fb-103">兩個數字相減。</span><span class="sxs-lookup"><span data-stu-id="813fb-103">Subtracts two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="813fb-104">語法</span><span class="sxs-lookup"><span data-stu-id="813fb-104">Syntax</span></span>  
  
```  
expression - expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="813fb-105">引數</span><span class="sxs-lookup"><span data-stu-id="813fb-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="813fb-106">任何一個數值資料型別的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="813fb-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="813fb-107">結果型別</span><span class="sxs-lookup"><span data-stu-id="813fb-107">Result Types</span></span>  
 <span data-ttu-id="813fb-108">從兩個引數的隱含型別提升產生的資料型別。</span><span class="sxs-lookup"><span data-stu-id="813fb-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="813fb-109">如需有關隱含型別提升的詳細資訊，請參閱[型別系統](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="813fb-109">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="813fb-110">範例</span><span class="sxs-lookup"><span data-stu-id="813fb-110">Example</span></span>  
 <span data-ttu-id="813fb-111">下列 Entity SQL 查詢會使用 - 算術運算子讓兩個數字相減。</span><span class="sxs-lookup"><span data-stu-id="813fb-111">The following Entity SQL query uses the - arithmetic operator to subtract two numbers.</span></span> <span data-ttu-id="813fb-112">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="813fb-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="813fb-113">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="813fb-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="813fb-114">請依照下列中的程序[How to:執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)。</span><span class="sxs-lookup"><span data-stu-id="813fb-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="813fb-115">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="813fb-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#SUBTRACT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#subtract)]  
  
## <a name="see-also"></a><span data-ttu-id="813fb-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="813fb-116">See also</span></span>

- [<span data-ttu-id="813fb-117">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="813fb-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
