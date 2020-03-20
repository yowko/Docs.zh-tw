---
title: '&amp;&amp;（和）（實體 SQL）'
ms.date: 03/30/2017
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
ms.openlocfilehash: eccad616de287a39c42e986cea84dc22feec7f70
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150504"
---
# <a name="ampamp-and-entity-sql"></a><span data-ttu-id="569c7-102">&amp;&amp;（和）（實體 SQL）</span><span class="sxs-lookup"><span data-stu-id="569c7-102">&amp;&amp; (AND) (Entity SQL)</span></span>
<span data-ttu-id="569c7-103">如果兩個運算式都是 `true` 則傳回 `true`，否則為 `false` 或 `NULL`。</span><span class="sxs-lookup"><span data-stu-id="569c7-103">Returns `true` if both expressions are `true`; otherwise, `false` or `NULL`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="569c7-104">語法</span><span class="sxs-lookup"><span data-stu-id="569c7-104">Syntax</span></span>  
  
```csharp  
boolean_expression AND boolean_expression
```

<span data-ttu-id="569c7-105">或</span><span class="sxs-lookup"><span data-stu-id="569c7-105">or</span></span>  

```csharp
boolean_expression && boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="569c7-106">引數</span><span class="sxs-lookup"><span data-stu-id="569c7-106">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="569c7-107">傳回布林值的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="569c7-107">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="569c7-108">備註</span><span class="sxs-lookup"><span data-stu-id="569c7-108">Remarks</span></span>  
 <span data-ttu-id="569c7-109">雙連字號 (&&) 的功能與 AND 運算子相同。</span><span class="sxs-lookup"><span data-stu-id="569c7-109">Double ampersands (&&) have the same functionality as the AND operator.</span></span>  
  
 <span data-ttu-id="569c7-110">下表顯示可能的輸入值和傳回型別。</span><span class="sxs-lookup"><span data-stu-id="569c7-110">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="569c7-111">TRUE</span><span class="sxs-lookup"><span data-stu-id="569c7-111">TRUE</span></span>|<span data-ttu-id="569c7-112">FALSE</span><span class="sxs-lookup"><span data-stu-id="569c7-112">FALSE</span></span>|<span data-ttu-id="569c7-113">NULL</span><span class="sxs-lookup"><span data-stu-id="569c7-113">NULL</span></span>|  
|`FALSE`|<span data-ttu-id="569c7-114">FALSE</span><span class="sxs-lookup"><span data-stu-id="569c7-114">FALSE</span></span>|<span data-ttu-id="569c7-115">FALSE</span><span class="sxs-lookup"><span data-stu-id="569c7-115">FALSE</span></span>|<span data-ttu-id="569c7-116">FALSE</span><span class="sxs-lookup"><span data-stu-id="569c7-116">FALSE</span></span>|  
|`NULL`|<span data-ttu-id="569c7-117">NULL</span><span class="sxs-lookup"><span data-stu-id="569c7-117">NULL</span></span>|<span data-ttu-id="569c7-118">FALSE</span><span class="sxs-lookup"><span data-stu-id="569c7-118">FALSE</span></span>|<span data-ttu-id="569c7-119">NULL</span><span class="sxs-lookup"><span data-stu-id="569c7-119">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="569c7-120">範例</span><span class="sxs-lookup"><span data-stu-id="569c7-120">Example</span></span>  
 <span data-ttu-id="569c7-121">下列 Entity SQL 查詢會示範如何使用 AND 運算子。</span><span class="sxs-lookup"><span data-stu-id="569c7-121">The following Entity SQL query demonstrates how to use the AND operator.</span></span> <span data-ttu-id="569c7-122">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="569c7-122">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="569c7-123">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="569c7-123">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="569c7-124">遵循 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。</span><span class="sxs-lookup"><span data-stu-id="569c7-124">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="569c7-125">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="569c7-125">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## <a name="see-also"></a><span data-ttu-id="569c7-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="569c7-126">See also</span></span>

- [<span data-ttu-id="569c7-127">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="569c7-127">Entity SQL Reference</span></span>](entity-sql-reference.md)
