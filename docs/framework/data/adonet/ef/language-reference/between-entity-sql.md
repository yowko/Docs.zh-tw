---
title: BETWEEN (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 3b27aee261e9195c2cb5f15e369cf26de4c0691a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="between-entity-sql"></a><span data-ttu-id="6ee94-102">BETWEEN (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="6ee94-102">BETWEEN (Entity SQL)</span></span>
<span data-ttu-id="6ee94-103">判斷運算式是否會產生所指定範圍內的值。</span><span class="sxs-lookup"><span data-stu-id="6ee94-103">Determines whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="6ee94-104">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] BETWEEN 運算式的 於 TRANSACT-SQL BETWEEN 運算式相同的功能。</span><span class="sxs-lookup"><span data-stu-id="6ee94-104">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] BETWEEN expression has the same functionality as the Transact-SQL BETWEEN expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ee94-105">語法</span><span class="sxs-lookup"><span data-stu-id="6ee94-105">Syntax</span></span>  
  
```  
expression [ NOT ] BETWEEN begin_expression AND end_expression    
```  
  
## <a name="arguments"></a><span data-ttu-id="6ee94-106">引數</span><span class="sxs-lookup"><span data-stu-id="6ee94-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="6ee94-107">用來測試是否在 `begin_expression` 和 `end_expression` 所定義範圍中的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="6ee94-107">Any valid expression to test for in the range defined by `begin_expression` and `end_expression`.</span></span> <span data-ttu-id="6ee94-108">`expression` 必須與 `begin_expression` 和 `end_expression` 兩者型別相同。</span><span class="sxs-lookup"><span data-stu-id="6ee94-108">`expression` must be the same type as both `begin_expression` and `end_expression`.</span></span>  
  
 `begin_expression`  
 <span data-ttu-id="6ee94-109">任何有效的運算式。</span><span class="sxs-lookup"><span data-stu-id="6ee94-109">Any valid expression.</span></span> <span data-ttu-id="6ee94-110">`begin_expression` 必須與 `expression` 和 `end_expression` 兩者型別相同。</span><span class="sxs-lookup"><span data-stu-id="6ee94-110">`begin_expression` must be the same type as both `expression` and `end_expression`.</span></span> <span data-ttu-id="6ee94-111">`begin_expression` 應小於 `end_expression`，否則便會否定傳回值。</span><span class="sxs-lookup"><span data-stu-id="6ee94-111">`begin_expression` should be less than `end_expression`, else the return value will be negated.</span></span>  
  
 `end_expression`  
 <span data-ttu-id="6ee94-112">任何有效的運算式。</span><span class="sxs-lookup"><span data-stu-id="6ee94-112">Any valid expression.</span></span> <span data-ttu-id="6ee94-113">`end_expression` 必須與 `expression` 和 `begin_expression` 兩者型別相同。</span><span class="sxs-lookup"><span data-stu-id="6ee94-113">`end_expression` must be the same type as both `expression` and `begin_expression`.</span></span>  
  
 <span data-ttu-id="6ee94-114">NOT</span><span class="sxs-lookup"><span data-stu-id="6ee94-114">NOT</span></span>  
 <span data-ttu-id="6ee94-115">指定要否定 BETWEEN 的結果。</span><span class="sxs-lookup"><span data-stu-id="6ee94-115">Specifies that the result of BETWEEN be negated.</span></span>  
  
 <span data-ttu-id="6ee94-116">AND</span><span class="sxs-lookup"><span data-stu-id="6ee94-116">AND</span></span>  
 <span data-ttu-id="6ee94-117">做為一個預留位置，用來指出 `expression` 應該在 `begin_expression` 和 `end_expression` 所指示的範圍內。</span><span class="sxs-lookup"><span data-stu-id="6ee94-117">Acts as a placeholder that indicates `expression` should be within the range indicated by `begin_expression` and `end_expression`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6ee94-118">傳回值</span><span class="sxs-lookup"><span data-stu-id="6ee94-118">Return Value</span></span>  
 <span data-ttu-id="6ee94-119">如果 `true` 是在 `expression` 和 `begin_expression` 所指定的範圍內則為 `end_expression`；否則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="6ee94-119">`true` if `expression` is between the range indicated by `begin_expression` and `end_expression`; otherwise, `false`.</span></span> <span data-ttu-id="6ee94-120">如果 `null` 為 `expression`，或者 `null` 或 `begin_expression` 為 `end_expression`，便會傳回 `null`。</span><span class="sxs-lookup"><span data-stu-id="6ee94-120">`null` will be returned if `expression` is `null` or if `begin_expression` or `end_expression` is `null`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ee94-121">備註</span><span class="sxs-lookup"><span data-stu-id="6ee94-121">Remarks</span></span>  
 <span data-ttu-id="6ee94-122">若要指定排除範圍，請使用大於 (>) 及小於 (<) 運算子，不要用 BETWEEN。</span><span class="sxs-lookup"><span data-stu-id="6ee94-122">To specify an exclusive range, use the greater than (>) and less than (<) operators instead of BETWEEN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ee94-123">範例</span><span class="sxs-lookup"><span data-stu-id="6ee94-123">Example</span></span>  
 <span data-ttu-id="6ee94-124">以下 Entity SQL 查詢使用 BETWEEN 運算子來判斷運算式是否會產生所指定範圍內的值。</span><span class="sxs-lookup"><span data-stu-id="6ee94-124">The following Entity SQL query uses BETWEEN operator to determine whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="6ee94-125">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="6ee94-125">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="6ee94-126">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="6ee94-126">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="6ee94-127">遵循 [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。</span><span class="sxs-lookup"><span data-stu-id="6ee94-127">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="6ee94-128">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="6ee94-128">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a><span data-ttu-id="6ee94-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="6ee94-129">See Also</span></span>  
 [<span data-ttu-id="6ee94-130">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="6ee94-130">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
