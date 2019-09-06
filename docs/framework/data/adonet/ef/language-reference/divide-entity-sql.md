---
title: '- 拆分（Entity SQL）'
ms.date: 03/30/2017
ms.assetid: ef48c368-f3ed-4275-8ada-4e9649781262
ms.openlocfilehash: d4e4c1449b665e6dea22bfcc0ee2277478b4da1a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251060"
---
# <a name="-divide-entity-sql"></a><span data-ttu-id="9d0bd-102">/ (除號) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="9d0bd-102">/ (Divide) (Entity SQL)</span></span>
<span data-ttu-id="9d0bd-103">將一個數字除以另一個數字。</span><span class="sxs-lookup"><span data-stu-id="9d0bd-103">Divides one number by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d0bd-104">語法</span><span class="sxs-lookup"><span data-stu-id="9d0bd-104">Syntax</span></span>  
  
```  
dividend / divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="9d0bd-105">引數</span><span class="sxs-lookup"><span data-stu-id="9d0bd-105">Arguments</span></span>  
 `dividend`  
 <span data-ttu-id="9d0bd-106">要當做被除數的數值運算式。</span><span class="sxs-lookup"><span data-stu-id="9d0bd-106">The numeric expression to divide.</span></span> <span data-ttu-id="9d0bd-107">`dividend` 是任何一個數值資料型別的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="9d0bd-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="9d0bd-108">要當做除數的數值運算式。</span><span class="sxs-lookup"><span data-stu-id="9d0bd-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="9d0bd-109">`divisor` 是任何一個數值資料型別的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="9d0bd-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="9d0bd-110">結果型別</span><span class="sxs-lookup"><span data-stu-id="9d0bd-110">Result Types</span></span>  
 <span data-ttu-id="9d0bd-111">從兩個引數的隱含型別提升產生的資料型別。</span><span class="sxs-lookup"><span data-stu-id="9d0bd-111">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="9d0bd-112">如需隱含類型升級的詳細資訊，請參閱[類型系統](type-system-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="9d0bd-112">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d0bd-113">範例</span><span class="sxs-lookup"><span data-stu-id="9d0bd-113">Example</span></span>  
 <span data-ttu-id="9d0bd-114">下列 Entity SQL 查詢會使用/算術運算子，將一個數位除以另一個數位。</span><span class="sxs-lookup"><span data-stu-id="9d0bd-114">The following Entity SQL query uses the / arithmetic operator to divide one number by another.</span></span> <span data-ttu-id="9d0bd-115">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="9d0bd-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="9d0bd-116">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="9d0bd-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="9d0bd-117">[遵循 how to：執行可傳回 StructuralType 結果](../how-to-execute-a-query-that-returns-structuraltype-results.md)的查詢。</span><span class="sxs-lookup"><span data-stu-id="9d0bd-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="9d0bd-118">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="9d0bd-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#DIVIDE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#divide)]  
  
## <a name="see-also"></a><span data-ttu-id="9d0bd-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d0bd-119">See also</span></span>

- [<span data-ttu-id="9d0bd-120">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="9d0bd-120">Entity SQL Reference</span></span>](entity-sql-reference.md)
