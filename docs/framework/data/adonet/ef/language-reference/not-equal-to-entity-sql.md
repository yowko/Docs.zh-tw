---
title: '!= (不等於) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 3b4a02ad-ddfc-4c42-8dfa-676234461312
ms.openlocfilehash: bebe85072f5a2cf6a133b88c6d3f5c97299aa63f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191771"
---
# <a name="-not-equal-to-entity-sql"></a><span data-ttu-id="c91a0-102">!= (不等於) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="c91a0-102">!= (Not Equal To) (Entity SQL)</span></span>

<span data-ttu-id="c91a0-103">比較兩個運算式來判斷左運算式是否不等於右運算式。</span><span class="sxs-lookup"><span data-stu-id="c91a0-103">Compares two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="c91a0-104">!= (不等於) 運算子的功能相當於 <> 運算子。</span><span class="sxs-lookup"><span data-stu-id="c91a0-104">The != (Not Equal To) operator is functionally equivalent to the <> operator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c91a0-105">語法</span><span class="sxs-lookup"><span data-stu-id="c91a0-105">Syntax</span></span>  
  
```sql  
expression != expression  
-- or  
expression <> expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="c91a0-106">引數</span><span class="sxs-lookup"><span data-stu-id="c91a0-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="c91a0-107">任何有效的運算式。</span><span class="sxs-lookup"><span data-stu-id="c91a0-107">Any valid expression.</span></span> <span data-ttu-id="c91a0-108">這兩個運算式的類型，都必須是可以隱含轉換的資料類型。</span><span class="sxs-lookup"><span data-stu-id="c91a0-108">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="c91a0-109">結果類型</span><span class="sxs-lookup"><span data-stu-id="c91a0-109">Result Types</span></span>  

 <span data-ttu-id="c91a0-110">如果左運算式不等於右運算式，則為`true` ，否則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="c91a0-110">`true` if the left expression is not equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c91a0-111">範例</span><span class="sxs-lookup"><span data-stu-id="c91a0-111">Example</span></span>  

 <span data-ttu-id="c91a0-112">下列 Entity SQL 查詢使用 != 運算子來比較兩個運算式，以判斷左運算式是否不等於右運算式。</span><span class="sxs-lookup"><span data-stu-id="c91a0-112">The following Entity SQL query uses the != operator to compare two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="c91a0-113">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="c91a0-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="c91a0-114">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="c91a0-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="c91a0-115">遵循 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。</span><span class="sxs-lookup"><span data-stu-id="c91a0-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="c91a0-116">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="c91a0-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#NOT_EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#not_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="c91a0-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c91a0-117">See also</span></span>

- [<span data-ttu-id="c91a0-118">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="c91a0-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
