---
title: '&lt; (小於) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 1fc2a039-3ad6-4b3c-b41d-09932e803f86
ms.openlocfilehash: e11f28fd05cb49524b5a0ff854f951385603602f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="lt-less-than-entity-sql"></a><span data-ttu-id="d29bc-102">&lt; (小於) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d29bc-102">&lt; (Less Than) (Entity SQL)</span></span>
<span data-ttu-id="d29bc-103">比較兩個運算式來判斷左運算式的值是否小於右運算式。</span><span class="sxs-lookup"><span data-stu-id="d29bc-103">Compares two expressions to determine whether the left expression has a value less than the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d29bc-104">語法</span><span class="sxs-lookup"><span data-stu-id="d29bc-104">Syntax</span></span>  
  
```  
expression < expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="d29bc-105">引數</span><span class="sxs-lookup"><span data-stu-id="d29bc-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="d29bc-106">任何有效的運算式。</span><span class="sxs-lookup"><span data-stu-id="d29bc-106">Any valid expression.</span></span> <span data-ttu-id="d29bc-107">兩個運算式都必須有可隱含轉換的資料型別。</span><span class="sxs-lookup"><span data-stu-id="d29bc-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="d29bc-108">結果型別</span><span class="sxs-lookup"><span data-stu-id="d29bc-108">Result Types</span></span>  
 <span data-ttu-id="d29bc-109">如果左運算式的值小於右運算式則為`true` ；否則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="d29bc-109">`true` if the left expression has a value less than the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d29bc-110">範例</span><span class="sxs-lookup"><span data-stu-id="d29bc-110">Example</span></span>  
 <span data-ttu-id="d29bc-111">下列 Entity SQL 查詢使用 < 比較運算子來比較兩個運算式，以判斷左運算式的值是否小於右運算式。</span><span class="sxs-lookup"><span data-stu-id="d29bc-111">The following Entity SQL query uses < comparison operator to compare two expressions to determine whether the left expression has a value less than the right expression.</span></span> <span data-ttu-id="d29bc-112">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="d29bc-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="d29bc-113">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="d29bc-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="d29bc-114">遵循 [如何：執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。</span><span class="sxs-lookup"><span data-stu-id="d29bc-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="d29bc-115">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="d29bc-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less)]  
  
## <a name="see-also"></a><span data-ttu-id="d29bc-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d29bc-116">See Also</span></span>  
 [<span data-ttu-id="d29bc-117">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="d29bc-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
