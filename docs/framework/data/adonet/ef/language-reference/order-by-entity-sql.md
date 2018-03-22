---
title: ORDER BY (Entity SQL)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c0b61572-ecee-41eb-9d7f-74132ec8a26c
caps.latest.revision: ''
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 4321c5fd3f173b209d99e096ec0ebf8788437c3d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="order-by-entity-sql"></a><span data-ttu-id="42d40-102">ORDER BY (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="42d40-102">ORDER BY (Entity SQL)</span></span>
<span data-ttu-id="42d40-103">指定 SELECT 陳述式所傳回物件使用的排序順序。</span><span class="sxs-lookup"><span data-stu-id="42d40-103">Specifies the sort order used on objects returned in a SELECT statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42d40-104">語法</span><span class="sxs-lookup"><span data-stu-id="42d40-104">Syntax</span></span>  
  
```  
[ ORDER BY   
   {  
      order_by_expression [SKIP n] [LIMIT n]  
      [ COLLATE collation_name ]  
      [ ASC | DESC ]  
   }  
   [ ,…n ]   
]  
```  
  
## <a name="arguments"></a><span data-ttu-id="42d40-105">引數</span><span class="sxs-lookup"><span data-stu-id="42d40-105">Arguments</span></span>  
 `order_by_expression`  
 <span data-ttu-id="42d40-106">任何指定要排序之屬性的有效查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="42d40-106">Any valid query expression specifying a property on which to sort.</span></span> <span data-ttu-id="42d40-107">可以指定多個排序運算式。</span><span class="sxs-lookup"><span data-stu-id="42d40-107">Multiple sort expressions can be specified.</span></span> <span data-ttu-id="42d40-108">ORDER BY 子句中排序運算式的順序會定義排序結果集的組織方式。</span><span class="sxs-lookup"><span data-stu-id="42d40-108">The sequence of the sort expressions in the ORDER BY clause defines the organization of the sorted result set.</span></span>  
  
 <span data-ttu-id="42d40-109">COLLATE {collation_name}</span><span class="sxs-lookup"><span data-stu-id="42d40-109">COLLATE {collation_name}</span></span>  
 <span data-ttu-id="42d40-110">指定 ORDER BY 運算要依照 `collation_name`中指定的定序執行。</span><span class="sxs-lookup"><span data-stu-id="42d40-110">Specifies that the ORDER BY operation should be performed according to the collation specified in `collation_name`.</span></span> <span data-ttu-id="42d40-111">COLLATE 只適用於字串運算式。</span><span class="sxs-lookup"><span data-stu-id="42d40-111">COLLATE is applicable only for string expressions.</span></span>  
  
 <span data-ttu-id="42d40-112">ASC</span><span class="sxs-lookup"><span data-stu-id="42d40-112">ASC</span></span>  
 <span data-ttu-id="42d40-113">指定特定屬性中的值要以遞增順序 (從最低值到最高值) 排序。</span><span class="sxs-lookup"><span data-stu-id="42d40-113">Specifies that the values in the specified property should be sorted in ascending order, from lowest value to highest value.</span></span> <span data-ttu-id="42d40-114">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="42d40-114">This is the default.</span></span>  
  
 <span data-ttu-id="42d40-115">DESC</span><span class="sxs-lookup"><span data-stu-id="42d40-115">DESC</span></span>  
 <span data-ttu-id="42d40-116">指定特定屬性中的值要以遞減順序 (從最高值到最低值) 排序。</span><span class="sxs-lookup"><span data-stu-id="42d40-116">Specifies that the values in the specified property should be sorted in descending order, from highest value to lowest value.</span></span>  
  
 <span data-ttu-id="42d40-117">LIMIT `n`</span><span class="sxs-lookup"><span data-stu-id="42d40-117">LIMIT `n`</span></span>  
 <span data-ttu-id="42d40-118">只選取前 `n` 個項目。</span><span class="sxs-lookup"><span data-stu-id="42d40-118">Only the first `n` items will be selected.</span></span>  
  
 <span data-ttu-id="42d40-119">SKIP `n`</span><span class="sxs-lookup"><span data-stu-id="42d40-119">SKIP `n`</span></span>  
 <span data-ttu-id="42d40-120">略過前 `n` 個項目。</span><span class="sxs-lookup"><span data-stu-id="42d40-120">Skips the first `n` items.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42d40-121">備註</span><span class="sxs-lookup"><span data-stu-id="42d40-121">Remarks</span></span>  
 <span data-ttu-id="42d40-122">ORDER BY 子句會以邏輯方式套用到 SELECT 子句的結果。</span><span class="sxs-lookup"><span data-stu-id="42d40-122">The ORDER BY clause is logically applied to the result of the SELECT clause.</span></span> <span data-ttu-id="42d40-123">ORDER BY 子句可以利用項目的別名參考選取清單中的項目。</span><span class="sxs-lookup"><span data-stu-id="42d40-123">The ORDER BY clause can reference items in the select list by using their aliases.</span></span> <span data-ttu-id="42d40-124">ORDER BY 子句也可以參考目前在範圍內的其他變數。</span><span class="sxs-lookup"><span data-stu-id="42d40-124">The ORDER BY clause can also reference other variables that are currently in-scope.</span></span> <span data-ttu-id="42d40-125">但是，如果已經配合 DISTINCT 修飾詞指定了 SELECT 子句，那麼 ORDER BY 子句就只能參考來自 SELECT 子句的別名。</span><span class="sxs-lookup"><span data-stu-id="42d40-125">However, if the SELECT clause has been specified with a DISTINCT modifier, the ORDER BY clause can only reference aliases from the SELECT clause.</span></span>  
  
 `SELECT c AS c1 FROM cs AS c ORDER BY c1.e1, c.e2`  
  
 <span data-ttu-id="42d40-126">ORDER BY 子句中的每個運算式都必評估為可以比較排序是否不相等 (小於或大於等) 的型別。</span><span class="sxs-lookup"><span data-stu-id="42d40-126">Each expression in the ORDER BY clause must evaluate to some type that can be compared for ordered inequality (less than or greater than, and so on).</span></span> <span data-ttu-id="42d40-127">這些型別通常是純量基本型別，例如數值、字串和日期。</span><span class="sxs-lookup"><span data-stu-id="42d40-127">These types are generally scalar primitives such as numbers, strings, and dates.</span></span> <span data-ttu-id="42d40-128">屬於可比較型別的 RowTypes 也可以比較排序。</span><span class="sxs-lookup"><span data-stu-id="42d40-128">RowTypes of comparable types are also order comparable.</span></span>  
  
 <span data-ttu-id="42d40-129">如果程式碼要在最上層投影以外的排序集上重複執行，輸出不一定會保持原排序。</span><span class="sxs-lookup"><span data-stu-id="42d40-129">If your code iterates over an ordered set, other than for a top-level projection, the output is not guaranteed to have its order preserved.</span></span>  
  
```  
-- In the following sample, order is guaranteed to be preserved:  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
 <span data-ttu-id="42d40-130">如需排序的 UNION、UNION ALL、EXCEPT 或 INTERSECT 運算，請使用下列模式：</span><span class="sxs-lookup"><span data-stu-id="42d40-130">To have an ordered UNION, UNION ALL, EXCEPT, or INTERSECT operation, use the following pattern:</span></span>  
  
```  
SELECT ...  
FROM ( UNION/EXCEPT/INTERSECT operation )  
ORDER BY ...  
```  
  
## <a name="restricted-keywords"></a><span data-ttu-id="42d40-131">限制關鍵字</span><span class="sxs-lookup"><span data-stu-id="42d40-131">Restricted keywords</span></span>  
 <span data-ttu-id="42d40-132">使用於 `ORDER BY` 子句時，下列關鍵字必須括在引號內：</span><span class="sxs-lookup"><span data-stu-id="42d40-132">The following keywords must be enclosed in quotation marks when used in an `ORDER BY` clause:</span></span>  
  
-   <span data-ttu-id="42d40-133">CROSS</span><span class="sxs-lookup"><span data-stu-id="42d40-133">CROSS</span></span>  
  
-   <span data-ttu-id="42d40-134">FULL</span><span class="sxs-lookup"><span data-stu-id="42d40-134">FULL</span></span>  
  
-   <span data-ttu-id="42d40-135">KEY</span><span class="sxs-lookup"><span data-stu-id="42d40-135">KEY</span></span>  
  
-   <span data-ttu-id="42d40-136">LEFT</span><span class="sxs-lookup"><span data-stu-id="42d40-136">LEFT</span></span>  
  
-   <span data-ttu-id="42d40-137">ORDER</span><span class="sxs-lookup"><span data-stu-id="42d40-137">ORDER</span></span>  
  
-   <span data-ttu-id="42d40-138">OUTER</span><span class="sxs-lookup"><span data-stu-id="42d40-138">OUTER</span></span>  
  
-   <span data-ttu-id="42d40-139">RIGHT</span><span class="sxs-lookup"><span data-stu-id="42d40-139">RIGHT</span></span>  
  
-   <span data-ttu-id="42d40-140">ROW</span><span class="sxs-lookup"><span data-stu-id="42d40-140">ROW</span></span>  
  
-   <span data-ttu-id="42d40-141">VALUE</span><span class="sxs-lookup"><span data-stu-id="42d40-141">VALUE</span></span>  
  
## <a name="ordering-nested-queries"></a><span data-ttu-id="42d40-142">排序巢狀查詢</span><span class="sxs-lookup"><span data-stu-id="42d40-142">Ordering Nested Queries</span></span>  
 <span data-ttu-id="42d40-143">在 Entity Framework 中，巢狀運算式可放在查詢中的任何地方；巢狀查詢的順序並不會保留。</span><span class="sxs-lookup"><span data-stu-id="42d40-143">In the Entity Framework, a nested expression can be placed anywhere in the query; the order of a nested query is not preserved.</span></span>  
  
```  
-- The following query will order the results by the last name.  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query, ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="example"></a><span data-ttu-id="42d40-144">範例</span><span class="sxs-lookup"><span data-stu-id="42d40-144">Example</span></span>  
 <span data-ttu-id="42d40-145">以下 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢使用 ORDER BY 運算子指定 SELECT 陳述式所傳回物件使用的排序順序。</span><span class="sxs-lookup"><span data-stu-id="42d40-145">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the ORDER BY operator to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="42d40-146">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="42d40-146">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="42d40-147">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="42d40-147">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="42d40-148">遵循 [如何：執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。</span><span class="sxs-lookup"><span data-stu-id="42d40-148">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="42d40-149">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="42d40-149">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ORDERBY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#orderby)]  
  
## <a name="see-also"></a><span data-ttu-id="42d40-150">請參閱</span><span class="sxs-lookup"><span data-stu-id="42d40-150">See Also</span></span>  
 [<span data-ttu-id="42d40-151">查詢運算式</span><span class="sxs-lookup"><span data-stu-id="42d40-151">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)  
 [<span data-ttu-id="42d40-152">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="42d40-152">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="42d40-153">SKIP</span><span class="sxs-lookup"><span data-stu-id="42d40-153">SKIP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)  
 [<span data-ttu-id="42d40-154">LIMIT</span><span class="sxs-lookup"><span data-stu-id="42d40-154">LIMIT</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)  
 [<span data-ttu-id="42d40-155">TOP</span><span class="sxs-lookup"><span data-stu-id="42d40-155">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
