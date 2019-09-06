---
title: BETWEEN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
ms.openlocfilehash: 41036e629837bd5861368df545bed9423eac5b23
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251288"
---
# <a name="between-entity-sql"></a><span data-ttu-id="b1d1d-102">BETWEEN (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="b1d1d-102">BETWEEN (Entity SQL)</span></span>
<span data-ttu-id="b1d1d-103">判斷運算式是否會產生所指定範圍內的值。</span><span class="sxs-lookup"><span data-stu-id="b1d1d-103">Determines whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="b1d1d-104">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Between 運算式與 expression 之間的 transact-sql 具有相同的功能。</span><span class="sxs-lookup"><span data-stu-id="b1d1d-104">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] BETWEEN expression has the same functionality as the Transact-SQL BETWEEN expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1d1d-105">語法</span><span class="sxs-lookup"><span data-stu-id="b1d1d-105">Syntax</span></span>  
  
```  
expression [ NOT ] BETWEEN begin_expression AND end_expression    
```  
  
## <a name="arguments"></a><span data-ttu-id="b1d1d-106">引數</span><span class="sxs-lookup"><span data-stu-id="b1d1d-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="b1d1d-107">用來測試是否在 `begin_expression` 和 `end_expression` 所定義範圍中的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="b1d1d-107">Any valid expression to test for in the range defined by `begin_expression` and `end_expression`.</span></span> <span data-ttu-id="b1d1d-108">`expression` 必須與 `begin_expression` 和 `end_expression` 兩者型別相同。</span><span class="sxs-lookup"><span data-stu-id="b1d1d-108">`expression` must be the same type as both `begin_expression` and `end_expression`.</span></span>  
  
 `begin_expression`  
 <span data-ttu-id="b1d1d-109">任何有效的運算式。</span><span class="sxs-lookup"><span data-stu-id="b1d1d-109">Any valid expression.</span></span> <span data-ttu-id="b1d1d-110">`begin_expression` 必須與 `expression` 和 `end_expression` 兩者型別相同。</span><span class="sxs-lookup"><span data-stu-id="b1d1d-110">`begin_expression` must be the same type as both `expression` and `end_expression`.</span></span> <span data-ttu-id="b1d1d-111">`begin_expression` 應小於 `end_expression`，否則便會否定傳回值。</span><span class="sxs-lookup"><span data-stu-id="b1d1d-111">`begin_expression` should be less than `end_expression`, else the return value will be negated.</span></span>  
  
 `end_expression`  
 <span data-ttu-id="b1d1d-112">任何有效的運算式。</span><span class="sxs-lookup"><span data-stu-id="b1d1d-112">Any valid expression.</span></span> <span data-ttu-id="b1d1d-113">`end_expression` 必須與 `expression` 和 `begin_expression` 兩者型別相同。</span><span class="sxs-lookup"><span data-stu-id="b1d1d-113">`end_expression` must be the same type as both `expression` and `begin_expression`.</span></span>  
  
 <span data-ttu-id="b1d1d-114">NOT</span><span class="sxs-lookup"><span data-stu-id="b1d1d-114">NOT</span></span>  
 <span data-ttu-id="b1d1d-115">指定要否定 BETWEEN 的結果。</span><span class="sxs-lookup"><span data-stu-id="b1d1d-115">Specifies that the result of BETWEEN be negated.</span></span>  
  
 <span data-ttu-id="b1d1d-116">AND</span><span class="sxs-lookup"><span data-stu-id="b1d1d-116">AND</span></span>  
 <span data-ttu-id="b1d1d-117">做為一個預留位置，用來指出 `expression` 應該在 `begin_expression` 和 `end_expression` 所指示的範圍內。</span><span class="sxs-lookup"><span data-stu-id="b1d1d-117">Acts as a placeholder that indicates `expression` should be within the range indicated by `begin_expression` and `end_expression`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b1d1d-118">傳回值</span><span class="sxs-lookup"><span data-stu-id="b1d1d-118">Return Value</span></span>  
 <span data-ttu-id="b1d1d-119">如果 `true` 是在 `expression` 和 `begin_expression` 所指定的範圍內則為 `end_expression`；否則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="b1d1d-119">`true` if `expression` is between the range indicated by `begin_expression` and `end_expression`; otherwise, `false`.</span></span> <span data-ttu-id="b1d1d-120">如果 `null` 為 `expression`，或者 `null` 或 `begin_expression` 為 `end_expression`，便會傳回 `null`。</span><span class="sxs-lookup"><span data-stu-id="b1d1d-120">`null` will be returned if `expression` is `null` or if `begin_expression` or `end_expression` is `null`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1d1d-121">備註</span><span class="sxs-lookup"><span data-stu-id="b1d1d-121">Remarks</span></span>  
 <span data-ttu-id="b1d1d-122">若要指定獨佔範圍，請使用大於（>）和小於（<）運算子，而不是介於之間。</span><span class="sxs-lookup"><span data-stu-id="b1d1d-122">To specify an exclusive range, use the greater than (>) and less than (<) operators instead of BETWEEN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1d1d-123">範例</span><span class="sxs-lookup"><span data-stu-id="b1d1d-123">Example</span></span>  
 <span data-ttu-id="b1d1d-124">以下 Entity SQL 查詢使用 BETWEEN 運算子來判斷運算式是否會產生所指定範圍內的值。</span><span class="sxs-lookup"><span data-stu-id="b1d1d-124">The following Entity SQL query uses BETWEEN operator to determine whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="b1d1d-125">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="b1d1d-125">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="b1d1d-126">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="b1d1d-126">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="b1d1d-127">[遵循 how to：執行可傳回 StructuralType 結果](../how-to-execute-a-query-that-returns-structuraltype-results.md)的查詢。</span><span class="sxs-lookup"><span data-stu-id="b1d1d-127">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="b1d1d-128">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="b1d1d-128">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a><span data-ttu-id="b1d1d-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1d1d-129">See also</span></span>

- [<span data-ttu-id="b1d1d-130">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="b1d1d-130">Entity SQL Reference</span></span>](entity-sql-reference.md)
