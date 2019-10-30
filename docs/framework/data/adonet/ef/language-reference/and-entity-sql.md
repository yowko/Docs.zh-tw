---
title: '&amp;&amp; （和）（Entity SQL）'
ms.date: 03/30/2017
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
ms.openlocfilehash: be6e7120e6c19714f151aa38a8b9a1355de29d1a
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039959"
---
# <a name="ampamp-and-entity-sql"></a><span data-ttu-id="66b37-102">&amp;&amp; （和）（Entity SQL）</span><span class="sxs-lookup"><span data-stu-id="66b37-102">&amp;&amp; (AND) (Entity SQL)</span></span>
<span data-ttu-id="66b37-103">如果兩個運算式都是 `true` 則傳回 `true`，否則為 `false` 或 `NULL`。</span><span class="sxs-lookup"><span data-stu-id="66b37-103">Returns `true` if both expressions are `true`; otherwise, `false` or `NULL`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66b37-104">語法</span><span class="sxs-lookup"><span data-stu-id="66b37-104">Syntax</span></span>  
  
```csharp  
boolean_expression AND boolean_expression
```
 
<span data-ttu-id="66b37-105">或</span><span class="sxs-lookup"><span data-stu-id="66b37-105">or</span></span>  

```csharp
boolean_expression && boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="66b37-106">引數</span><span class="sxs-lookup"><span data-stu-id="66b37-106">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="66b37-107">傳回布林值的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="66b37-107">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66b37-108">備註</span><span class="sxs-lookup"><span data-stu-id="66b37-108">Remarks</span></span>  
 <span data-ttu-id="66b37-109">雙連字號 (&&) 的功能與 AND 運算子相同。</span><span class="sxs-lookup"><span data-stu-id="66b37-109">Double ampersands (&&) have the same functionality as the AND operator.</span></span>  
  
 <span data-ttu-id="66b37-110">下表顯示可能的輸入值和傳回型別。</span><span class="sxs-lookup"><span data-stu-id="66b37-110">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="66b37-111">true</span><span class="sxs-lookup"><span data-stu-id="66b37-111">TRUE</span></span>|<span data-ttu-id="66b37-112">false</span><span class="sxs-lookup"><span data-stu-id="66b37-112">FALSE</span></span>|<span data-ttu-id="66b37-113">NULL</span><span class="sxs-lookup"><span data-stu-id="66b37-113">NULL</span></span>|  
|`FALSE`|<span data-ttu-id="66b37-114">false</span><span class="sxs-lookup"><span data-stu-id="66b37-114">FALSE</span></span>|<span data-ttu-id="66b37-115">false</span><span class="sxs-lookup"><span data-stu-id="66b37-115">FALSE</span></span>|<span data-ttu-id="66b37-116">false</span><span class="sxs-lookup"><span data-stu-id="66b37-116">FALSE</span></span>|  
|`NULL`|<span data-ttu-id="66b37-117">NULL</span><span class="sxs-lookup"><span data-stu-id="66b37-117">NULL</span></span>|<span data-ttu-id="66b37-118">false</span><span class="sxs-lookup"><span data-stu-id="66b37-118">FALSE</span></span>|<span data-ttu-id="66b37-119">NULL</span><span class="sxs-lookup"><span data-stu-id="66b37-119">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="66b37-120">範例</span><span class="sxs-lookup"><span data-stu-id="66b37-120">Example</span></span>  
 <span data-ttu-id="66b37-121">下列 Entity SQL 查詢會示範如何使用 AND 運算子。</span><span class="sxs-lookup"><span data-stu-id="66b37-121">The following Entity SQL query demonstrates how to use the AND operator.</span></span> <span data-ttu-id="66b37-122">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="66b37-122">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="66b37-123">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="66b37-123">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="66b37-124">遵循 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。</span><span class="sxs-lookup"><span data-stu-id="66b37-124">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="66b37-125">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="66b37-125">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## <a name="see-also"></a><span data-ttu-id="66b37-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="66b37-126">See also</span></span>

- [<span data-ttu-id="66b37-127">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="66b37-127">Entity SQL Reference</span></span>](entity-sql-reference.md)
