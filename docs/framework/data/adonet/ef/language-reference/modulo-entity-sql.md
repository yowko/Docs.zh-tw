---
title: (模數) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
ms.openlocfilehash: 25bd34db3a627fa708e1ab9a3f0e237426487bcb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175703"
---
# <a name="modulo-entity-sql"></a><span data-ttu-id="0c7e0-102">(模數) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="0c7e0-102">(Modulo) (Entity SQL)</span></span>

<span data-ttu-id="0c7e0-103">傳回某個運算式除以另一個運算式的餘數。</span><span class="sxs-lookup"><span data-stu-id="0c7e0-103">Returns the remainder of one expression divided by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c7e0-104">語法</span><span class="sxs-lookup"><span data-stu-id="0c7e0-104">Syntax</span></span>  
  
```sql  
dividend % divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="0c7e0-105">引數</span><span class="sxs-lookup"><span data-stu-id="0c7e0-105">Arguments</span></span>  

 `dividend`  
 <span data-ttu-id="0c7e0-106">要當做被除數的數值運算式。</span><span class="sxs-lookup"><span data-stu-id="0c7e0-106">The numeric expression to divide.</span></span> <span data-ttu-id="0c7e0-107">`dividend` 是任何一個數值資料型別的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="0c7e0-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="0c7e0-108">要當做除數的數值運算式。</span><span class="sxs-lookup"><span data-stu-id="0c7e0-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="0c7e0-109">`divisor` 是任何一個數值資料型別的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="0c7e0-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="0c7e0-110">結果類型</span><span class="sxs-lookup"><span data-stu-id="0c7e0-110">Result Types</span></span>  

 <span data-ttu-id="0c7e0-111">Edm.Int32</span><span class="sxs-lookup"><span data-stu-id="0c7e0-111">Edm.Int32</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c7e0-112">範例</span><span class="sxs-lookup"><span data-stu-id="0c7e0-112">Example</span></span>  

 <span data-ttu-id="0c7e0-113">下列 Entity SQL 查詢會使用 % 算術運算子來傳回某個運算式除以另一個運算式的餘數。</span><span class="sxs-lookup"><span data-stu-id="0c7e0-113">The following Entity SQL query uses the % arithmetic operator to return the remainder of one expression divided by another.</span></span> <span data-ttu-id="0c7e0-114">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="0c7e0-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="0c7e0-115">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="0c7e0-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="0c7e0-116">遵循 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。</span><span class="sxs-lookup"><span data-stu-id="0c7e0-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="0c7e0-117">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="0c7e0-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#MODULO](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#modulo)]  
  
## <a name="see-also"></a><span data-ttu-id="0c7e0-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c7e0-118">See also</span></span>

- [<span data-ttu-id="0c7e0-119">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="0c7e0-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
