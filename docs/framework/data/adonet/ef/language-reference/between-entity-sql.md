---
title: BETWEEN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
ms.openlocfilehash: a0f5dd19c439861451b1e88c3ae35f9f265288fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150489"
---
# <a name="between-entity-sql"></a><span data-ttu-id="c4e9a-102">BETWEEN (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="c4e9a-102">BETWEEN (Entity SQL)</span></span>
<span data-ttu-id="c4e9a-103">判斷運算式是否會產生所指定範圍內的值。</span><span class="sxs-lookup"><span data-stu-id="c4e9a-103">Determines whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="c4e9a-104">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] "之間"運算式具有與"轉單-SQL-BETWEEN"運算式相同的功能。</span><span class="sxs-lookup"><span data-stu-id="c4e9a-104">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] BETWEEN expression has the same functionality as the Transact-SQL BETWEEN expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4e9a-105">語法</span><span class="sxs-lookup"><span data-stu-id="c4e9a-105">Syntax</span></span>  
  
```csharp  
expression [ NOT ] BETWEEN begin_expression AND end_expression
```  
  
## <a name="arguments"></a><span data-ttu-id="c4e9a-106">引數</span><span class="sxs-lookup"><span data-stu-id="c4e9a-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="c4e9a-107">用來測試是否在 `begin_expression` 和 `end_expression` 所定義範圍中的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="c4e9a-107">Any valid expression to test for in the range defined by `begin_expression` and `end_expression`.</span></span> <span data-ttu-id="c4e9a-108">`expression` 必須與 `begin_expression` 和 `end_expression` 兩者型別相同。</span><span class="sxs-lookup"><span data-stu-id="c4e9a-108">`expression` must be the same type as both `begin_expression` and `end_expression`.</span></span>  
  
 `begin_expression`  
 <span data-ttu-id="c4e9a-109">任何有效的運算式。</span><span class="sxs-lookup"><span data-stu-id="c4e9a-109">Any valid expression.</span></span> <span data-ttu-id="c4e9a-110">`begin_expression` 必須與 `expression` 和 `end_expression` 兩者型別相同。</span><span class="sxs-lookup"><span data-stu-id="c4e9a-110">`begin_expression` must be the same type as both `expression` and `end_expression`.</span></span> <span data-ttu-id="c4e9a-111">`begin_expression` 應小於 `end_expression`，否則便會否定傳回值。</span><span class="sxs-lookup"><span data-stu-id="c4e9a-111">`begin_expression` should be less than `end_expression`, else the return value will be negated.</span></span>  
  
 `end_expression`  
 <span data-ttu-id="c4e9a-112">任何有效的運算式。</span><span class="sxs-lookup"><span data-stu-id="c4e9a-112">Any valid expression.</span></span> <span data-ttu-id="c4e9a-113">`end_expression` 必須與 `expression` 和 `begin_expression` 兩者型別相同。</span><span class="sxs-lookup"><span data-stu-id="c4e9a-113">`end_expression` must be the same type as both `expression` and `begin_expression`.</span></span>  
  
 <span data-ttu-id="c4e9a-114">NOT</span><span class="sxs-lookup"><span data-stu-id="c4e9a-114">NOT</span></span>  
 <span data-ttu-id="c4e9a-115">指定要否定 BETWEEN 的結果。</span><span class="sxs-lookup"><span data-stu-id="c4e9a-115">Specifies that the result of BETWEEN be negated.</span></span>  
  
 <span data-ttu-id="c4e9a-116">AND</span><span class="sxs-lookup"><span data-stu-id="c4e9a-116">AND</span></span>  
 <span data-ttu-id="c4e9a-117">做為一個預留位置，用來指出 `expression` 應該在 `begin_expression` 和 `end_expression` 所指示的範圍內。</span><span class="sxs-lookup"><span data-stu-id="c4e9a-117">Acts as a placeholder that indicates `expression` should be within the range indicated by `begin_expression` and `end_expression`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c4e9a-118">傳回值</span><span class="sxs-lookup"><span data-stu-id="c4e9a-118">Return Value</span></span>  
 <span data-ttu-id="c4e9a-119">如果 `true` 是在 `expression` 和 `begin_expression` 所指定的範圍內則為 `end_expression`；否則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="c4e9a-119">`true` if `expression` is between the range indicated by `begin_expression` and `end_expression`; otherwise, `false`.</span></span> <span data-ttu-id="c4e9a-120">如果 `null` 為 `expression`，或者 `null` 或 `begin_expression` 為 `end_expression`，便會傳回 `null`。</span><span class="sxs-lookup"><span data-stu-id="c4e9a-120">`null` will be returned if `expression` is `null` or if `begin_expression` or `end_expression` is `null`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4e9a-121">備註</span><span class="sxs-lookup"><span data-stu-id="c4e9a-121">Remarks</span></span>  
 <span data-ttu-id="c4e9a-122">要指定獨佔範圍，請使用大於 （>） 和小於 （<） 運算子而不是"之間"。</span><span class="sxs-lookup"><span data-stu-id="c4e9a-122">To specify an exclusive range, use the greater than (>) and less than (<) operators instead of BETWEEN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4e9a-123">範例</span><span class="sxs-lookup"><span data-stu-id="c4e9a-123">Example</span></span>  
 <span data-ttu-id="c4e9a-124">以下 Entity SQL 查詢使用 BETWEEN 運算子來判斷運算式是否會產生所指定範圍內的值。</span><span class="sxs-lookup"><span data-stu-id="c4e9a-124">The following Entity SQL query uses BETWEEN operator to determine whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="c4e9a-125">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="c4e9a-125">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="c4e9a-126">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="c4e9a-126">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="c4e9a-127">遵循 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。</span><span class="sxs-lookup"><span data-stu-id="c4e9a-127">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="c4e9a-128">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="c4e9a-128">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a><span data-ttu-id="c4e9a-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4e9a-129">See also</span></span>

- [<span data-ttu-id="c4e9a-130">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="c4e9a-130">Entity SQL Reference</span></span>](entity-sql-reference.md)
