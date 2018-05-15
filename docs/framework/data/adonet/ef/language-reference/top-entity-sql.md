---
title: TOP (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4a4a0954-82e2-4eae-bcaf-7c4552f3532d
ms.openlocfilehash: 25afda64aafcd5a97dee7ad4cee25b152ef55907
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="top-entity-sql"></a><span data-ttu-id="1b55b-102">TOP (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="1b55b-102">TOP (Entity SQL)</span></span>
<span data-ttu-id="1b55b-103">SELECT 子句在選擇性 ALL/DISTINCT 修飾詞之後可以有選擇性 TOP 子項子句。</span><span class="sxs-lookup"><span data-stu-id="1b55b-103">The SELECT clause can have an optional TOP sub-clause following the optional ALL/DISTINCT modifier.</span></span> <span data-ttu-id="1b55b-104">TOP 子項子句指定只會從查詢結果傳回第一組資料列。</span><span class="sxs-lookup"><span data-stu-id="1b55b-104">The TOP sub-clause specifies that only the first set of rows will be returned from the query result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b55b-105">語法</span><span class="sxs-lookup"><span data-stu-id="1b55b-105">Syntax</span></span>  
  
```  
[ TOP (n) ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="1b55b-106">引數</span><span class="sxs-lookup"><span data-stu-id="1b55b-106">Arguments</span></span>  
 `n`  
 <span data-ttu-id="1b55b-107">指定傳回資料列數量的數值運算式。</span><span class="sxs-lookup"><span data-stu-id="1b55b-107">The numeric expression that specifies the number of rows to be returned.</span></span> <span data-ttu-id="1b55b-108">`n` 可以是單一數字常值或單一參數。</span><span class="sxs-lookup"><span data-stu-id="1b55b-108">`n` could be a single numeric literal or a single parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b55b-109">備註</span><span class="sxs-lookup"><span data-stu-id="1b55b-109">Remarks</span></span>  
 <span data-ttu-id="1b55b-110">TOP 運算式必須是單一數值常值或單一參數。</span><span class="sxs-lookup"><span data-stu-id="1b55b-110">The TOP expression must be either a single numeric literal or a single parameter.</span></span> <span data-ttu-id="1b55b-111">如果使用常數常值，此常值型別必須可隱含提升為 Edm.Int64 (byte、int16、int32 或 int64 或是對應到可提升為 Edm.Int64 之型別的任何提供者型別)，而且它的值必須大於或等於零。</span><span class="sxs-lookup"><span data-stu-id="1b55b-111">If a constant literal is used, the literal type must be implicitly promotable to Edm.Int64 (byte, int16, int32 or int64 or any provider type that maps to a type that is promotable to Edm.Int64) and its value must be greater than or equal to zero.</span></span> <span data-ttu-id="1b55b-112">否則將會引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1b55b-112">Otherwise an exception will be raised.</span></span> <span data-ttu-id="1b55b-113">如果參數是當做運算式使用，此參數型別也必須可隱含提升為 Edm.Int64，但是在編譯期間並不會驗證實際的參數值，因為參數值是晚期繫結的。</span><span class="sxs-lookup"><span data-stu-id="1b55b-113">If a parameter is used as an expression, the parameter type must also be implicitly promotable to Edm.Int64, but there will be no validation of the actual parameter value during compilation because the parameter values are late bounded.</span></span>  
  
 <span data-ttu-id="1b55b-114">以下是常數 TOP 運算式的範例：</span><span class="sxs-lookup"><span data-stu-id="1b55b-114">The following is an example of constant TOP expression:</span></span>  
  
 `select distinct top(10) c.a1, c.a2 from T as a`  
  
 <span data-ttu-id="1b55b-115">以下是參數化 TOP 運算式的範例：</span><span class="sxs-lookup"><span data-stu-id="1b55b-115">The following is an example of parametrized TOP expression:</span></span>  
  
 `select distinct top(@topParam) c.a1, c.a2 from T as a`  
  
 <span data-ttu-id="1b55b-116">除非查詢已排序，否則 TOP 將不具決定性。</span><span class="sxs-lookup"><span data-stu-id="1b55b-116">TOP is non-deterministic unless the query is sorted.</span></span> <span data-ttu-id="1b55b-117">如果您要查詢具有決定性的結果，請在 [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) 子句中使用 [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) 和 [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) 次子句。</span><span class="sxs-lookup"><span data-stu-id="1b55b-117">If you require a deterministic result, use the [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) and [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) sub-clauses in the [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) clause.</span></span> <span data-ttu-id="1b55b-118">TOP 和 SKIP/LIMIT 會互斥。</span><span class="sxs-lookup"><span data-stu-id="1b55b-118">The TOP and SKIP/LIMIT are mutually exclusive.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b55b-119">範例</span><span class="sxs-lookup"><span data-stu-id="1b55b-119">Example</span></span>  
 <span data-ttu-id="1b55b-120">下列 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢使用 TOP，指定從查詢結果傳回的頂端第一行資料列。</span><span class="sxs-lookup"><span data-stu-id="1b55b-120">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the TOP to specify the top one row to be returned from the query result.</span></span> <span data-ttu-id="1b55b-121">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="1b55b-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="1b55b-122">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="1b55b-122">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="1b55b-123">遵循 [如何：執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。</span><span class="sxs-lookup"><span data-stu-id="1b55b-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="1b55b-124">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="1b55b-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#TOP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#top)]  
  
## <a name="see-also"></a><span data-ttu-id="1b55b-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b55b-125">See Also</span></span>  
 [<span data-ttu-id="1b55b-126">SELECT</span><span class="sxs-lookup"><span data-stu-id="1b55b-126">SELECT</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)  
 [<span data-ttu-id="1b55b-127">SKIP</span><span class="sxs-lookup"><span data-stu-id="1b55b-127">SKIP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)  
 [<span data-ttu-id="1b55b-128">LIMIT</span><span class="sxs-lookup"><span data-stu-id="1b55b-128">LIMIT</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)  
 [<span data-ttu-id="1b55b-129">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="1b55b-129">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
 [<span data-ttu-id="1b55b-130">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="1b55b-130">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
