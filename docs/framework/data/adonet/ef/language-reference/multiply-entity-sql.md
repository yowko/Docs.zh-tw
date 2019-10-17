---
title: '* 乘以（Entity SQL）'
ms.date: 03/30/2017
ms.assetid: 508ce246-4e86-47dd-a605-4af4bebb9891
ms.openlocfilehash: 7006f5143e8cc18156f748ae7664f3787c9ff5c9
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319618"
---
# <a name="-multiply-entity-sql"></a><span data-ttu-id="dd5ce-102">\* (乘號) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="dd5ce-102">\* (Multiply) (Entity SQL)</span></span>
<span data-ttu-id="dd5ce-103">將兩個運算式相乘。</span><span class="sxs-lookup"><span data-stu-id="dd5ce-103">Multiplies two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd5ce-104">語法</span><span class="sxs-lookup"><span data-stu-id="dd5ce-104">Syntax</span></span>  
  
```sql  
expression * expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="dd5ce-105">引數</span><span class="sxs-lookup"><span data-stu-id="dd5ce-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="dd5ce-106">任何一個數值資料型別的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="dd5ce-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="dd5ce-107">結果型別</span><span class="sxs-lookup"><span data-stu-id="dd5ce-107">Result Types</span></span>  
 <span data-ttu-id="dd5ce-108">從兩個引數的隱含型別提升產生的資料型別。</span><span class="sxs-lookup"><span data-stu-id="dd5ce-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="dd5ce-109">如需隱含類型升級的詳細資訊，請參閱[類型系統](type-system-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="dd5ce-109">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd5ce-110">範例</span><span class="sxs-lookup"><span data-stu-id="dd5ce-110">Example</span></span>  
 <span data-ttu-id="dd5ce-111">下列 Entity SQL 查詢會使用 \* 算術運算子讓兩個數字相乘。</span><span class="sxs-lookup"><span data-stu-id="dd5ce-111">The following Entity SQL query uses the \* arithmetic operator to multiply two numbers.</span></span> <span data-ttu-id="dd5ce-112">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="dd5ce-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="dd5ce-113">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="dd5ce-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="dd5ce-114">遵循 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。</span><span class="sxs-lookup"><span data-stu-id="dd5ce-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="dd5ce-115">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="dd5ce-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#MULTIPLY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#multiply)]  
  
## <a name="see-also"></a><span data-ttu-id="dd5ce-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="dd5ce-116">See also</span></span>

- [<span data-ttu-id="dd5ce-117">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="dd5ce-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
