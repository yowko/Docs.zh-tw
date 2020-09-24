---
title: '-  (除以)  (Entity SQL) '
ms.date: 03/30/2017
ms.assetid: ef48c368-f3ed-4275-8ada-4e9649781262
ms.openlocfilehash: d7d25d8c5b91850b21e36ba8f6f668af7a7d0045
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148157"
---
# <a name="-divide-entity-sql"></a><span data-ttu-id="d4ab0-102">/ (除號) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d4ab0-102">/ (Divide) (Entity SQL)</span></span>

<span data-ttu-id="d4ab0-103">兩個數字相除。</span><span class="sxs-lookup"><span data-stu-id="d4ab0-103">Divides one number by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4ab0-104">語法</span><span class="sxs-lookup"><span data-stu-id="d4ab0-104">Syntax</span></span>  
  
```sql  
dividend / divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="d4ab0-105">引數</span><span class="sxs-lookup"><span data-stu-id="d4ab0-105">Arguments</span></span>  

 `dividend`  
 <span data-ttu-id="d4ab0-106">要當做被除數的數值運算式。</span><span class="sxs-lookup"><span data-stu-id="d4ab0-106">The numeric expression to divide.</span></span> <span data-ttu-id="d4ab0-107">`dividend` 是任何一個數值資料型別的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="d4ab0-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="d4ab0-108">要當做除數的數值運算式。</span><span class="sxs-lookup"><span data-stu-id="d4ab0-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="d4ab0-109">`divisor` 是任何一個數值資料型別的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="d4ab0-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="d4ab0-110">結果類型</span><span class="sxs-lookup"><span data-stu-id="d4ab0-110">Result Types</span></span>  

 <span data-ttu-id="d4ab0-111">從兩個引數的隱含型別提升產生的資料型別。</span><span class="sxs-lookup"><span data-stu-id="d4ab0-111">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="d4ab0-112">如需隱含類型升級的詳細資訊，請參閱 [類型系統](type-system-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="d4ab0-112">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4ab0-113">範例</span><span class="sxs-lookup"><span data-stu-id="d4ab0-113">Example</span></span>  

 <span data-ttu-id="d4ab0-114">下列 Entity SQL 查詢會使用/算術運算子，將一個數位除以另一個數位。</span><span class="sxs-lookup"><span data-stu-id="d4ab0-114">The following Entity SQL query uses the / arithmetic operator to divide one number by another.</span></span> <span data-ttu-id="d4ab0-115">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="d4ab0-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="d4ab0-116">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="d4ab0-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="d4ab0-117">遵循 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。</span><span class="sxs-lookup"><span data-stu-id="d4ab0-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="d4ab0-118">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="d4ab0-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#DIVIDE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#divide)]  
  
## <a name="see-also"></a><span data-ttu-id="d4ab0-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4ab0-119">See also</span></span>

- [<span data-ttu-id="d4ab0-120">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="d4ab0-120">Entity SQL Reference</span></span>](entity-sql-reference.md)
