---
title: '>= (大於或等於) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 70780ac4-0123-4da8-b731-8af856daffe3
ms.openlocfilehash: b5a8a834c325cca38e2c106ca3f8ee829dd699b2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034147"
---
# <a name="-greater-than-or-equal-to-entity-sql"></a><span data-ttu-id="64c0d-102">> = (大於或等於) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="64c0d-102">>= (Greater Than or Equal To) (Entity SQL)</span></span>
<span data-ttu-id="64c0d-103">比較兩個運算式來判斷左運算式的值是否大於或等於右運算式。</span><span class="sxs-lookup"><span data-stu-id="64c0d-103">Compares two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64c0d-104">語法</span><span class="sxs-lookup"><span data-stu-id="64c0d-104">Syntax</span></span>  
  
```  
expression >= expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="64c0d-105">引數</span><span class="sxs-lookup"><span data-stu-id="64c0d-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="64c0d-106">任何有效的運算式。</span><span class="sxs-lookup"><span data-stu-id="64c0d-106">Any valid expression.</span></span> <span data-ttu-id="64c0d-107">兩個運算式都必須有可隱含轉換的資料型別。</span><span class="sxs-lookup"><span data-stu-id="64c0d-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="64c0d-108">結果型別</span><span class="sxs-lookup"><span data-stu-id="64c0d-108">Result Types</span></span>  
 <span data-ttu-id="64c0d-109">如果左運算式的值大於或等於右運算式則為`true` ；否則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="64c0d-109">`true` if the left expression has a value greater than or equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64c0d-110">範例</span><span class="sxs-lookup"><span data-stu-id="64c0d-110">Example</span></span>  
 <span data-ttu-id="64c0d-111">下列 Entity SQL 查詢使用 >= 比較運算子來比較兩個運算式，以判斷左運算式的值是否大於或等於右運算式。</span><span class="sxs-lookup"><span data-stu-id="64c0d-111">The following Entity SQL query uses >= comparison operator to compare two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span> <span data-ttu-id="64c0d-112">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="64c0d-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="64c0d-113">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="64c0d-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="64c0d-114">請依照下列中的程序[How to:執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)。</span><span class="sxs-lookup"><span data-stu-id="64c0d-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="64c0d-115">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="64c0d-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER_OR_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater_or_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="64c0d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64c0d-116">See also</span></span>

- [<span data-ttu-id="64c0d-117">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="64c0d-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
