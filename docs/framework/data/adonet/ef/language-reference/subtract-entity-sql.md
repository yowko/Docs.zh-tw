---
title: '-  (減去)  (Entity SQL) '
ms.date: 03/30/2017
ms.assetid: bc4327f9-09c0-438f-a008-927c5c478040
ms.openlocfilehash: 17841f336ed186dcbc50b84254048546b15297e7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181033"
---
# <a name="--subtract-entity-sql"></a><span data-ttu-id="e2ac5-102">- (減號) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e2ac5-102">- (Subtract) (Entity SQL)</span></span>

<span data-ttu-id="e2ac5-103">兩個數字相減。</span><span class="sxs-lookup"><span data-stu-id="e2ac5-103">Subtracts two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2ac5-104">語法</span><span class="sxs-lookup"><span data-stu-id="e2ac5-104">Syntax</span></span>  
  
```sql  
expression - expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="e2ac5-105">引數</span><span class="sxs-lookup"><span data-stu-id="e2ac5-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="e2ac5-106">任何一個數值資料型別的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="e2ac5-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="e2ac5-107">結果類型</span><span class="sxs-lookup"><span data-stu-id="e2ac5-107">Result Types</span></span>  

 <span data-ttu-id="e2ac5-108">從兩個引數的隱含型別提升產生的資料型別。</span><span class="sxs-lookup"><span data-stu-id="e2ac5-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="e2ac5-109">如需隱含類型升級的詳細資訊，請參閱 [類型系統](type-system-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="e2ac5-109">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2ac5-110">範例</span><span class="sxs-lookup"><span data-stu-id="e2ac5-110">Example</span></span>  

 <span data-ttu-id="e2ac5-111">下列 Entity SQL 查詢會使用 - 算術運算子讓兩個數字相減。</span><span class="sxs-lookup"><span data-stu-id="e2ac5-111">The following Entity SQL query uses the - arithmetic operator to subtract two numbers.</span></span> <span data-ttu-id="e2ac5-112">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="e2ac5-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="e2ac5-113">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="e2ac5-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="e2ac5-114">遵循 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。</span><span class="sxs-lookup"><span data-stu-id="e2ac5-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="e2ac5-115">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="e2ac5-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#SUBTRACT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#subtract)]  
  
## <a name="see-also"></a><span data-ttu-id="e2ac5-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2ac5-116">See also</span></span>

- [<span data-ttu-id="e2ac5-117">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="e2ac5-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
