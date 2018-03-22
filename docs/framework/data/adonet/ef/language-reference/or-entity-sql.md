---
title: '|| (OR) (Entity SQL)'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
caps.latest.revision: ''
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: b44934aa0db73f872f0ab27a4c36c5c615855de1
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="-or-entity-sql"></a><span data-ttu-id="09386-102">|| (OR) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="09386-102">|| (OR) (Entity SQL)</span></span>
<span data-ttu-id="09386-103">結合兩個 `Boolean` 運算式。</span><span class="sxs-lookup"><span data-stu-id="09386-103">Combines two `Boolean` expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09386-104">語法</span><span class="sxs-lookup"><span data-stu-id="09386-104">Syntax</span></span>  
  
```  
boolean_expression OR boolean_expression  
or   
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="09386-105">引數</span><span class="sxs-lookup"><span data-stu-id="09386-105">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="09386-106">傳回 `Boolean`的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="09386-106">Any valid expression that returns a `Boolean`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="09386-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="09386-107">Return Value</span></span>  
 <span data-ttu-id="09386-108">當其中一個條件為`true` 時就會傳回 `true`，否則會傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="09386-108">`true` when either of the conditions is `true`; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09386-109">備註</span><span class="sxs-lookup"><span data-stu-id="09386-109">Remarks</span></span>  
 <span data-ttu-id="09386-110">OR 是 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 邏輯運算子，</span><span class="sxs-lookup"><span data-stu-id="09386-110">OR is an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] logical operator.</span></span> <span data-ttu-id="09386-111">它是用來結合兩個條件。</span><span class="sxs-lookup"><span data-stu-id="09386-111">It is used to combine two conditions.</span></span> <span data-ttu-id="09386-112">當在陳述式中使用一個以上的邏輯運算子時，OR 運算子會在 AND 運算子之後評估。</span><span class="sxs-lookup"><span data-stu-id="09386-112">When more than one logical operator is used in a statement, OR operators are evaluated after AND operators.</span></span> <span data-ttu-id="09386-113">然而，您可以使用括號來變更評估的順序。</span><span class="sxs-lookup"><span data-stu-id="09386-113">However, you can change the order of evaluation by using parentheses.</span></span>  
  
 <span data-ttu-id="09386-114">雙分隔號 (&#124; &#124;) 具有相同的功能與 OR 運算子。</span><span class="sxs-lookup"><span data-stu-id="09386-114">Double vertical bars (&#124;&#124;) have the same functionality as the OR operator.</span></span>  
  
 <span data-ttu-id="09386-115">下表顯示可能的輸入值和傳回型別。</span><span class="sxs-lookup"><span data-stu-id="09386-115">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="09386-116">true</span><span class="sxs-lookup"><span data-stu-id="09386-116">TRUE</span></span>|<span data-ttu-id="09386-117">TRUE</span><span class="sxs-lookup"><span data-stu-id="09386-117">TRUE</span></span>|<span data-ttu-id="09386-118">TRUE</span><span class="sxs-lookup"><span data-stu-id="09386-118">TRUE</span></span>|  
|`FALSE`|<span data-ttu-id="09386-119">TRUE</span><span class="sxs-lookup"><span data-stu-id="09386-119">TRUE</span></span>|<span data-ttu-id="09386-120">FALSE</span><span class="sxs-lookup"><span data-stu-id="09386-120">FALSE</span></span>|<span data-ttu-id="09386-121">NULL</span><span class="sxs-lookup"><span data-stu-id="09386-121">NULL</span></span>|  
|`NULL`|<span data-ttu-id="09386-122">TRUE</span><span class="sxs-lookup"><span data-stu-id="09386-122">TRUE</span></span>|<span data-ttu-id="09386-123">NULL</span><span class="sxs-lookup"><span data-stu-id="09386-123">NULL</span></span>|<span data-ttu-id="09386-124">NULL</span><span class="sxs-lookup"><span data-stu-id="09386-124">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="09386-125">範例</span><span class="sxs-lookup"><span data-stu-id="09386-125">Example</span></span>  
 <span data-ttu-id="09386-126">下列 Entity SQL 查詢會使用 OR 運算子結合兩個 `Boolean` 運算式。</span><span class="sxs-lookup"><span data-stu-id="09386-126">The following Entity SQL query uses the OR operator to combine two `Boolean` expressions.</span></span> <span data-ttu-id="09386-127">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="09386-127">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="09386-128">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="09386-128">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="09386-129">遵循 [如何：執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。</span><span class="sxs-lookup"><span data-stu-id="09386-129">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="09386-130">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="09386-130">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#OR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#or)]  
  
## <a name="see-also"></a><span data-ttu-id="09386-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="09386-131">See Also</span></span>  
 [<span data-ttu-id="09386-132">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="09386-132">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
