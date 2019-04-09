---
title: '!= (不等於) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 3b4a02ad-ddfc-4c42-8dfa-676234461312
ms.openlocfilehash: 3d6e391e708b81c45af82280f200aebdaef41421
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130961"
---
# <a name="-not-equal-to-entity-sql"></a><span data-ttu-id="8c10b-102">!= (不等於) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="8c10b-102">!= (Not Equal To) (Entity SQL)</span></span>
<span data-ttu-id="8c10b-103">比較兩個運算式來判斷左運算式是否不等於右運算式。</span><span class="sxs-lookup"><span data-stu-id="8c10b-103">Compares two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="8c10b-104">!= (不等於) 運算子的功能相當於 <> 運算子。</span><span class="sxs-lookup"><span data-stu-id="8c10b-104">The != (Not Equal To) operator is functionally equivalent to the <> operator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c10b-105">語法</span><span class="sxs-lookup"><span data-stu-id="8c10b-105">Syntax</span></span>  
  
```  
expression != expression  
or  
expression <> expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="8c10b-106">引數</span><span class="sxs-lookup"><span data-stu-id="8c10b-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="8c10b-107">任何有效的運算式。</span><span class="sxs-lookup"><span data-stu-id="8c10b-107">Any valid expression.</span></span> <span data-ttu-id="8c10b-108">兩個運算式都必須有可隱含轉換的資料型別。</span><span class="sxs-lookup"><span data-stu-id="8c10b-108">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="8c10b-109">結果型別</span><span class="sxs-lookup"><span data-stu-id="8c10b-109">Result Types</span></span>  
 `true` <span data-ttu-id="8c10b-110">如果左的運算式是否不等於右邊的運算式;否則， `false`。</span><span class="sxs-lookup"><span data-stu-id="8c10b-110">if the left expression is not equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c10b-111">範例</span><span class="sxs-lookup"><span data-stu-id="8c10b-111">Example</span></span>  
 <span data-ttu-id="8c10b-112">下列 Entity SQL 查詢使用 != 運算子來比較兩個運算式，以判斷左運算式是否不等於右運算式。</span><span class="sxs-lookup"><span data-stu-id="8c10b-112">The following Entity SQL query uses the != operator to compare two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="8c10b-113">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="8c10b-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="8c10b-114">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="8c10b-114">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="8c10b-115">請依照下列中的程序[How to:執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)。</span><span class="sxs-lookup"><span data-stu-id="8c10b-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="8c10b-116">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="8c10b-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NOT_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#not_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="8c10b-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c10b-117">See also</span></span>

- [<span data-ttu-id="8c10b-118">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="8c10b-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
