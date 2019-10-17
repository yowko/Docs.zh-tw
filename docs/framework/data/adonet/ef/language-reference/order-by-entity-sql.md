---
title: ORDER BY (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c0b61572-ecee-41eb-9d7f-74132ec8a26c
ms.openlocfilehash: 2010ef9d6fe37e65824cac877074453db1b789db
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319438"
---
# <a name="order-by-entity-sql"></a><span data-ttu-id="2cb10-102">ORDER BY (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="2cb10-102">ORDER BY (Entity SQL)</span></span>
<span data-ttu-id="2cb10-103">指定 SELECT 陳述式所傳回物件使用的排序順序。</span><span class="sxs-lookup"><span data-stu-id="2cb10-103">Specifies the sort order used on objects returned in a SELECT statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cb10-104">語法</span><span class="sxs-lookup"><span data-stu-id="2cb10-104">Syntax</span></span>  
  
```sql  
[ ORDER BY   
   {  
      order_by_expression [SKIP n] [LIMIT n]  
      [ COLLATE collation_name ]  
      [ ASC | DESC ]  
   }  
   [ ,…n ]   
]  
```  
  
## <a name="arguments"></a><span data-ttu-id="2cb10-105">引數</span><span class="sxs-lookup"><span data-stu-id="2cb10-105">Arguments</span></span>  
 `order_by_expression`  
 <span data-ttu-id="2cb10-106">任何指定要排序之屬性的有效查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="2cb10-106">Any valid query expression specifying a property on which to sort.</span></span> <span data-ttu-id="2cb10-107">可以指定多個排序運算式。</span><span class="sxs-lookup"><span data-stu-id="2cb10-107">Multiple sort expressions can be specified.</span></span> <span data-ttu-id="2cb10-108">ORDER BY 子句中排序運算式的順序會定義排序結果集的組織方式。</span><span class="sxs-lookup"><span data-stu-id="2cb10-108">The sequence of the sort expressions in the ORDER BY clause defines the organization of the sorted result set.</span></span>  
  
 <span data-ttu-id="2cb10-109">COLLATE {collation_name}</span><span class="sxs-lookup"><span data-stu-id="2cb10-109">COLLATE {collation_name}</span></span>  
 <span data-ttu-id="2cb10-110">指定 ORDER BY 運算要依照 `collation_name`中指定的定序執行。</span><span class="sxs-lookup"><span data-stu-id="2cb10-110">Specifies that the ORDER BY operation should be performed according to the collation specified in `collation_name`.</span></span> <span data-ttu-id="2cb10-111">COLLATE 只適用於字串運算式。</span><span class="sxs-lookup"><span data-stu-id="2cb10-111">COLLATE is applicable only for string expressions.</span></span>  
  
 <span data-ttu-id="2cb10-112">ASC</span><span class="sxs-lookup"><span data-stu-id="2cb10-112">ASC</span></span>  
 <span data-ttu-id="2cb10-113">指定特定屬性中的值要以遞增順序 (從最低值到最高值) 排序。</span><span class="sxs-lookup"><span data-stu-id="2cb10-113">Specifies that the values in the specified property should be sorted in ascending order, from lowest value to highest value.</span></span> <span data-ttu-id="2cb10-114">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="2cb10-114">This is the default.</span></span>  
  
 <span data-ttu-id="2cb10-115">DESC</span><span class="sxs-lookup"><span data-stu-id="2cb10-115">DESC</span></span>  
 <span data-ttu-id="2cb10-116">指定特定屬性中的值要以遞減順序 (從最高值到最低值) 排序。</span><span class="sxs-lookup"><span data-stu-id="2cb10-116">Specifies that the values in the specified property should be sorted in descending order, from highest value to lowest value.</span></span>  
  
 <span data-ttu-id="2cb10-117">LIMIT `n`</span><span class="sxs-lookup"><span data-stu-id="2cb10-117">LIMIT `n`</span></span>  
 <span data-ttu-id="2cb10-118">只選取前 `n` 個項目。</span><span class="sxs-lookup"><span data-stu-id="2cb10-118">Only the first `n` items will be selected.</span></span>  
  
 <span data-ttu-id="2cb10-119">SKIP `n`</span><span class="sxs-lookup"><span data-stu-id="2cb10-119">SKIP `n`</span></span>  
 <span data-ttu-id="2cb10-120">略過前 `n` 個項目。</span><span class="sxs-lookup"><span data-stu-id="2cb10-120">Skips the first `n` items.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2cb10-121">備註</span><span class="sxs-lookup"><span data-stu-id="2cb10-121">Remarks</span></span>  
 <span data-ttu-id="2cb10-122">ORDER BY 子句會以邏輯方式套用到 SELECT 子句的結果。</span><span class="sxs-lookup"><span data-stu-id="2cb10-122">The ORDER BY clause is logically applied to the result of the SELECT clause.</span></span> <span data-ttu-id="2cb10-123">ORDER BY 子句可以利用項目的別名參考選取清單中的項目。</span><span class="sxs-lookup"><span data-stu-id="2cb10-123">The ORDER BY clause can reference items in the select list by using their aliases.</span></span> <span data-ttu-id="2cb10-124">ORDER BY 子句也可以參考目前在範圍內的其他變數。</span><span class="sxs-lookup"><span data-stu-id="2cb10-124">The ORDER BY clause can also reference other variables that are currently in-scope.</span></span> <span data-ttu-id="2cb10-125">但是，如果已經配合 DISTINCT 修飾詞指定了 SELECT 子句，那麼 ORDER BY 子句就只能參考來自 SELECT 子句的別名。</span><span class="sxs-lookup"><span data-stu-id="2cb10-125">However, if the SELECT clause has been specified with a DISTINCT modifier, the ORDER BY clause can only reference aliases from the SELECT clause.</span></span>  
  
 `SELECT c AS c1 FROM cs AS c ORDER BY c1.e1, c.e2`  
  
 <span data-ttu-id="2cb10-126">ORDER BY 子句中的每個運算式都必評估為可以比較排序是否不相等 (小於或大於等) 的型別。</span><span class="sxs-lookup"><span data-stu-id="2cb10-126">Each expression in the ORDER BY clause must evaluate to some type that can be compared for ordered inequality (less than or greater than, and so on).</span></span> <span data-ttu-id="2cb10-127">這些型別通常是純量基本型別，例如數值、字串和日期。</span><span class="sxs-lookup"><span data-stu-id="2cb10-127">These types are generally scalar primitives such as numbers, strings, and dates.</span></span> <span data-ttu-id="2cb10-128">屬於可比較型別的 RowTypes 也可以比較排序。</span><span class="sxs-lookup"><span data-stu-id="2cb10-128">RowTypes of comparable types are also order comparable.</span></span>  
  
 <span data-ttu-id="2cb10-129">如果程式碼要在最上層投影以外的排序集上重複執行，輸出不一定會保持原排序。</span><span class="sxs-lookup"><span data-stu-id="2cb10-129">If your code iterates over an ordered set, other than for a top-level projection, the output is not guaranteed to have its order preserved.</span></span>  

<span data-ttu-id="2cb10-130">在下列範例中，保證會保留訂單：</span><span class="sxs-lookup"><span data-stu-id="2cb10-130">In the following sample, order is guaranteed to be preserved:</span></span>

```sql  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  

<span data-ttu-id="2cb10-131">在下列查詢中，會忽略巢狀查詢的順序：</span><span class="sxs-lookup"><span data-stu-id="2cb10-131">In the following query, ordering of the nested query is ignored:</span></span>  

```sql  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
 <span data-ttu-id="2cb10-132">如需排序的 UNION、UNION ALL、EXCEPT 或 INTERSECT 運算，請使用下列模式：</span><span class="sxs-lookup"><span data-stu-id="2cb10-132">To have an ordered UNION, UNION ALL, EXCEPT, or INTERSECT operation, use the following pattern:</span></span>  
  
```sql  
SELECT ...  
FROM ( UNION/EXCEPT/INTERSECT operation )  
ORDER BY ...  
```  
  
## <a name="restricted-keywords"></a><span data-ttu-id="2cb10-133">限制關鍵字</span><span class="sxs-lookup"><span data-stu-id="2cb10-133">Restricted keywords</span></span>  
 <span data-ttu-id="2cb10-134">使用於 `ORDER BY` 子句時，下列關鍵字必須括在引號內：</span><span class="sxs-lookup"><span data-stu-id="2cb10-134">The following keywords must be enclosed in quotation marks when used in an `ORDER BY` clause:</span></span>  
  
- <span data-ttu-id="2cb10-135">CROSS</span><span class="sxs-lookup"><span data-stu-id="2cb10-135">CROSS</span></span>  
  
- <span data-ttu-id="2cb10-136">FULL</span><span class="sxs-lookup"><span data-stu-id="2cb10-136">FULL</span></span>  
  
- <span data-ttu-id="2cb10-137">KEY</span><span class="sxs-lookup"><span data-stu-id="2cb10-137">KEY</span></span>  
  
- <span data-ttu-id="2cb10-138">LEFT</span><span class="sxs-lookup"><span data-stu-id="2cb10-138">LEFT</span></span>  
  
- <span data-ttu-id="2cb10-139">ORDER</span><span class="sxs-lookup"><span data-stu-id="2cb10-139">ORDER</span></span>  
  
- <span data-ttu-id="2cb10-140">OUTER</span><span class="sxs-lookup"><span data-stu-id="2cb10-140">OUTER</span></span>  
  
- <span data-ttu-id="2cb10-141">RIGHT</span><span class="sxs-lookup"><span data-stu-id="2cb10-141">RIGHT</span></span>  
  
- <span data-ttu-id="2cb10-142">ROW</span><span class="sxs-lookup"><span data-stu-id="2cb10-142">ROW</span></span>  
  
- <span data-ttu-id="2cb10-143">VALUE</span><span class="sxs-lookup"><span data-stu-id="2cb10-143">VALUE</span></span>  
  
## <a name="ordering-nested-queries"></a><span data-ttu-id="2cb10-144">排序巢狀查詢</span><span class="sxs-lookup"><span data-stu-id="2cb10-144">Ordering Nested Queries</span></span>  
 <span data-ttu-id="2cb10-145">在 Entity Framework 中，巢狀運算式可放在查詢中的任何地方；巢狀查詢的順序並不會保留。</span><span class="sxs-lookup"><span data-stu-id="2cb10-145">In the Entity Framework, a nested expression can be placed anywhere in the query; the order of a nested query is not preserved.</span></span>  

<span data-ttu-id="2cb10-146">下列查詢會依姓氏排序結果：</span><span class="sxs-lookup"><span data-stu-id="2cb10-146">The following query will order the results by the last name:</span></span>  

```sql  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  

<span data-ttu-id="2cb10-147">在下列查詢中，會忽略巢狀查詢的順序：</span><span class="sxs-lookup"><span data-stu-id="2cb10-147">In the following query, ordering of the nested query is ignored:</span></span>  

```sql  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="example"></a><span data-ttu-id="2cb10-148">範例</span><span class="sxs-lookup"><span data-stu-id="2cb10-148">Example</span></span>  
 <span data-ttu-id="2cb10-149">以下 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢使用 ORDER BY 運算子指定 SELECT 陳述式所傳回物件使用的排序順序。</span><span class="sxs-lookup"><span data-stu-id="2cb10-149">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the ORDER BY operator to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="2cb10-150">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="2cb10-150">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="2cb10-151">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="2cb10-151">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="2cb10-152">遵循 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。</span><span class="sxs-lookup"><span data-stu-id="2cb10-152">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="2cb10-153">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="2cb10-153">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#ORDERBY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#orderby)]  
  
## <a name="see-also"></a><span data-ttu-id="2cb10-154">請參閱</span><span class="sxs-lookup"><span data-stu-id="2cb10-154">See also</span></span>

- [<span data-ttu-id="2cb10-155">查詢運算式</span><span class="sxs-lookup"><span data-stu-id="2cb10-155">Query Expressions</span></span>](query-expressions-entity-sql.md)
- [<span data-ttu-id="2cb10-156">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="2cb10-156">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="2cb10-157">SKIP</span><span class="sxs-lookup"><span data-stu-id="2cb10-157">SKIP</span></span>](skip-entity-sql.md)
- [<span data-ttu-id="2cb10-158">LIMIT</span><span class="sxs-lookup"><span data-stu-id="2cb10-158">LIMIT</span></span>](limit-entity-sql.md)
- [<span data-ttu-id="2cb10-159">TOP</span><span class="sxs-lookup"><span data-stu-id="2cb10-159">TOP</span></span>](top-entity-sql.md)
