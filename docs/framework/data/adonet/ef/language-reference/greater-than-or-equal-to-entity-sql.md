---
title: '>= (大於或等於) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 70780ac4-0123-4da8-b731-8af856daffe3
ms.openlocfilehash: 1e2eef7c98aefd93c6ef388888661ac758fd8e30
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166110"
---
# <a name="-greater-than-or-equal-to-entity-sql"></a><span data-ttu-id="8af8c-102">> = (大於或等於) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="8af8c-102">>= (Greater Than or Equal To) (Entity SQL)</span></span>
<span data-ttu-id="8af8c-103">比較兩個運算式來判斷左運算式的值是否大於或等於右運算式。</span><span class="sxs-lookup"><span data-stu-id="8af8c-103">Compares two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8af8c-104">語法</span><span class="sxs-lookup"><span data-stu-id="8af8c-104">Syntax</span></span>  
  
```  
expression >= expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="8af8c-105">引數</span><span class="sxs-lookup"><span data-stu-id="8af8c-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="8af8c-106">任何有效的運算式。</span><span class="sxs-lookup"><span data-stu-id="8af8c-106">Any valid expression.</span></span> <span data-ttu-id="8af8c-107">兩個運算式都必須有可隱含轉換的資料型別。</span><span class="sxs-lookup"><span data-stu-id="8af8c-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="8af8c-108">結果型別</span><span class="sxs-lookup"><span data-stu-id="8af8c-108">Result Types</span></span>  
 `true` <span data-ttu-id="8af8c-109">如果左的運算式的值大於或等於右邊的運算式;否則， `false`。</span><span class="sxs-lookup"><span data-stu-id="8af8c-109">if the left expression has a value greater than or equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8af8c-110">範例</span><span class="sxs-lookup"><span data-stu-id="8af8c-110">Example</span></span>  
 <span data-ttu-id="8af8c-111">下列 Entity SQL 查詢使用 >= 比較運算子來比較兩個運算式，以判斷左運算式的值是否大於或等於右運算式。</span><span class="sxs-lookup"><span data-stu-id="8af8c-111">The following Entity SQL query uses >= comparison operator to compare two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span> <span data-ttu-id="8af8c-112">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="8af8c-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="8af8c-113">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="8af8c-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="8af8c-114">請依照下列中的程序[How to:執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)。</span><span class="sxs-lookup"><span data-stu-id="8af8c-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="8af8c-115">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="8af8c-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER_OR_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater_or_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="8af8c-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8af8c-116">See also</span></span>

- [<span data-ttu-id="8af8c-117">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="8af8c-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
