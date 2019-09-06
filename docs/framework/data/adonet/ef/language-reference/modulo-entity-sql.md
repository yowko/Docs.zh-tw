---
title: (模數) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
ms.openlocfilehash: a30306539d45c3718d2e948e9717997bbe2104fa
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250076"
---
# <a name="modulo-entity-sql"></a><span data-ttu-id="66ec5-102">(模數) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="66ec5-102">(Modulo) (Entity SQL)</span></span>
<span data-ttu-id="66ec5-103">傳回某個運算式除以另一個運算式的餘數。</span><span class="sxs-lookup"><span data-stu-id="66ec5-103">Returns the remainder of one expression divided by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66ec5-104">語法</span><span class="sxs-lookup"><span data-stu-id="66ec5-104">Syntax</span></span>  
  
```  
dividend % divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="66ec5-105">引數</span><span class="sxs-lookup"><span data-stu-id="66ec5-105">Arguments</span></span>  
 `dividend`  
 <span data-ttu-id="66ec5-106">要當做被除數的數值運算式。</span><span class="sxs-lookup"><span data-stu-id="66ec5-106">The numeric expression to divide.</span></span> <span data-ttu-id="66ec5-107">`dividend` 是任何一個數值資料型別的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="66ec5-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="66ec5-108">要當做除數的數值運算式。</span><span class="sxs-lookup"><span data-stu-id="66ec5-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="66ec5-109">`divisor` 是任何一個數值資料型別的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="66ec5-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="66ec5-110">結果型別</span><span class="sxs-lookup"><span data-stu-id="66ec5-110">Result Types</span></span>  
 <span data-ttu-id="66ec5-111">Edm.Int32</span><span class="sxs-lookup"><span data-stu-id="66ec5-111">Edm.Int32</span></span>  
  
## <a name="example"></a><span data-ttu-id="66ec5-112">範例</span><span class="sxs-lookup"><span data-stu-id="66ec5-112">Example</span></span>  
 <span data-ttu-id="66ec5-113">下列 Entity SQL 查詢會使用 % 算術運算子來傳回某個運算式除以另一個運算式的餘數。</span><span class="sxs-lookup"><span data-stu-id="66ec5-113">The following Entity SQL query uses the % arithmetic operator to return the remainder of one expression divided by another.</span></span> <span data-ttu-id="66ec5-114">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="66ec5-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="66ec5-115">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="66ec5-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="66ec5-116">[遵循 how to:執行可傳回 StructuralType 結果](../how-to-execute-a-query-that-returns-structuraltype-results.md)的查詢。</span><span class="sxs-lookup"><span data-stu-id="66ec5-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="66ec5-117">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="66ec5-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MODULO](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#modulo)]  
  
## <a name="see-also"></a><span data-ttu-id="66ec5-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66ec5-118">See also</span></span>

- [<span data-ttu-id="66ec5-119">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="66ec5-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
