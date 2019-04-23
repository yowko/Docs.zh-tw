---
title: < （小於） (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 1fc2a039-3ad6-4b3c-b41d-09932e803f86
ms.openlocfilehash: 1ca1cbdf1282782295b659393e8f54aae3ec5649
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59320440"
---
# <a name="-less-than-entity-sql"></a><span data-ttu-id="83ef5-102">\< (小於) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="83ef5-102">\< (Less Than) (Entity SQL)</span></span>
<span data-ttu-id="83ef5-103">比較兩個運算式來判斷左運算式的值是否小於右運算式。</span><span class="sxs-lookup"><span data-stu-id="83ef5-103">Compares two expressions to determine whether the left expression has a value less than the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83ef5-104">語法</span><span class="sxs-lookup"><span data-stu-id="83ef5-104">Syntax</span></span>  
  
```  
expression < expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="83ef5-105">引數</span><span class="sxs-lookup"><span data-stu-id="83ef5-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="83ef5-106">任何有效的運算式。</span><span class="sxs-lookup"><span data-stu-id="83ef5-106">Any valid expression.</span></span> <span data-ttu-id="83ef5-107">兩個運算式都必須有可隱含轉換的資料型別。</span><span class="sxs-lookup"><span data-stu-id="83ef5-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="83ef5-108">結果型別</span><span class="sxs-lookup"><span data-stu-id="83ef5-108">Result Types</span></span>  
 <span data-ttu-id="83ef5-109">如果左運算式的值小於右運算式則為`true` ；否則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="83ef5-109">`true` if the left expression has a value less than the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83ef5-110">範例</span><span class="sxs-lookup"><span data-stu-id="83ef5-110">Example</span></span>  
 <span data-ttu-id="83ef5-111">下列 Entity SQL 查詢使用 < 比較運算子來比較兩個運算式，以判斷左運算式的值是否小於右運算式。</span><span class="sxs-lookup"><span data-stu-id="83ef5-111">The following Entity SQL query uses < comparison operator to compare two expressions to determine whether the left expression has a value less than the right expression.</span></span> <span data-ttu-id="83ef5-112">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="83ef5-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="83ef5-113">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="83ef5-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="83ef5-114">請依照下列中的程序[How to:執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)。</span><span class="sxs-lookup"><span data-stu-id="83ef5-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="83ef5-115">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="83ef5-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less)]  
  
## <a name="see-also"></a><span data-ttu-id="83ef5-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83ef5-116">See also</span></span>

- [<span data-ttu-id="83ef5-117">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="83ef5-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
