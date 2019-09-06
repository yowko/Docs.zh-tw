---
title: '>= (大於或等於) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 70780ac4-0123-4da8-b731-8af856daffe3
ms.openlocfilehash: fb97786687616ff92f0e4402c86aef02de2e70c9
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250874"
---
# <a name="-greater-than-or-equal-to-entity-sql"></a><span data-ttu-id="1f7f3-102">> = (大於或等於) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="1f7f3-102">>= (Greater Than or Equal To) (Entity SQL)</span></span>
<span data-ttu-id="1f7f3-103">比較兩個運算式來判斷左運算式的值是否大於或等於右運算式。</span><span class="sxs-lookup"><span data-stu-id="1f7f3-103">Compares two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f7f3-104">語法</span><span class="sxs-lookup"><span data-stu-id="1f7f3-104">Syntax</span></span>  
  
```  
expression >= expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="1f7f3-105">引數</span><span class="sxs-lookup"><span data-stu-id="1f7f3-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="1f7f3-106">任何有效的運算式。</span><span class="sxs-lookup"><span data-stu-id="1f7f3-106">Any valid expression.</span></span> <span data-ttu-id="1f7f3-107">兩個運算式都必須有可隱含轉換的資料型別。</span><span class="sxs-lookup"><span data-stu-id="1f7f3-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="1f7f3-108">結果型別</span><span class="sxs-lookup"><span data-stu-id="1f7f3-108">Result Types</span></span>  
 <span data-ttu-id="1f7f3-109">如果左運算式的值大於或等於右運算式則為`true` ；否則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="1f7f3-109">`true` if the left expression has a value greater than or equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f7f3-110">範例</span><span class="sxs-lookup"><span data-stu-id="1f7f3-110">Example</span></span>  
 <span data-ttu-id="1f7f3-111">下列 Entity SQL 查詢使用 >= 比較運算子來比較兩個運算式，以判斷左運算式的值是否大於或等於右運算式。</span><span class="sxs-lookup"><span data-stu-id="1f7f3-111">The following Entity SQL query uses >= comparison operator to compare two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span> <span data-ttu-id="1f7f3-112">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="1f7f3-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="1f7f3-113">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="1f7f3-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="1f7f3-114">[遵循 how to:執行可傳回 StructuralType 結果](../how-to-execute-a-query-that-returns-structuraltype-results.md)的查詢。</span><span class="sxs-lookup"><span data-stu-id="1f7f3-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="1f7f3-115">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="1f7f3-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER_OR_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater_or_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="1f7f3-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f7f3-116">See also</span></span>

- [<span data-ttu-id="1f7f3-117">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="1f7f3-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
