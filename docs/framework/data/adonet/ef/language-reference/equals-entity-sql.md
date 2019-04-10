---
title: = (等號) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
ms.openlocfilehash: d50ede1964f6d6b9025a7214efe90e878aa55a0c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59333154"
---
# <a name="-equals-entity-sql"></a><span data-ttu-id="3a472-102">= (等號) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="3a472-102">= (Equals) (Entity SQL)</span></span>
<span data-ttu-id="3a472-103">比較兩個運算式是否相等。</span><span class="sxs-lookup"><span data-stu-id="3a472-103">Compares the equality of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a472-104">語法</span><span class="sxs-lookup"><span data-stu-id="3a472-104">Syntax</span></span>  
  
```  
expression = expression  
or   
expression == expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="3a472-105">引數</span><span class="sxs-lookup"><span data-stu-id="3a472-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="3a472-106">任何有效的運算式。</span><span class="sxs-lookup"><span data-stu-id="3a472-106">Any valid expression.</span></span> <span data-ttu-id="3a472-107">兩個運算式都必須有可隱含轉換的資料型別。</span><span class="sxs-lookup"><span data-stu-id="3a472-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="3a472-108">結果型別</span><span class="sxs-lookup"><span data-stu-id="3a472-108">Result Types</span></span>  
 `true` <span data-ttu-id="3a472-109">如果左的運算式等於右運算式;否則， `false`。</span><span class="sxs-lookup"><span data-stu-id="3a472-109">if the left expression is equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3a472-110">備註</span><span class="sxs-lookup"><span data-stu-id="3a472-110">Remarks</span></span>  
 <span data-ttu-id="3a472-111">== 運算子就相當於 =。</span><span class="sxs-lookup"><span data-stu-id="3a472-111">The == operator is equivalent to =.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a472-112">範例</span><span class="sxs-lookup"><span data-stu-id="3a472-112">Example</span></span>  
 <span data-ttu-id="3a472-113">以下 Entity SQL 查詢使用 = 比較運算子來比較兩個運算式是否相等。</span><span class="sxs-lookup"><span data-stu-id="3a472-113">The following Entity SQL query uses = comparison operator to compare the equality of two expressions.</span></span> <span data-ttu-id="3a472-114">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="3a472-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="3a472-115">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="3a472-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="3a472-116">請依照下列中的程序[How to:執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)。</span><span class="sxs-lookup"><span data-stu-id="3a472-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="3a472-117">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="3a472-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#equals)]  
  
## <a name="see-also"></a><span data-ttu-id="3a472-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a472-118">See also</span></span>

- [<span data-ttu-id="3a472-119">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="3a472-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
